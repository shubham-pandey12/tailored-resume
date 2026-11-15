# Application Answers — Atolls | Senior Full-Stack Software Engineer

**Prepared:** October 30, 2026

---

## Application Form

LinkedIn Apply or Atolls ATS — contact info, resume upload (English CV required), work authorization.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Interview Q&As

**1. Describe how you architect and optimize backend microservices for performance, security, and scalability.**

I start with service boundary design: each microservice owns one domain, communicates over typed REST or GraphQL contracts, and has no shared mutable state with other services. For performance, I layer caching strategically — at Moresand, a Redis-backed caching layer in front of high-traffic API endpoints cut response latency significantly while protecting downstream services from spikes. For scalability, I design services to be stateless so they can be horizontally scaled on ECS; I use connection pooling for database access and size connection pools to match expected concurrency. For security, I build authentication and authorization at the API gateway layer — every inbound request validates a JWT before touching service logic — and enforce least-privilege IAM roles for each AWS service. Observability is built in from day one: structured logs, custom metrics, and alerting so that performance regressions and security anomalies surface before customers notice them.

**2. How do you manage AWS-based microservices (Lambda, API Gateway, ECS) in a production environment?**

I treat the AWS stack as infrastructure-as-code: ECS task definitions and Lambda configurations live in version control alongside the application code. At Moresand, I deploy backend services to ECS with rolling deployments and health check grace periods so that releases never cause downtime. For Lambda, I keep functions single-purpose, keep cold-start latency low by minimizing package size and using provisioned concurrency for latency-sensitive paths, and instrument them with structured CloudWatch logs. API Gateway is where I enforce rate limiting, request validation, and authentication — it is the perimeter, not the service. I use CloudWatch alarms and dashboards as the production health surface and maintain runbooks so the team can respond to alerts without me being the single point of knowledge.

**3. How do you build reusable component libraries and frontend features at scale?**

I design components around props contracts and single-responsibility: each component does one thing and is tested independently. At Moresand, I built a modular library of reusable widgets with configurable API integrations and data mapping — each widget could be assembled into different page layouts across 5+ client brands without modification. I write component tests with Jest and React Testing Library, document the API in the component itself (TypeScript prop types as documentation), and enforce the library boundary through code review — no business logic bleeds into the component layer. For responsive styling I use utility-first approaches (Tailwind CSS / CSS3) with design tokens for color and spacing so the library renders consistently across viewport sizes and themes.

**4. What is your approach to mentoring junior engineers?**

I mentorship through the work itself rather than through separate sessions. The most impactful thing I do is code review that explains the why, not just the what — I comment on the trade-off made, not just the fix needed. At Moresand I pair with junior engineers on design decisions before they write code, which surfaces misunderstandings early when they are cheap to correct. I assign features end-to-end with clear acceptance criteria, then let the engineer drive while I am available for questions — the goal is for them to own the feature, not execute my plan. I track their growth explicitly: after a few weeks on a feature area, I step back and watch whether they can design the next one independently.

**5. How do you approach web security best practices in application development?**

Security is a cross-cutting concern, not a checklist at the end. I enforce it at three layers. First, at the API boundary: all inputs are validated against a schema before any processing; authentication uses short-lived JWTs with refresh-token rotation; authorization is role-based and enforced in the service layer, not just the gateway. Second, in data handling: parameterized queries everywhere, secrets in AWS Secrets Manager never in code, and tenant-scoped data access so a bug cannot leak one client's data to another. Third, in the supply chain: dependency scanning in CI (npm audit / Snyk), container image scanning before ECS deployment, and IAM roles with least-privilege policies for each service. I also run OWASP Top 10 checks as part of code review for any feature that touches auth flows, file uploads, or external API integrations.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
