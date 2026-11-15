# Application Answers — Comviva | Full Stack Developer

**Prepared:** October 30, 2026

---

## Application Form

LinkedIn Easy Apply or Comviva ATS — contact info, resume upload, work authorization, screening questions.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/
**Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Interview Q&As

**1. Describe how you design a scalable full stack web application from scratch.**

I start with the API contract — define the endpoints, request/response schemas, auth requirements, and error codes before any code is written. At Moresand, every feature starts with an API spec reviewed by frontend and QA before implementation begins. On the backend, I choose service boundaries based on data ownership and change frequency — I build Node.js/Express.js microservices with clear ownership per domain. On the frontend, I design a component hierarchy: identify what is reusable (form elements, data tables, modals) and what is page-specific, then build the reusable layer first. Performance is baked in from day one — Redis caching for read-heavy endpoints, lazy loading for frontend routes, SSR for SEO-sensitive pages. I validate scalability through load testing and observability (structured logs, custom metrics) before any production launch.

**2. How do you build and structure reusable UI component libraries?**

I think of a component library in three tiers: primitives (buttons, inputs, typography), composites (form groups, card layouts, data tables), and feature components (specific to a domain). Primitives are fully generic and take all their configuration via props. Composites compose primitives with a specific layout contract. Feature components own business logic. At Moresand, I built a modular library of reusable widgets and templates used across 5+ enterprise client brands — each brand configures the same components with different styles via a theme layer. I enforce the library's API through TypeScript interfaces — if a component is used in more than one place, its props type is the contract and must be stable. I also write Storybook-style examples (in Jest) for each component so the team can see usage without running the full app.

**3. How do you design REST API authentication and authorization?**

Three layers. Authentication: I use JWT for stateless auth — the token is issued on login (or OAuth2 callback), contains the user's identity and roles, and is verified on every protected endpoint using middleware. I implement token refresh flows and short-lived access tokens. Authorization: I enforce RBAC at the API level — each route checks the caller's roles before touching data. At Moresand, I added tenant-scoped authorization: every query filters by the caller's tenant ID, enforced at the repository layer so a bug cannot leak data across tenants. SSO: I've implemented OAuth2 flows (Google OAuth in WebHealth) and understand SAML and OIDC patterns. For security, I follow OWASP API guidelines: input validation, parameterized queries, secrets in environment variables, dependency scanning in CI.

**4. How do you approach performance optimization across the full stack?**

I optimize based on measurement, not guessing. Frontend: I use browser DevTools and Lighthouse to identify long tasks, layout shifts, and bundle size issues — then apply code splitting, lazy loading, and image optimization. Backend: I profile slow endpoints with structured query logs and identify N+1 queries — I add appropriate indexes and Redis caching for hot-path data (at Moresand, this reduced API response latency significantly). Database: I review query plans and ensure indexes exist for common filter columns. I set SLOs for p95 response time and alert when they breach — that makes performance a production concern, not a one-time optimization.

**5. How do you work in Agile teams and contribute to engineering quality?**

I treat Agile ceremonies as engineering rituals, not overhead. In sprint planning, I break features into independently shippable slices — each slice has clear acceptance criteria and a testability plan. In standups, I surface blockers early rather than absorbing them quietly. In backlog grooming, I push back on vague requirements and document edge cases before they reach implementation. Code reviews are where I focus on: API contract correctness, test coverage for the happy path and at least one failure mode, and whether new code introduces technical debt. I write code review comments as questions, not commands — "would this break if X?" rather than "change this to Y." I also maintain technical documentation inline with code changes so the team doesn't need me to explain how something works.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
- **Years of experience** — 3.7 years; JD doesn't state a hard year requirement, so answer directly
