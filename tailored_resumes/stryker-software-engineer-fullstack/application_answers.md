# Application Answers — Stryker | Software Engineer - Full Stack Developer

**Prepared:** October 30, 2026

---

## Application Form

Standard Stryker careers form (Workday) — contact info, resume upload, work authorization, EEO.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Walk me through a time you designed a high-availability backend service.**

At Moresand, I designed and owned the Node.js + Express.js backend services for a multi-tenant SaaS platform serving 5+ luxury travel brands. The availability requirement was core — downtime affects real client bookings. I designed the services around clean REST API boundaries, Redis-backed caching for high-traffic endpoints to reduce database load, and a CI/CD pipeline (Docker + AWS ECS) that deployed with zero downtime. I implemented structured logging and alerting so any degradation surfaced before clients noticed. The system has run without a missed SLA since launch.

**2. How do you ensure code quality and application security in a production codebase?**

Three layers. First, automated testing suites: unit tests for business logic (Jest), integration tests for API contracts, and security checks for known vulnerability patterns — I enforce coverage thresholds in CI so quality can't silently erode. Second, code review discipline: every PR gets a structured review against design specifications before merge. Third, observability: structured logs, metrics, and alerting that surface anomalies in production before they become incidents. At Techolution, I maintained 90% test coverage across unit, integration, and acceptance suites. At Moresand, I own the full testing and deployment pipeline end-to-end.

**3. Describe your experience with GCP.**

My WebHealth project is deployed on GCP Cloud Run with Cloud Logging for observability — I set up the containerized deployment, configured environment variables, and wired Cloud Logging to surface request traces and errors. It handles automated web crawler jobs that run on demand and return consolidated audit reports. At MAQ Software, I deployed backend services to cloud infrastructure with structured logging and alerting integrated into the production monitoring stack. I am familiar with Cloud Run's serverless container model and Cloud Logging's query interface.

**4. How do you approach architectural reviews and technology trade-off decisions?**

I start by writing down the constraints: performance targets, team familiarity, operational complexity, and cost. Then I sketch two or three candidate approaches at the API/data contract level (not at the code level), evaluate each against the constraints, and present the trade-offs to the team before committing. At Moresand, I evaluated trade-offs between a monolith and a microservices split for the multi-brand CMS — chose a modular monolith with service boundaries enforced by TypeScript interfaces, which gave us independent deployability without the operational overhead of separate services at our scale. The decision held as we added 3 more clients without restructuring.

**5. How do you work within Agile teams?**

At Moresand and MAQ Software, I participate in sprint planning (breaking epics into shippable slices with API-contract-first decomposition), backlog grooming (refining stories with product before sprint start so requirements are unambiguous), daily standups, and retrospectives. I run structured code reviews on every PR — not just for correctness but for maintainability and security. I push back on large undifferentiated features and advocate for thin vertical slices that can be demonstrated at the end of each sprint.

**6. Why Stryker?**

The engineering domain — secure, high-availability software in a medical technology context — is exactly where the discipline of building production-grade systems matters most. The constraint that software failures could affect patient outcomes raises the bar for testing, observability, and reliability in a way I find motivating. Stryker's global scale (150M+ patients impacted annually) and the Gurugram engineering team's proximity to global product teams make it a strong environment for technically demanding, high-impact backend work.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
- **Work authorization** — confirm status
