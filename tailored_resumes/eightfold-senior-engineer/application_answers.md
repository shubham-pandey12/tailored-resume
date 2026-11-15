# Application Answers — Eightfold AI | Senior Engineer (Data Platform)

**Prepared:** October 30, 2026

---

## Application Form

LinkedIn Apply / Eightfold Zoho ATS — contact info, resume upload, work authorization, screening questions.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. How do you design a data integration framework to sync millions of records across multiple external systems?**

The core problem is building a reliable, idempotent sync layer that handles failures gracefully. At Moresand, I built an integration framework to sync data across 5+ external client systems into a single normalized data model. My design approach: define a canonical schema upfront — the "common model" — so every source system maps into the same structure regardless of its shape; write source-specific adapters that handle transformation, type coercion, and field normalization; and make every sync operation idempotent so retries don't create duplicate or inconsistent records. For high-volume syncs, I batch records and process asynchronously with a Redis-backed queue, track sync state per entity, and emit structured events for audit and replay. At scale (millions of records), the key reliability pattern is checkpointing: save progress at each batch boundary so a crash resumes from the last consistent point rather than re-syncing everything. Monitoring is non-negotiable — I attach data health metrics (records synced, error rate, lag) to every pipeline so anomalies surface before users see inconsistent data.

**2. How do you ensure data consistency and quality across distributed storage systems?**

Data inconsistency in distributed systems comes from two places: writes that partially succeed (network failure mid-transaction) and reads that don't reflect the most recent write (replication lag). My approach has three layers. First, idempotent writes with a deduplication key — every record has a stable identifier so re-processing the same event produces the same result. Second, reconciliation jobs that periodically compare source-of-truth and downstream stores and flag (or auto-fix) divergence. At Moresand I built a service that compared the canonical database against cached views and repaired inconsistencies automatically, similar to the framework Eightfold's team built to identify and fix data inconsistencies between storage systems. Third, observable pipelines — every write emits a checksum or hash of the payload; downstream consumers validate on read. When a mismatch surfaces, the structured log carries enough context (entity id, source, timestamp, expected vs. actual) to diagnose root cause quickly.

**3. Walk me through how you'd design REST APIs for a data platform serving millions of users.**

API-first design: define the contract (endpoint, schema, auth, pagination, error codes) before any implementation, and document it in OpenAPI so consumers can validate against it. For a data platform specifically: read endpoints must be designed for high throughput — I use Redis caching on hot data with a TTL matched to acceptable staleness, and avoid N+1 query patterns by composing joins server-side rather than round-tripping. For write endpoints, I enforce idempotency (idempotency-key header) so retries are safe. Rate limiting and auth (JWT/OAuth) are part of the contract, not afterthoughts. I also design for observability from day one: every endpoint emits request latency, error rate, and payload size as metrics — at Moresand this let me spot a slow vendor API call adding 300ms to p99 latency within an hour of rollout.

**4. Describe a technically challenging data or distributed systems problem you solved.**

At MAQ Software, the challenge was building a reliable retrieval pipeline for an enterprise AI assistant where the accuracy of AI responses depended on the quality of data the pipeline served. The system had to ingest documents from multiple external sources (SharePoint, internal databases), normalize them to a common schema suitable for embedding, index them in Azure AI Search, and serve context-aware results to an LLM inference layer — all with low latency and high accuracy. The technically hard part was the normalization step: source documents had inconsistent structure (different field names, nested vs. flat, missing fields), and a bad normalization produced irrelevant search results which compounded into poor LLM responses. I instrumented the pipeline end-to-end — logging what each document looked like before and after normalization, what the retrieval returned, and where the LLM diverged from the expected answer. That instrumentation let me identify that 40% of accuracy issues traced back to three specific normalization patterns. Fixing those three patterns improved prompt accuracy by 28%.

**5. How do you use AI tools in your engineering workflow?**

I use Claude and GitHub Copilot actively, not as code completers but as thinking partners and research accelerators. For a new problem (a data model design, an API contract, a system I haven't worked with before), I use Claude to explore trade-offs, generate edge cases I might miss, and review my design before I write code. For implementation, Copilot accelerates the mechanical parts — boilerplate, test stubs, type annotations — so I can focus on the logic that actually matters. The discipline is: every AI-generated output gets reviewed; I own what ships, not the model. For Eightfold's emphasis on "using AI for research, task breakdown, and edge-case discovery," that's exactly how I use it — as a multiplier on engineering judgment, not a replacement for it.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
