# Application & Recruiter Screening Answers: Kiwi General Insurance (SDE Backend — Mumbai, Vikhroli)

This document provides ready-to-use, crisp, and high-impact answers for application forms, recruiter screening calls, and hiring manager discussions.

---

### Q1: Location & Relocation Question
**Prompt/Question:** *Are you open to relocating to Mumbai (Vikhroli) for a 5-day work-from-office setup? What has your geographic work experience been like?*

**Tailored Answer:**
> "Yes, absolutely. I am completely comfortable with a 5-day work-from-office model in Vikhroli, Mumbai, and ready to relocate. Throughout my academic and professional journey, I have actively lived and worked across multiple tech hubs across India—graduating from IIIT Vadodara in Gujarat, working in Noida/Delhi NCR (MAQ Software and GeeksforGeeks), operating remotely (Techolution), and currently working in Bengaluru (Moresand Technologies). This multi-city journey has made me highly adaptable to diverse work cultures, fast-paced team dynamics, and new environments. I value high-bandwidth, in-person whiteboarding and real-time collaboration with product and engineering teams, making this on-site role in Vikhroli an ideal fit."

---

### Q2: MVP to Scalable Architecture (0-to-1 vs. 1-to-100)
**Prompt/Question:** *How do you navigate different stages of product development—from scrappy MVPs to scalable architectures?*

**Tailored Answer:**
> "In early-stage MVP phases, speed of validation is paramount. I focus on contract-first API design, leveraging Node.js/TypeScript to deliver tight, working endpoints with sensible defaults rather than premature over-engineering. For example, during an MVP rollout at Moresand for a new tenant integration, we shipped a functional monolithic service within two weeks to validate real client demand and partner onboarding.
> 
> Once traffic validated the feature and hit scale, I transitioned the architecture: we extracted bounded contexts into decoupled services, introduced NestJS modular architecture, migrated expensive recurring queries to a Redis caching layer, optimized PostgreSQL indexes, and instituted connection pooling. This brought latency down from ~220ms to sub-50ms under peak spikes without disrupting ongoing product velocity. Navigating both stages requires knowing when to optimize for time-to-market versus when to invest in architectural resilience."

---

### Q3: Deep Expertise in Node.js & TypeScript
**Prompt/Question:** *Tell us about your hands-on experience with Node.js and TypeScript. What makes you confident in building high-throughput systems with this stack?*

**Tailored Answer:**
> "I have over 3.5 years of production experience centered on Node.js and TypeScript across product platforms. I utilize strict TypeScript type systems (generics, Zod/Joi schema validation, and shared interface contracts) to eliminate runtime type mismatches between frontend, backend, and external partner APIs. 
> 
> Under the hood in Node.js, I understand event loop phases, non-blocking asynchronous I/O, worker threads for CPU-heavy tasks, and streaming interfaces for handling large payloads without memory leaks. In high-throughput environments, I use clustered Node instances, robust error boundaries, structured JSON logging, and connection pooling across Redis and PostgreSQL, ensuring the system sustains high requests per second with predictable low latency."

---

### Q4: Database Design & High Performance
**Prompt/Question:** *How do you approach database design, performance tuning, and caching in high-scale systems?*

**Tailored Answer:**
> "I approach data design by starting with query patterns and consistency requirements. For relational data (PostgreSQL/MySQL), I normalize core transactional schemas to ensure ACID compliance while strategically denormalizing read-heavy views where latency is critical. I design indexes around composite query filters and monitor slow query logs (`pg_stat_statements`).
> 
> To protect the database during traffic surges, I implement Redis as both a look-aside cache (with TTLs and cache-invalidation hooks) and an asynchronous queue. Furthermore, I implement connection pooling (e.g., PgBouncer or Knex/TypeORM pool configs) and rate-limiting to prevent connection exhaustion. At Moresand, this combined setup allowed us to absorb sudden traffic surges with 99.9% availability."

---

### Q5: Notice Period & Current Status
**Prompt/Question:** *What is your notice period, current location, and availability to join?*

**Tailored Answer:**
> - **Current Location:** Bengaluru, Karnataka
> - **Notice Period:** Serving / 60 days (with strong possibility of early buyout/release depending on mutual alignment)
> - **Joining Availability:** Immediate to 60 days
> - **Work Model:** 100% committed to 5 Days Work from Office in Vikhroli, Mumbai
