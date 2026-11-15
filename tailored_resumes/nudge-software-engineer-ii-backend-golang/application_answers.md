# Application Answers — Nudge | Software Engineer II (SDE 2) - (Backend - Golang)

**Company:** Nudge  
**Role:** Software Engineer II (SDE 2) - (Backend - Golang)  
**Department:** Technology / Core Platform Engineering  
**Location:** Bangalore Corporate Office  
**Source URL:** https://nudge.keka.com/careers/jobdetails/94988?source=linkedin  
**Prepared Date:** November 10, 2026  

---

## 1. Standard Application Form Fields (Keka ATS)

| Form Field | Value to Enter | Status |
|---|---|---|
| **First Name** | `Shubham` | Verified |
| **Last Name** | `Pandey` | Verified |
| **Email** | `mr.pshubham@gmail.com` | Verified |
| **Phone / Mobile** | `+91-8174081896` | Verified |
| **Current Company** | `Moresand Technologies` | Confirm current employment |
| **Current Location** | `Bengaluru, Karnataka` | Confirm current city / Bangalore office readiness |
| **Total Experience** | `3.4 years full-time (~3.9 years including 6-month internship)` | Verified against resume dates (as of Nov 2026) |
| **LinkedIn URL** | `https://www.linkedin.com/in/shubham-pandey-a74716199/` | Verified |
| **GitHub URL** | `https://github.com/shubham-pandey12` | Verified |
| **Portfolio URL** | `https://shubham-portfolio-mocha.vercel.app/` | Verified |
| **Resume** | Attach `ShubhamPandeyResume.pdf` | Ready (1 page verified) |
| **Cover Letter** | Attach `ShubhamPandeyCoverLetter.pdf` | Ready (1 page verified) |
| **Current CTC** | `[USER CONFIRMATION REQUIRED]` | Not in master resume |
| **Expected CTC** | `[USER CONFIRMATION REQUIRED]` | Not in master resume |
| **Notice Period / Availability** | `[USER CONFIRMATION REQUIRED]` | Not in master resume |

---

## 2. Draft Answers for Screening & Technical Questions

### Q1: Why Nudge, and why this SDE 2 (Backend - Golang) role?
> **Draft Answer:**  
> "Nudge sits at the intersection of high-concurrency consumer traffic and strict transactional correctness—ingesting shopping bills and third-party app activity, parsing messy payloads asynchronously, and crediting rewards without double-spending. Over the last 3+ years, I have architected multi-tenant Golang microservices, designed PostgreSQL schemas and Redis caching/locking layers, and owned production services end-to-end from design docs to on-call observability. I want to solve hard concurrency, ledger consistency, and event-driven pipeline problems at scale in an AI-first engineering team."

### Q2: How do you ensure reward and ledger flows stay consistent under concurrent uploads, retries, and partial failures?
> **Draft Answer:**  
> "I combine database-level invariants with idempotent request handling. Every credit/debit action carries a client or event-derived idempotency key enforced by a unique constraint in PostgreSQL alongside append-only ledger entries wrapped in atomic transactions. For concurrent duplicate uploads targeting the same account or bill hash, I pair short-lived Redis distributed locks (or rate-limiting token buckets) with row-level `SELECT ... FOR UPDATE` inside the PostgreSQL transaction so correctness never depends solely on cache availability. Downstream side effects use an outbox/event-driven retry mechanism with dead-letter handling so partial failures recover safely without double-crediting."

### Q3: How do you structure Go concurrency using goroutines, channels, and `context` for production reliability?
> **Draft Answer:**  
> "I avoid unbounded goroutine spawning by using bounded worker pools or `errgroup` with explicit concurrency limits. Every downstream call, DB query, and third-party integration accepts a `context.Context` with deadlines and cancellation propagation so slow dependencies do not leak goroutines or exhaust connection pools. Channels are scoped clearly for worker coordination or fan-in/fan-out pipelines with explicit `select` on `ctx.Done()`, and all concurrent paths are validated with `go test -race` and monitored via goroutine-count metrics and `pprof` profiles."

### Q4: How do you build reliable third-party integrations when external platforms have strict rate limits, flaky auth, or messy payloads?
> **Draft Answer:**  
> "At Moresand and MAQ, I isolated external integrations behind dedicated adapter boundaries with strict timeouts, token refresh locking (singleflight/Redis lock so concurrent workers do not stampede OAuth refresh endpoints), and client-side rate limiters matching partner quotas. Transient 429/5xx errors trigger bounded exponential backoff with jitter and circuit breakers, while messy external payloads pass through strict schema validation and normalization before entering internal event-driven pipelines."

### Q5: How do you use AI coding tools (Claude Code, Cursor, GitHub Copilot) while maintaining high code quality?
> **Draft Answer:**  
> "I use Claude Code, Cursor, and GitHub Copilot daily for prototyping service boilerplate, generating edge-case table-driven tests, drafting migrations, and speeding up root-cause exploration across unfamiliar modules. However, AI-generated code is treated strictly as a fast draft: I review concurrency invariants, `context` propagation, SQL query plans, error wrapping, and security boundaries manually, run `-race` and automated test suites before review, and enforce clear team review standards so speed never compromises production reliability."

---

## 3. Items Requiring User Confirmation Before Submitting

- [ ] **Current Company:** Confirm `Moresand Technologies` is still your current employer.
- [ ] **Current Location & In-Office Readiness:** Confirm you are in `Bengaluru` and available to work from Nudge's Bangalore Corporate Office.
- [ ] **Golang Production Depth Comfort:** Confirm you are prepared for live Go coding, goroutines/channels/`context`, `pprof` debugging, and PostgreSQL transactional ledger design interviews (given master `resume.tex` originates in Node.js/Java/Python).
- [ ] **Notice Period:** Confirm exact notice period / earliest joining date (e.g., Immediate / 30 days / 60 days).
- [ ] **Current & Expected CTC:** Provide current fixed/variable CTC and target expected CTC if requested by Keka's form or recruiter call.
- [ ] **Work Authorization:** Confirm unrestricted authorization to work full-time in India.
