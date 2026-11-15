# Application Answers — PhonePe Software Engineer (3–5 years)

---

## Why PhonePe?

PhonePe operates at a scale very few engineering teams in India experience — 70 Crore users, 5 Crore merchants, and financial flows that cannot afford downtime. I've built multi-tenant platforms and high-scale backend services, and I want to work where the load is real and the engineering challenges require genuine systems thinking — not just feature delivery.

## Describe a complex distributed system you designed or owned.

At Moresand Technologies, I architected a multi-tenant CMS platform for 5+ luxury travel brands on a single codebase. I owned schema design, API versioning, service boundary decisions, and the concurrent REST API layer under high traffic. The core challenge was enforcing strict separation of concerns while sharing infrastructure — I applied OOD principles and module decomposition to keep each brand's data isolated within a shared runtime, reducing new-brand onboarding time by 50%.

## Describe a performance optimisation you led.

At Moresand, I profiled high-traffic API endpoints and identified that repeated downstream calls on every request were the primary latency driver. I built a Redis-backed caching layer with configurable TTLs per endpoint type, which significantly reduced API response latency under concurrent load and reduced downstream service pressure.

## How do you approach TDD and testing discipline?

At Techolution I applied TDD from the ground up — writing unit tests before implementation, using integration tests to validate service contracts, and E2E acceptance tests to cover user-facing flows. We achieved 90% test coverage. I treat tests as first-class citizens: when refactoring, tests get refactored too.

## What's your experience with high-volume data systems?

At MAQ Software I built a backend service integrating Azure AI Search (Elasticsearch-backed vector search) for an enterprise AI assistant handling high-volume data retrieval. The challenge was ensuring retrieval latency stayed within SLA bounds under concurrent user load — I implemented concurrency controls in the Node.js service and maintained production observability through structured logging and CloudWatch alerts.

## Describe a time you mentored a junior engineer.

[Requires personal confirmation.] Framing: At HACKIIITV 2019, led a team of 5 engineers — responsible for technical direction, module decomposition, and reviewing each engineer's implementation. At Moresand (SDE2), I conducted structured code reviews with documented feedback for junior team members, enforcing OOD and SOLID principles as part of the review process.

## Skills gaps to prepare for interview.

- **Java production depth:** Listed as primary; primary production language is Node.js. Prepare to discuss Java's concurrency model (threads, synchronisation, ExecutorService) and OOD in Java.
- **NoSQL depth (HBase, Aerospike):** MongoDB and Redis are strong; HBase and Aerospike are listed but less hands-on. Frame Redis expertise as analogous to Aerospike's key-value model; HBase as column-store for analytics use cases.
- **Multi-threading specifics:** Prepare examples around concurrent API handling in Node.js event loop and async patterns; if Java is probed, study `synchronized`, `ReentrantLock`, and `CompletableFuture`.
