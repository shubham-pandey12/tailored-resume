# Application Answers — SDE 2 | Integration Platform

**Prepared:** October 30, 2026

---

## Application Form

No URL provided — company is anonymous ("Top Product-Based Organisation"). Apply via the channel through which the job was shared.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Walk me through an LLD you designed for an integration system. What decisions did you make and what did you trade away?**

At Moresand, I designed the LLD for a multi-tenant integration middleware layer connecting our platform to 5+ enterprise clients — each with different data models, auth patterns, and API contracts. The core design decision was between a shared integration adapter (one adapter per integration type, configured per tenant) versus a per-tenant adapter. I chose the shared adapter pattern: more complex to build upfront but far cheaper to scale — adding a new client meant configuration, not code. I traded away some flexibility (client-specific logic had to fit the adapter contract) for drastically reduced surface area and maintenance cost. Each adapter was typed with strict input/output schemas, validated on ingress, and logged structured events at every stage so integration failures were immediately diagnosable. The LLD documented: data flow, schema contract, error handling at each stage, retry logic, and the circuit breaker pattern for external API failures.

**2. Design an event-driven system for syncing data between two enterprise platforms. Walk me through the architecture.**

Producer → Kafka topic (partitioned by entity type/tenant) → Consumer group → transformation + validation → target system write + acknowledgement → dead letter queue for failures + ELK-stack alerting. Key decisions: (1) Partition by tenant — ensures ordering per tenant without global bottleneck. (2) Idempotent consumers — every write checks if the record exists before inserting/updating; safe to replay. (3) Schema registry — producer and consumer agree on the Kafka event schema; breaking changes require a version bump. (4) Dead letter queue — failed events go to a separate topic; alerting fires; ops team can inspect and replay after fixing the root cause. (5) Observability — every event carries a correlation ID; ELK traces the full journey from producer to target write.

**3. REST vs SOAP vs Webhooks — when do you use which?**

REST: synchronous, stateless, resource-oriented. Use it when the caller needs an immediate response and the interaction is request-response — fetching data, creating records, querying status. SOAP: use when the integration partner requires it (legacy enterprise systems, financial/healthcare standards like HL7/SWIFT), or when you need WS-Security and formal contracts (WSDL). Most new integrations avoid SOAP unless the partner mandates it. Webhooks: use for asynchronous event notification — when the external system should push events to you rather than you polling. Better for high-frequency events (payment status, order updates, IoT data) where polling would be expensive or introduce latency. The integration layer I built at Moresand consumed external Webhooks from clients and exposed REST APIs internally — right tool for each direction.

**4. How do you ensure data consistency across multiple integrated systems when one system fails mid-flow?**

Three layers. First, write-ahead logging: before any state change, log the intent (correlation ID, source event, target system, payload). If the process crashes, replay from the log. Second, idempotent writes: every write operation is safe to retry — target systems check for the correlation ID and skip duplicates. Third, two-phase commit where strong consistency is required (rare — prefer eventual consistency for most integrations). For eventual consistency: the dead letter queue captures failures, ELK alerting fires immediately, and the reconciliation job periodically checks source vs target state and re-syncs drift. At Moresand, I built a reconciliation check that ran nightly and caught any rows that diverged between integrated systems — surfaced as structured ELK alerts with the affected entity IDs.

**5. How would you design a scalable integration middleware for a low-code/no-code platform? What are the key abstractions?**

Three key abstractions: (1) Connector: a typed, versioned adapter for a specific external system (REST/SOAP/Webhook/DB connector). Each connector exposes a standard interface — authenticate, fetch, push, subscribe. (2) Pipeline: a composable sequence of steps — trigger → transform → route → write. Each step is a node in a DAG; the platform runs the DAG and handles retries, error routing, and observability. (3) Schema registry: the data model each connector produces and consumes. The platform validates data against the schema at every step boundary — no silent data corruption. For scalability: pipelines run as stateless workers consuming from Kafka topics, scaled horizontally by partition count. The ELK stack captures every pipeline execution — step inputs, outputs, durations, errors — so users can debug their integrations without engineering support. This is the architecture that makes low-code integration platforms work at scale.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
- **Company name** — if revealed during process, adjust cover letter accordingly
