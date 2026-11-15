# Application Answers — Sage | Software Engineer

**Prepared:** October 30, 2026
**Note:** Contract role — confirm contract terms, rate, and duration before applying.

---

## Application Form

LinkedIn Easy Apply or Sage Careers portal — contact info, resume upload, work authorization, contract rate/availability.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Interview Questions — Using JD Language

**1. Describe a system you designed with strong service/API contracts, versioning, and backward compatibility.**

At Moresand, I own the API contract design for a multi-tenant SaaS platform serving 5+ enterprise clients. The backward-compatibility constraint is real — clients run on different release schedules, so breaking an API means breaking a live production brand. My approach: version every public API from day one (v1/v2 paths), design contracts as explicit typed schemas reviewed before implementation, and run automated API compatibility tests in CI that fail on breaking schema changes. For backward compatibility in practice: additive changes only in existing versions, deprecation notices with migration timelines, and a compatibility matrix updated with every release. The Moresand platform has zero reported backward-compatibility regressions in its lifetime because the contract discipline is upstream of the code.

**2. Walk me through how you design and build event-driven integrations.**

At Moresand I built event-driven data flows between the platform's services and client brand systems. The design starts with the event schema — what data, in what shape, with what guarantees (at-least-once, idempotent consumers). I use Redis pub/sub for lower-latency internal events and REST webhooks for external delivery, with structured logging on every event processed. At MAQ Software I built an event-driven retrieval pipeline — search query events triggered document retrieval, context assembly, and LLM inference in a chained async flow. The observability layer was part of the design: every stage logged its input/output and latency, so when accuracy dropped we could pinpoint exactly which stage diverged. For fault tolerance: async processing with retries, dead-letter queues, and circuit breakers for downstream failures.

**3. How do you approach Kubernetes and containerised deployments?**

At Techolution I designed and owned CI/CD pipelines (Jenkins, Docker) for container-orchestrated microservice deployments on Kubernetes, reducing deployment time by 60%. My approach to Kubernetes: services are stateless pods with readiness/liveness probes, config via ConfigMaps and Secrets (never hardcoded), resource limits set per service to prevent noisy-neighbour problems. Deployments use rolling updates with a rollback strategy — if the new pod's readiness probe fails, Kubernetes automatically rolls back. CI pipeline: build → test → container image → push to registry → kubectl apply with the new image tag. Observability in Kubernetes: structured logs shipped to a central aggregator, Prometheus metrics scraping from pod endpoints, and alerts on pod restarts and error rates.

**4. How do you implement observability and telemetry for production services?**

My standard: structured JSON logs (not string blobs), a metrics endpoint (Prometheus-compatible), and distributed traces for cross-service calls. At Moresand I own the telemetry for the entire platform — logs carry request IDs (correlation), metrics track endpoint latency and error rates by brand, and traces connect frontend API calls through the backend service graph. I use this data to set SLOs (e.g., p95 latency < 200ms for core endpoints) and trigger alerts when they breach. At MAQ Software I instrumented the AI orchestration pipeline to track retrieval latency, LLM inference latency, and accuracy (prompt quality metrics) — this is how we found and fixed the 28% accuracy gap. Telemetry is not an afterthought: it's designed into the API contract before code is written.

**5. How do you handle safe engineering changes in a system with compatibility and upgrade requirements?**

The X3 context — preserving partner IP and customer behaviour while modernising — is the same constraint I work under at Moresand (preserving client data and API contracts while refactoring the platform). My approach: (1) characterise current behaviour with automated tests before touching anything; (2) make changes additive and behind feature flags when possible; (3) run regression tests against the characterised behaviour in CI before merge; (4) stage rollouts (dev → staging → canary % of production) with automatic rollback on error-rate breach; (5) maintain a rollback runbook for every release. For schema migrations: expand-contract pattern — add the new column, migrate data, keep old column readable, remove only after all consumers have switched. No production surprises if you define "safe" before you start coding.

---

## Answers Requiring User Confirmation

- **Contract rate / daily rate** — confirm before answering
- **Contract duration preference** — confirm before answering
- **Availability / notice period** — confirm before answering
- **Right to work / work authorisation** — confirm before answering
