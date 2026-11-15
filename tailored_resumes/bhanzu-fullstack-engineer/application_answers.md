# Application Answers — Bhanzu | Full Stack Engineer

**Prepared:** October 30, 2026

---

## Application Form

LinkedIn Apply — contact info, resume upload, work authorization, screening questions.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Describe a full-stack feature you built end-to-end — what did you own from frontend to backend?**

At Moresand, I owned the full delivery of a multi-brand widget system for a travel SaaS platform. On the frontend, I designed and built reusable React.js + TypeScript component libraries with configurable API integrations — each brand got the same components with different data bindings. On the backend, I designed the REST API schema, data models, and Node.js/Express.js service layer that powered those widgets. I built authentication and authorization (tenant-scoped access), Redis-backed caching for high-traffic endpoints, and integrated with third-party data sources. I also owned CI/CD pipelines (Jenkins, Docker) and automated testing (Jest). The entire feature went from design to production with me as the single owner — that's the kind of full-stack ownership I find most natural.

**2. How do you build reusable UI components? What's your approach to component library design?**

I start with the API first: what props does the component accept, what events does it emit, what state does it own internally versus what the parent controls. Good component design is mostly about good API design. I keep components single-purpose — a component that does two things should usually be two components. I build for composability: smaller primitives that combine into larger patterns, not monolithic components that encode every variation. For styling, I use a token-based approach so the component responds to theme changes without internal conditionals. At Moresand, I built a library of reusable widgets used across 5+ enterprise clients — the key discipline was keeping each widget independently testable and not coupling it to any specific client's data shape.

**3. Describe your experience integrating with third-party services and external APIs — what patterns do you use?**

I always wrap third-party integrations in a service layer rather than calling them directly from business logic — this makes it easy to swap providers, add retries, and mock in tests. I design explicit error handling for every third-party call: what happens when they're down, when they return unexpected data, when rate limits are hit. At Moresand, I integrated with 5+ enterprise client APIs — each with different auth patterns and data models — through a shared integration library with retries, backoff, and structured error logging. At MAQ Software, I integrated Azure AI Search and LLM inference APIs into a backend pipeline, where reliability and latency management were critical. I validate external API responses with type guards before accessing fields and never assume the shape will match documentation.

**4. Tell me about your experience with authentication and authorization mechanisms**

I've implemented JWT-based authentication and role-based authorization (RBAC) in production systems. The pattern I use: authentication at the API gateway layer validates the token and attaches the user identity; authorization is enforced at the resource layer, where every query is scoped to the authenticated user's tenant or role. At Moresand, I built tenant-scoped data access — a bug cannot leak one client's data to another because the query itself carries the tenant filter, not just a middleware check. At MAQ Software, I implemented auth flows for an enterprise AI assistant, including OAuth-based identity and API key management for external integrations. I also built Google OAuth integration in WebHealth, my personal project.

**5. How do you approach debugging across the full stack — frontend, API, database?**

I start by isolating the layer where the failure occurs. For a user-reported bug, I trace the request: does the browser send the right payload? Does the API receive it? Does it return the expected response? Does the frontend render it correctly? I use structured logging on the backend to reconstruct what happened at each step, and browser dev tools on the frontend to inspect network requests, state, and render behavior. The hardest bugs span multiple layers — for example, a performance issue that looks like a slow API but is actually a missing database index. For those, I look at end-to-end traces: API latency breakdown, query execution plans, and frontend paint timing together. At Moresand, I've debugged production incidents spanning Redis cache invalidation, REST API contract mismatches, and frontend state management — always starting from logs and working toward the root cause.

**6. Why Bhanzu / edtech? What draws you to building educational products?**

I started my career at GeeksForGeeks, where I built features used by millions of students every day. What struck me was how directly the quality of the engineering affected the learning experience — a slow page load, a broken component, an unresponsive UI — it's not just a product metric, it's a student who gets frustrated and disengages. Bhanzu is solving a harder version of that problem: not just delivering content, but making mathematics genuinely engaging and experiential. The product complexity — student management, payment processing, assessment platforms, batch scheduling — is exactly the kind of multi-system engineering challenge I find interesting, and the mission of making math accessible is one I find genuinely meaningful.

**7. You list Python in your skills — describe your backend Python experience**

Python has been part of my backend toolkit for scripting, data processing, and automation tasks alongside my primary Node.js/Express.js work. I've used Python for data pipeline scripts, API integrations, and backend utility services. Flask and FastAPI are frameworks I've worked with in personal projects and prototypes — the patterns (routing, middleware, request/response handling, dependency injection in FastAPI) are conceptually identical to Express.js, so the ramp from one to the other is fast. At Moresand, Python is used in our backend alongside Node.js for specific processing tasks. I'm comfortable working in a Python/Flask or FastAPI codebase and the engineering judgment — API design, data modeling, error handling, testing — transfers directly.

**8. How do you handle database performance optimization and query improvement?**

I start by measuring: query execution plans (EXPLAIN in PostgreSQL/MySQL, equivalents in DynamoDB), slow query logs, and application-level latency telemetry. The most common fixes are missing indexes, N+1 query patterns, and fetching more data than needed. I add indexes based on the actual access patterns of the queries, not speculatively. For DynamoDB specifically, access pattern design is critical at the schema level — table design should be driven by the queries you need to run, so I prefer to think through access patterns before writing the schema rather than retrofitting after. For relational databases, I use query builders or ORMs with logging enabled so I can see the actual SQL being generated and catch unintentional full-table scans in code review.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
