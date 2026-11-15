# Application Answers — Planview | Software Engineer II (AP)

**Prepared:** October 30, 2026

---

## Application Form

Standard Planview careers form — no visible screening questions beyond contact info, resume, and LinkedIn.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Walk me through how you design a multi-tenant REST API in Node.js.**

Start with tenant isolation: every API request carries a tenant identifier (JWT claim or header), and middleware resolves it before any business logic runs. The data layer enforces isolation at the query level — every query scopes to the tenant's data, either via a `tenantId` column with an indexed filter or a schema-per-tenant model depending on scale. API boundaries are typed end-to-end with TypeScript interfaces. At Moresand, I own this exact pattern for 5+ enterprise clients — REST APIs built in Node.js + TypeScript, with permission checks, WIP-style policy enforcement, and tenant-scoped data access all layered through typed middleware.

**2. How do you model domain entities and evolve them over time in a live SaaS product?**

At Moresand, I model domain entities (permissions, approval workflows, role assignments, policy configurations) as typed TypeScript interfaces at the service layer, with the database schema as the source of truth. Schema changes go through migrations with backwards-compatible defaults — never a breaking change in production. New fields are nullable or have sensible defaults; old fields are deprecated before removal. I document the data contract in the API layer so the frontend knows what to expect without reading the database schema.

**3. How do you approach observability for a backend Node.js service?**

Three layers: structured logging (JSON logs with request ID, tenant ID, and severity — never unstructured strings), custom metrics (request latency, error rates, queue depths — pushed to a metrics store and visualised on dashboards), and alerting (thresholds on error rate and latency that page on-call). At Moresand, I own this stack — structured logging, metrics via AWS CloudWatch, and alerting that fires on SLA breaches. The goal is that when something breaks in production, you know which service, which tenant, and which request caused it before you open a terminal.

**4. How do you write testable Node.js code?**

Dependency injection at the service layer — controllers don't instantiate their dependencies, they receive them. This makes unit testing trivial: pass mock repositories or API clients and assert on the output. Integration tests run against a real test database (in-memory or a Dockerised Postgres) to catch anything the unit tests miss. At Techolution, I maintained 90% test coverage across unit and integration tests. At Moresand, I enforce coverage thresholds in CI so they can't drop without a deliberate decision.

**5. How do you work with product to break requirements into shippable slices?**

At MAQ Software, I worked directly with product in sprint planning to split features along API boundaries — backend-complete with a contract first, then the frontend consumes it. This lets both sides ship independently. I push back on large "all-or-nothing" features and propose a thin vertical slice (minimum API + minimum UI) that users can interact with, then iterate. Shippable slices reduce review risk, surface integration issues early, and keep velocity visible.

**6. Why Planview?**

The engineering domain — workflow management, WIP rules, metrics, cross-team visibility — is directly adjacent to the business logic I build every day at Moresand. The scale (3M+ users, Fortune 100 customers) is a step up that I am deliberately targeting: patterns I apply at startup scale become load-tested at Planview's. The Gartner leadership position signals engineering maturity — good codebases, thoughtful architecture decisions, and product direction that comes from real customer feedback.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
