# Application Answers — Urban Company | SDE-2 Fulfilment

**Prepared:** October 30, 2026

---

## Application Form

LinkedIn Easy Apply — contact info, resume upload, work authorization, screening questions.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Design a scalable, fault-tolerant system for real-time partner–job matching at marketplace scale.**

I would design this as an event-driven, multi-layered matching service. The matching trigger — a new booking event — enters a queue (Kafka or Redis streams). A matching service consumes it: first a coarse filter (geography, skill, availability window) against a pre-computed availability index, then a ranking pass that scores eligible partners by proximity, fairness score, and historical acceptance rate. The output is a ranked candidate list passed to an assignment service that handles concurrency — using optimistic locking or a distributed lock (Redis SETNX) to prevent double-assignment. For high-traffic slots, a pre-computed availability cache (Redis sorted set by slot + region) avoids real-time DB scans on every booking. I would instrument every stage with latency histograms, match rate, and fallback rate, and design a recovery path for no-match cases (widen radius, relax constraints, trigger manual review). Fault tolerance: the consumer group retries failed events with exponential backoff; the assignment service is idempotent (booking ID as dedup key).

**2. How do you design and operate caching for high-traffic, time-sensitive systems?**

Cache design starts with understanding the access pattern: read-heavy with occasional writes (partner availability slots) calls for a read-through cache with TTL aligned to slot granularity. At Moresand, I built a Redis-backed caching layer for high-traffic API endpoints — the key insight was that different data has different staleness tolerance. Static config: long TTL, eager population. Session-scoped data: short TTL, lazy load. For time-slot availability, I used a Redis sorted set keyed by region + date, scored by slot time, so range queries for "available slots in the next 4 hours" are O(log N + K). Cache invalidation is the hard part: I use write-through for critical correctness (partner status changes) and TTL-expiry for lower-stakes data. I monitor cache hit rate, TTL expirations, and memory usage through structured metrics and alert on hit rate drops below threshold.

**3. How do you use AI in your day-to-day engineering workflow?**

I use Claude, GitHub Copilot, and Cursor as accelerators for the mechanical parts of engineering — boilerplate, test scaffolding, documentation drafts — freeing up focus for the design and judgement problems. In practice: Copilot for inline completion of repetitive patterns (API route handlers, type definitions), Claude for design review ("what are the failure modes of this approach?"), Cursor for codebase-aware refactors. I always review AI-generated code against my mental model of correctness — AI suggestions introduce subtle bugs if you stop thinking. At MAQ Software, I owned full delivery of a production AI backend using Claude and GitHub Copilot throughout; the 28% prompt accuracy improvement came from instrumentation and iteration, not from tool suggestions. The key discipline: AI output is a first draft, not a final answer.

**4. Describe a complex system you owned end-to-end. What were the key decisions?**

At Moresand, I owned end-to-end design and delivery of the multi-tenant API layer for our CMS platform — the system that supports 5+ enterprise clients on a single codebase with fully isolated data and brand-specific configuration. Key decisions: (1) Schema design — I chose a shared-schema multi-tenancy model with a tenant_id column on every entity and row-level access control enforced at the repository layer, not the controller. This made isolation a correctness property, not a convention. (2) API versioning — I introduced versioned routes (/v1/, /v2/) with a compatibility shim layer so we could evolve the API without breaking existing clients. (3) Caching — Redis-backed with a cache key that includes the tenant ID, so no cross-tenant leakage was architecturally possible. These decisions cut onboarding time by 50% and reduced regression risk on new-client launches.

**5. How do you translate ambiguous business problems into technical solutions?**

I start by writing the problem statement in one sentence: "The system must do X for Y users in Z time." That forces precision about scope and constraints. Then I list the invariants — what must always be true — before designing anything. At Moresand, when asked to build "a way for clients to configure their own brand experience," I spent two days with the product team clarifying: which config is static vs. dynamic, what the blast radius of a misconfiguration is, and what rollback looks like. That clarification changed the design entirely — from a per-request config load to a build-time configuration baked into the deployment. The wrong framing (dynamic, per-request) would have added latency and operational complexity with no real benefit. Getting the problem statement right is the highest-leverage part of the work.
