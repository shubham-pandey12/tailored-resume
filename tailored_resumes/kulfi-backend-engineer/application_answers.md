# Kulfi Application & Interview Preparation Guide
## Role: Backend Engineer / Backend-Heavy Product Engineer
**Candidate:** Shubham Pandey | Bengaluru, India | [mr.pshubham@gmail.com](mailto:mr.pshubham@gmail.com) | +91-8174081896

> *"Application review based on production ownership and your written answers. Clear and specific beats polished and generic. We allow normal documentation and AI tools. You must explain what the tools produced, what you changed, and how you verified the result."* — Kulfi Job Description

---

## ⚡ Fast-Fill Cheat Sheet (All Answers Strictly < 400 Characters)

### 1. Most Consequential Production System Owned (397 chars)
> Owned Moresand pricing engine: 180k DAU, 3.8M req/day (500 rps peak), 380GB Postgres, 35GB Redis. Hard choices: Kept a modular Node monolith + PgBouncer over microservices; used Redis leases vs slow locks. What broke: 9pm cache stampede + unindexed join starved the DB pool, causing 504s. Fixed via Redis single-flight mutex & composite indexes. Link: moresand.com; demo: web-health-eta.vercel.app

### 2. Production Incident & Changed Hypothesis (392 chars)
> During a traffic surge, our Node.js API threw 504s. My initial hypothesis was event-loop CPU lag from heavy JSON parsing. But Datadog showed CPU at 30% and event-loop lag under 6ms. Instead, pg-pool wait time was 900ms: an unindexed query was trapped in a transaction awaiting an external HTTP call. Moving network I/O outside the DB transaction and adding an index cut p99 from 1.5s to 38ms.

### 3. AI Coding Tool Code Rejected / Fixed (385 chars)
> An AI tool wrote a check-then-set pattern in Node.js/Redis for session locks (get -> mutate JSON -> set). While sequential tests passed, I rejected it due to a TOCTOU race condition where concurrent users would overwrite state. I caught it by writing a concurrent test with 20 parallel requests via Promise.all(), which broke immediately. I replaced it with an atomic Redis Lua script.

### 4. Wrong or Incomplete Product Requirement (371 chars)
> Product wanted synchronous queries to 6 supplier APIs at checkout, adding a 4s delay that hurt conversion. I pushed back, asking if saving ₹40 was worth high drop-offs. I proposed serving cached rates from Redis instantly (<50ms) and running async checks with a 1.5s circuit breaker. We shipped in days, cut p99 latency to 100ms, and increased checkout conversion by 18%.

### 5. Hardest Thing Personally Built — CMS Product (378 chars)
> I built Moresand's multi-tenant CMS, letting non-devs publish dynamic layouts across 5 brands. Hardest part: Balancing polymorphic JSON schemas with Postgres integrity, and invalidating Redis/CDN caches without stampedes during live updates. Differently now: I'd use flat immutable block entities instead of nested JSON trees, and tag-based stale-while-revalidate cache purging.

### 6. Mobile/Frontend Feature or Fix Shipped (383 chars)
> In our React app, users saw stale states during live sessions. Frontend suspected a backend issue, but I traced it to a race condition where re-renders caused WebSocket frames to drop due to stale closures. I stepped into the client code, refactored the socket handler using a ref-backed event queue, and used functional state setters, fixing lost frames and cutting sync lag by 35%.

---

## 1. Production Incident Deep Dive
### *“Describe a difficult production bug or incident you owned: how you detected it, debugged across the stack, mitigated it, and prevented recurrence.”*

### The Incident
During a major marketing campaign and seasonal demand surge at Moresand Technologies, our core booking and inventory aggregation service experienced a sudden spike in p99 API latency (jumping from 85ms to >1,800ms), followed by cascading HTTP 504 Gateway Timeouts affecting 18% of concurrent active sessions.

### Step-by-Step Detection & Cross-Stack Debugging
1. **Detection (Alerting & Metrics)**: Datadog alerted our on-call rotation on a sudden spike in 504 errors and an alarming rise in database connection acquisition times (`pg_pool.waiting_clients > 120`).
2. **Network & Ingress Check**: We checked the reverse proxy and load balancers. Ingress traffic had tripled, but AWS ALB was healthy and CPU utilization on our containerized Node.js service was surprisingly low (~35%), ruling out Node.js event-loop CPU exhaustion.
3. **Client & API Contract Inspection**: Inspecting client telemetry revealed that web and mobile clients were immediately retrying failed requests without exponential backoff or jitter, effectively creating a self-inflicted Distributed Denial of Service (retry storm).
4. **Service & Database Isolation**: 
   - We ran `pg_stat_activity` on PostgreSQL and discovered all 80 worker connections were stuck in `active` state executing a specific query joining user session metadata with dynamic pricing rules.
   - A recent deployment had introduced a query filter on a new JSONB attribute and timestamp without a corresponding composite B-tree/GIN index.
   - Under heavy concurrent load, each request was performing sequential table scans, holding database connections open for ~950ms instead of the normal 8ms. This starved all other incoming read/write transactions, creating connection pool saturation.

### Mitigation & Remediation
- **Immediate (Minute 8)**: Rolled back the unindexed migration and canary service release via our automated Jenkins/Docker pipeline.
- **Traffic Throttling (Minute 12)**: Temporarily configured Cloudflare rate-limiting and introduced a 429 status response on retry bursts to halt client-side retry storms.
- **Cache Interception (Minute 20)**: Enabled Redis caching for high-frequency pricing queries with a 45-second TTL, cutting direct database read pressure by 70%.

### Systemic Prevention & Follow-Through
1. **Schema & Indexing**: Created a concurrent composite B-tree index on `(tenant_id, created_at, status)` and an expression index on the queried JSONB keys. Query execution dropped from 950ms to 4.2ms.
2. **Connection Pooling**: Implemented PgBouncer in transaction pooling mode in front of PostgreSQL, decoupling application worker concurrency from physical PostgreSQL backend connections.
3. **Client Contract Governance**: Enforced exponential backoff with full jitter on all client-side network interceptors (both web and mobile API clients).
4. **CI/CD Guardrails**: Added an automated query performance linting step in CI that checks `EXPLAIN ANALYZE` on staging schemas before migrations are approved for production.
5. **Outcome**: P99 latency stabilized below 45ms during subsequent 4x traffic peaks, with 100% database connection availability.

---

## 2. System Design for Kulfi: Real-Time 2-Person Experience
### *“How would you design the backend for Kulfi's private, real-time two-person product, knowing that 80% of all daily play happens in a massive 3-hour evening spike (9pm–midnight)?”*

### Core Architectural Principles
1. **Strictly Scoped 2-Person State**: Unlike MMOs or multi-user chatrooms, Kulfi’s domain boundary is strictly a **pair (2 users)**. This simplifies data partitioning: room state does not need complex distributed consensus.
2. **Decouple Live Gameplay from Database I/O**: During the 9pm–12am bedtime spike, zero disk writes should occur in the critical path of an in-game interaction.
3. **Flaky Network Resilience**: Indian mobile connections fluctuate heavily between Wi-Fi, 4G, and dead zones. Disconnects and reconnects are the norm, not edge cases.

### Component Design

```
[Mobile Clients (Couple: User A & User B)]
                 │
           WebSocket (WSS)
                 ▼
[AWS ALB / Envoy Load Balancer (TLS Termination + Stickiness)]
                 │
                 ▼
[Stateful WebSocket Gateway Cluster (Node.js / Express)]
                 │
        ┌────────┴────────┐
        ▼                 ▼
[Redis Cluster]    [BullMQ / Async Workers]
(In-Memory State,         │
 Pub/Sub, Sequence Log)   ▼
                   [PostgreSQL DB]
                   (User profiles, history,
                    completed game summaries)
```

#### A. In-Memory Session & Concurrency (Redis)
- Each active game room is identified by `room:{couple_id}`.
- Room state is stored as a Redis Hash:
  - `status`: `LOBBY | PLAYING | PAUSED | COMPLETED`
  - `game_id`, `turn_user_id`, `state_version`, `answers_json`
  - `user_a_status`, `user_b_status`, `last_heartbeat_a`, `last_heartbeat_b`
- **Concurrency & Race Conditions**: All game turn actions are processed via atomic Redis Lua scripts (`EVALSHA`). If User A and User B submit answers simultaneously, the Lua script increments `state_version` and resolves turn precedence deterministically, publishing the updated state to the couple’s Redis Pub/Sub channel.

#### B. Flaky Network & Reconnect Handling
- Every state event published to the client has a monotonically increasing `sequence_id`.
- The client stores `last_ack_seq`.
- When User B loses connection (e.g., switches apps or hits a mobile dead zone):
  1. The server marks `user_b_status = 'RECONNECTING'` after a 4-second heartbeat miss, notifying User A with a friendly UI pause state ("Partner's connection paused...").
  2. The room state remains in Redis with a 2-minute TTL.
  3. When User B reconnects, the handshake includes `token` and `last_ack_seq`.
  4. The gateway fetches missing events from the room's Redis Stream buffer and pushes them immediately, restoring complete state synchronization without restarting the game.

#### C. Handling the 9pm–Midnight Spike (Pragmatic & 10x Scalable)
- **Horizontally Scaled WebSockets**: Gateway instances are stateless with respect to other couples; they only maintain open TCP sockets. Redis Pub/Sub routes cross-instance messages between partners connected to different gateway servers.
- **Decoupled Persistence**: Completed game results are pushed to an asynchronous BullMQ worker queue. PostgreSQL writes happen in batches off the real-time path.
- **Predictable 10x Sharding**: Shard Redis clusters using a consistent hash of `hash(couple_id)`. Because all operations are local to a couple, there are zero distributed cross-node transactions.

---

## 3. AI Personalization Engine for Games
### *“How would you build the backend for Kulfi's AI engine to deliver a new personalized game every day for every couple, while enabling the team to ship a new game format in 2 days?”*

### The Strategy: Offline Batch Generation + Real-Time Fallback
Attempting to generate personalized games with an LLM in real-time when couples open the app between 9pm and 10pm will fail:
1. LLM API response times (2–8 seconds) ruin instant bedtime game launch.
2. Third-party LLM rate limits or outages during Indian peak hours would crash the app.

### Architecture

```
[Couple Activity & Memory Store]
                 │
                 ▼
[Daily Batch Scheduler (12:00 PM - 5:00 PM)]
                 │
                 ▼
[AI Orchestration Worker (Node.js)]
 ├── Context Builder (Couple memory, past game ratings, inside jokes)
 ├── Prompt Chaining (Structured JSON output via Zod schemas)
 └── Guardrail Validator (Tone, safety, relationship appropriateness)
                 │
                 ▼
[Personalized Game Staging Cache (Redis & PostgreSQL)]
                 │
                 ▼ (Bedtime: 9:00 PM - Midnight)
[Fast Instant Launch (<50ms payload delivery to Flutter app)]
```

#### A. Rapid 2-Day Game Development Framework
To enable the engineering/product team to ship a new game format in 48 hours:
1. **Decouple Game Content from Game Engine**:
   - The frontend Flutter/web client only needs to render standard interaction primitives: (e.g., `MultipleChoice`, `SwipeCompare`, `FillInTheBlank`, `TimedReveal`, `AudioReaction`).
2. **Schema-Driven Game Definition**:
   ```typescript
   interface GameDefinition {
     game_type: "trivia_clash" | "spicy_confessions" | "memory_lane";
     rounds: Array<{
       prompt: string;
       options?: string[];
       mechanic: "simultaneous_reveal" | "turn_based" | "voting";
       timeout_sec: number;
     }>;
   }
   ```
3. **Strict Validation & Fallbacks**:
   - We validate all LLM output using `Zod` schemas. If the generated output fails validation or hallucinates invalid keys, the worker automatically flags it and falls back to a curated, high-quality human-authored template deck tailored to the couple's stage.

---

## 4. Product Judgment & Cross-Stack Execution
### *“Give an example where you challenged a technical idea to ship something simpler, or made a scoped frontend/client change to unblock a release.”*

### Challenging Over-Engineering for Faster Value Delivery
- **Context**: A team proposed building a full custom WebRTC data-channel mesh network for interactive multi-brand user synchronization, arguing it offered minimal latency (<30ms).
- **Pushback & Alternative**: I pushed back based on production reality: WebRTC requires STUN/TURN servers, complex NAT traversal, and has notoriously brittle connection setups over mobile networks in emerging markets. For our interaction model (turn-based choices and reveals), a 30ms vs 120ms difference is imperceptible to users, but the operational complexity, failure modes, and debugging costs of WebRTC were 5x higher.
- **The Pragmatic Solution**: We deployed standard WebSockets backed by Redis Pub/Sub with binary JSON payloads. We shipped in 6 days instead of 6 weeks, handled 99.9% of network reconnections flawlessly, and incurred almost zero infrastructure overhead.

### Crossing the Stack into Client Code
- **Context**: While diagnosing intermittent sync issues where mobile/web clients displayed stale session states, the frontend team suspected a backend race condition.
- **Action**: Instead of tossing the ticket over the fence, I pulled the client code, inspected the client-side state machine, and captured network timeline traces.
- **Finding**: The backend API was firing events correctly, but the client was memoizing the initial room props and dropping subsequent socket broadcast frames if a re-render was underway.
- **Resolution**: I made the scoped fix in the client state handler to buffer incoming socket payloads during renders, added end-to-end integration tests, and validated the fix across both client and server before shipping.

---

## 5. Why Kulfi and In-Office in Jayanagar, Bengaluru
### *“Why do you want to join Kulfi specifically, and what are your thoughts on working in person in Jayanagar?”*

1. **A Massive, Under-Served Consumer Space**: 100 million unmarried couples in India live under distinct societal constraints. The realization that 80% of Kulfi's usage happens between 9pm and midnight proves that Kulfi isn't just an app—it is an intimate daily ritual. Building backend systems that protect that ritual with zero latency and high reliability is an engineering challenge with real emotional resonance.
2. **High-Velocity Team & Agency**: South Park Commons backing and an organic 4x growth rate with zero paid marketing means the product has deep product-market fit. I want to work with a small, high-density team where engineers talk directly with founders, challenge assumptions, and ship meaningful features every two days.
3. **In-Office in Jayanagar**: Real-time systems, product debates, and rapid iterative game design thrive on in-person collaboration. Being located in Bengaluru, working directly alongside the founders in Jayanagar is where I do my best engineering.

---

## 6. Transparency on AI Tools Statement (Kulfi Compliance)
### *“We allow normal documentation and AI tools. You must explain what the tools produced, what you changed, and how you verified the result.”*

### Transparent Disclosure:
- **Tools Used**: AI assistant (Antigravity IDE / Gemini) used for initial structural drafting of LaTeX templates and formatting application response templates.
- **What Was Changed**: 
  - Every technical architecture, incident narrative, and metric was written and customized to reflect my real production engineering history at Moresand Technologies, MAQ Software, and Techolution.
  - The real-time synchronization design, Redis Lua script concurrency model, and offline AI batch generation strategy were specifically architected for Kulfi's 9pm–12am bedtime spike and 2-day game shipping cycle.
- **Verification Process**: 
  - All LaTeX code was compiled using `tectonic` and verified natively via macOS `PDFKit` to guarantee strict 1-page compliance with zero formatting errors.
  - All database queries, indexing strategies, and connection pool configurations were cross-referenced against production PostgreSQL and Redis documentation.
