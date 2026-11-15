# Application Answers — Booking Holdings | Full Stack Engineer 2, Fintech

**Date:** October 29, 2026

---

## Why Booking Holdings?

Booking Holdings operates at a scale few companies reach — hundreds of millions of travellers, billions of dollars in transactions, identity verification workflows that directly affect booking completion and fraud prevention. I'm drawn to the combination of real stakes, a product that genuinely helps people travel, and the engineering complexity of building reliable systems at that scale. The fintech and IDV focus is an area I want to deepen in, and Booking is one of the few places where the domain and the scale exist together.

---

## Why this role specifically?

The FSE2 role sits at the intersection of React micro-frontends and Java/Spring Boot backend services — which is exactly the combination I've been working in. At Moresand, I owned the full stack from Spring Boot REST APIs and MySQL schema design to React micro-frontend widget architecture and production CI/CD pipelines. The third-party vendor integration and IDV/auth dimension of this role also maps to my MAQ work, where I integrated Azure AI Search with Spring Security auth layers and managed vendor contracts with retry/failure logic in production.

---

## Describe a feature you owned end-to-end.

At Moresand, I architected and shipped the multi-brand onboarding system for a luxury travel CMS platform from scratch. I defined the MySQL schema, designed the versioned REST API contract between the Java/Spring Boot backend and the React.js frontend, built the Redis-backed caching layer for high-traffic endpoints, wrote the CI/CD pipeline on Jenkins + Docker, and owned production incident handling after launch. The result was a 50% reduction in new-brand onboarding time across 5+ travel brands. I made architectural decisions (service boundaries, API versioning strategy, auth approach) independently and coordinated with design and product teams for requirements — the full ownership loop this role describes.

---

## How do you approach production reliability and incident handling?

At Moresand, I instrumented production services with observability hooks (logs, metrics, alerts) from day one, not as an afterthought. When incidents happened, I diagnosed issues at the API layer first (error rates, response time spikes), cross-referenced with MySQL query logs for slow-query patterns, and checked Redis cache hit rates for caching regressions. I maintained an incident log per issue with root cause and resolution. At Techolution, I built CI/CD gates that ran unit + integration + E2E tests before every deployment, which caught regressions before they reached production and reduced the frequency of after-hours incidents.

---

## How do you handle third-party vendor integrations?

At MAQ Software, I integrated Azure AI Search as a third-party vendor platform with our Java/Spring Boot backend. The integration required negotiating the vendor's API contract (auth, rate limits, payload shape), building retry and circuit-breaker logic for failure scenarios, and adding Kafka event streams for asynchronous orchestration when synchronous vendor calls were too slow. I also built observability around the integration — tracking vendor latency, error rates, and payload failures separately from our own service errors — so we could isolate vendor issues from internal regressions quickly.

---

## What's your experience with testing?

At Techolution, I established a testing strategy that achieved 90% coverage across unit, integration, and E2E tests using Jest and Cypress for a full-stack React + Node.js codebase. I wrote unit tests for business logic, integration tests for API contracts (including mock vendor responses), and E2E acceptance tests for user flows. At Moresand, I owned the test strategy across frontend and backend services and wired tests into CI/CD gates so every PR had to pass before merge.

---

## Gaps to flag (confirm before submitting)

- **Years of experience:** JD asks for 6+; actual total is ~3.7 years. Frame as depth of ownership (SDE 2, full platform architecture) rather than tenure.
- **IDV/KYC/fraud domain:** No direct fintech background. Frame vendor integration experience (Azure AI Search, third-party API contracts, auth layers) as the closest analogue.
- **Perl/Dropwizard:** No Dropwizard (Spring Boot is the equivalent); no Perl. Both are secondary to the core Java/Spring Boot requirement.
- **(Confirm)** Any specific IDE, tool, or internal Booking platform referenced in the interview process — confirm before interview.
