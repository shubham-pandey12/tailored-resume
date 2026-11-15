# Application Answers — Crunchyroll | Software Engineer, Service Monetization

**Prepared:** October 30, 2026

---

## Application Form

Greenhouse ATS — contact info, resume upload, screening questions.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

### Screening Questions

- **Non-competition agreement:** No
- **Immigration sponsorship required:** No
- **Comfortable working from Hyderabad?** ⚠️ **USER TO ANSWER** — role is Hyderabad hybrid (2 days office, 3 days WFH); Shubham is based in Bengaluru. Confirm before submitting.
- **Years of engineering experience:** 3–4 years

---

## Likely Interview Questions

**1. Describe a distributed backend system you built — how did you handle reliability, security, and scale?**

At Moresand, I own the backend of a multi-tenant SaaS platform serving 5+ enterprise clients on a single codebase. The reliability engineering is layered: authentication and data isolation are enforced at the query level, so a bug cannot leak one tenant's data to another — that is a security guarantee, not just a practice. For reliability, I built structured logging, custom metrics, and alerting from the start, which means we catch anomalies before users do. For scale, I designed a Redis-backed caching layer for high-traffic endpoints that significantly cut latency under load. When something goes wrong in production, our observability stack narrows the root cause to a specific API, query, or integration within minutes — not hours. The same discipline applies to every system I build: observability is not optional, and production reliability is a first-class engineering requirement.

**2. How do you approach operational excellence — on-call, incident management, observability?**

My definition of operational excellence is: the system tells you what is wrong before a customer does, and the team can diagnose and resolve it quickly without tribal knowledge. At Moresand, I built structured logging with a consistent schema (request ID, tenant ID, operation, duration, status) so that any incident can be traced from the API call to the database query. Custom metrics feed alerting rules with noise-adjusted thresholds — I do not alert on every 5xx, I alert when the rate exceeds baseline by a meaningful margin. For incident management, I document response runbooks: for each critical alert, what the alert means, what to check first, and what the escalation path is. That means anyone on-call can respond effectively, not just the person who built the system. At Techolution, I reduced deployment time by 60% by improving CI/CD pipeline reliability — because flaky deployments are an operational excellence failure.

**3. Tell me about your experience with secure backend systems — authentication, data protection, access control.**

Security for me has three layers: design, practice, and observation. At Moresand, every API endpoint enforces tenant isolation at the query level — the WHERE clause is always scoped to the authenticated tenant's ID, not a parameter the client controls. Authentication uses JWT with short-lived access tokens and refresh flows. Sensitive configuration (keys, secrets, connection strings) lives in environment variables managed outside the codebase. In code review, I flag any raw string interpolation into SQL (parameterized queries only), any user-controlled value used in a file path, and any logging of credentials or PII. At the observation layer, I alert on unusual auth failure spikes — a spike in 401s often indicates a credential stuffing attempt rather than a bug. For a payments platform like Crunchyroll's, I would apply the same discipline to PCI-relevant data flows: explicit data classification, access control by role and need-to-know, and audit logging for any access to cardholder data.

**4. How do you integrate with external APIs and providers? What patterns do you use for reliability?**

My integration pattern is: contract-first, fail gracefully, observe everything. Contract-first means I define the expected request/response schema, error codes, and authentication flow before writing any integration code — and I write integration tests that validate the contract against a real or realistic test environment. For reliability, I wrap every external call with a timeout (I never leave a fetch unconstrained), implement exponential backoff with jitter for retries on transient failures, and circuit break after repeated failures to avoid cascading timeouts. At Moresand, I built a shared integration library that applies these patterns consistently across all enterprise client integrations — so the reliability behavior is uniform, not per-developer. For a payments provider integration at Crunchyroll, I would also implement idempotency keys on every payment-initiating call, so retries never double-charge.

**5. Describe your Agile workflow — sprint planning, estimation, delivery.**

I break work into thin, deployable slices with clear acceptance criteria before estimating. For sprint planning, I produce a spike or technical breakdown first for any significant new work — not to gold-plate the design, but to surface hidden complexity before committing to a sprint timeline. My estimates are ranges (1–2 days, 3–5 days) rather than single points, and I flag the assumptions that would move the estimate. During the sprint I track progress against the estimate daily and communicate blockers early — I do not wait until the last day of the sprint to surface a risk. At Moresand, my task estimates have been accurate within one sprint more than 90% of the time, which I attribute to upfront design thinking and explicit assumption-tracking.

**6. Why Crunchyroll and Service Monetization specifically?**

The Service Monetization team is directly tied to revenue and fan membership — that means the engineering bar for reliability, security, and correctness is exceptionally high. A bug that double-charges a user or drops a subscription renewal is not just a technical failure; it is a trust failure with a real person who loves anime. That kind of stakes makes the engineering more meaningful, not less enjoyable. Crunchyroll's scale — 100M fans, 200+ countries, millions of payments — is also genuinely interesting from a distributed systems standpoint. The problems the team works on (fraud detection, passive churn reduction, payment provider integrations, PCI compliance) are complex, consequential, and technically deep. That is exactly the kind of work I want to be doing.

**7. You don't have payments/fintech experience — how would you ramp on PCI compliance and the payments domain?**

I would approach PCI compliance the way I approach any regulated engineering domain: read the standard (PCI DSS), map our systems against its requirements, and identify the gaps. The core engineering principles of PCI are not foreign to me — access control by need-to-know, audit logging for cardholder data access, encryption in transit and at rest, tokenization to minimize PCI scope. These are standard secure engineering practices I already apply; PCI formalizes them with specific controls and audit requirements. For the payments domain specifically, I would study the team's existing integrations with payment providers, learn the idempotency and retry patterns already established, and shadow on-call for the first rotation before taking primary responsibility. My ramp would be measured in weeks for the technical domain, not months.

**8. How do you ensure backend services remain reliable under high traffic and millions of transactions?**

Four practices. First, measure before you optimize: I always establish a performance baseline with real traffic patterns, not synthetic benchmarks, so I know what "normal" looks like before load increases. Second, design for failure: I assume any downstream service will fail, and build retries, timeouts, and fallbacks into every integration. Third, limit blast radius: I prefer async processing for non-critical paths so that a spike in one workflow does not degrade another. Fourth, automate recovery: for predictable failure modes (cache miss storms, brief database unavailability), I implement automatic recovery paths rather than requiring manual intervention. At Moresand, this discipline keeps our SaaS platform at production reliability even during enterprise client onboarding spikes. For a payments platform processing millions of transactions, I would additionally ensure all payment-initiating operations are idempotent so that retries under high load never introduce duplicate charges.

---

## Answers Requiring User Confirmation

- **Comfortable working from Hyderabad?** — role is Hyderabad hybrid; Shubham is based in Bengaluru. Confirm before submitting.
- **Current compensation** — confirm before answering
- **Expected compensation (Total Rewards expectations)** — this is an optional form field; confirm how to respond or leave blank
- **Notice period** — confirm before answering
