# Application Answers — Increff | Software Development Engineer II (SDE-II)

**Prepared:** October 30, 2026

---

## Application Form

Zoho Recruit ATS — contact info, resume upload, work authorization, screening questions.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Describe a technical area you owned end-to-end. How did you plan, design, ship, and hold its quality bar?**

At Moresand, I own the multi-tenant platform integration layer — the component that connects our SaaS platform to 5+ enterprise clients with different data models, auth patterns, and business rules. I treat this like a mini-product. I write the HLD (which service handles what, how data flows, what the API contract is, what the failure modes are) before any code is written. That document is readable outside the immediate team — product, QA, and client teams can verify their understanding against it. The LLD covers implementation choices: which data is stored where, how we handle partial failures, how we version the API. Shipping means I own the release checklist: what tests must pass, what rollback looks like, what the cut-off criteria are for production readiness. Running it means I own the alerts and dashboards — if a latency spike hits, I know about it before clients do. For quality, I act as merge-quality gatekeeper: I review for correctness, security, and performance, not just for "does it work." When a defect reaches production, I run RCA and document it — both the root cause and the process gap that let it through. That RCA feeds back into test coverage and alert thresholds.

**2. Walk me through a system design decision you made. What did you trade away?**

At Moresand I designed the caching strategy for our high-traffic API endpoints. The options were: (a) application-level Redis cache with TTL-based invalidation, (b) database-level materialized views, (c) no caching with read replicas. I chose (a). Trade-offs: Redis cache is fast and horizontally scalable, but introduces potential stale-data windows. Materialized views would have been consistent but tied us to the database layer and added operational complexity. No caching with read replicas would have been simpler but wouldn't meet our latency targets at peak load. I chose Redis with a short TTL (30s) and explicit invalidation on write paths where consistency mattered. The trade-off I named explicitly: eventual consistency on reads for non-critical data, in exchange for sub-50ms p99 response times at 10x peak load. I documented this in the HLD with the reasoning — the next engineer who touches this cache knows why TTL is set to 30s and not 5 minutes.

**3. Describe a production incident. How did you diagnose it, contain it, and run the RCA?**

At Moresand, we had a latency spike on a client's API endpoint — p99 jumped from 80ms to 1200ms. Alert fired at 2am. I checked the dashboard first: database query latency was elevated. Structured logs showed a specific query pattern appearing 40x more frequently than baseline. The root cause: a new feature had introduced a missing index on a compound query — the query plan degraded from index seek to full table scan as the dataset grew past a threshold. Containment: I deployed a hotfix adding the index (online index creation, no downtime) within 25 minutes of alert. p99 returned to 75ms within 2 minutes of the index being ready. RCA doc: root cause (missing index), why it reached production (the performance test dataset was 100x smaller than production — the query plan looked fine in testing), systemic fix (added production-scale data to the CI performance test suite and a query-plan check to code review checklist). The RCA was shared with the full team, not just the people involved.

**4. How do you mentor SDE-I engineers?**

Three tools: design walkthroughs before they write code, code reviews with explanations (not just approvals or rejections), and pairing on hard problems. Design walkthroughs are the most leverage. Before an engineer writes a line, I sit with them for 30 minutes and ask: what are the failure modes? What happens if this service is down? Where does data integrity break? Most engineers haven't thought through these questions yet — not because they can't, but because no one asked them. After the walkthrough, I ask them to write the LLD. I review it and give written feedback. That feedback is a teaching artefact, not just a gate. Code reviews: I leave comments that explain *why*, not just *what*. "This index is missing" is less useful than "this query will full-scan the table once the dataset crosses ~50k rows — add a composite index on (user_id, created_at) and explain why in the PR description." Over time, engineers start catching these themselves. I measure mentoring success by whether engineers can run their own design review without me.

**5. How do you use AI tools in your engineering workflow?**

I use Claude and GitHub Copilot daily, with deliberate scope. Research: when I'm unfamiliar with a pattern or a library, I use Claude to get oriented quickly — not to copy-paste answers, but to understand the trade-off space faster. Task breakdown: for complex features, I describe the problem to Claude and ask it to identify edge cases I might have missed. This is AI for edge-case discovery — I validate each one against the actual system before acting on it. Code generation: Copilot handles boilerplate (test scaffolding, serialization code, config plumbing) well; I review every suggestion for correctness before accepting it. I do not use AI for system design decisions — those require understanding the actual production environment, the actual data volumes, the actual failure history. That understanding lives with me, not in the model.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
- **Spring Boot production experience** — confirm framing (see technology_alignment_and_gaps.md)
