# Application Answers — Navan | Senior Fullstack Engineer

**Prepared:** October 30, 2026

---

## Likely Screening Questions

**1. Describe a time you designed and owned a complex enterprise feature end-to-end.**

At Moresand Technologies, I designed and delivered a configurable approval workflow system for a multi-tenant SaaS platform serving 5+ enterprise clients. Owned it from schema design (MySQL) through REST API contracts, frontend integration (React.js, TypeScript), deployment on AWS ECS, and production monitoring. Defined service boundaries, data models, and the policy-based configuration layer that let each client customise their own approval chains without touching backend code.

**2. How have you approached data modelling for high-volume enterprise systems?**

At Moresand, I owned MySQL and PostgreSQL schema design end-to-end — complex joins across normalised entity tables, indexing strategies for high-read API endpoints, and transactional integrity for concurrent write paths. At MAQ Software, I designed data services for an enterprise AI assistant that combined PostgreSQL with vector search for high-volume retrieval. I start with access patterns: which queries must be fast, which can afford a join, and where indexing adds cost. Then schema evolves from those answers, not the reverse.

**3. How do you handle production incidents?**

At Moresand, I was primary on incident response: structured alerting through Grafana/CloudWatch, immediate triage on symptoms vs. root cause, rollback when needed, and zero-downtime fixes via blue-green deployments on AWS ECS. I maintained runbooks for known failure modes and authored post-incident write-ups. Mentored junior engineers on using the same runbook discipline so the team could triage without escalating to me.

**4. How do you use AI dev tools in your engineering workflow?**

I use GitHub Copilot for code completion and Claude for architecture discussions, debugging, and documentation. At MAQ Software, I applied Claude throughout the development loop for an enterprise AI assistant backend — generating test scaffolding, reviewing API contract designs, and validating outputs against production requirements before shipping. I treat AI-generated output as a high-quality draft that needs review and adjustment, not a final answer.

**5. Tell me about a time you mentored junior engineers.**

At Moresand, I ran structured code reviews where I paired reviewers with specific checklist items — not just "looks good" but "explain why this index is here" and "what happens if this transaction rolls back mid-flight." Junior engineers improved PR quality measurably within two sprints. I also documented runbook patterns and system design decisions so knowledge didn't stay locked in my head.

**6. Why Navan?**

Navan's product sits at the intersection of two technically rich domains: real-time travel data and enterprise expense management. The engineering challenges — approval workflows, policy engines, multi-currency data modelling, high-volume transactional integrity — are exactly the problems I have been solving at Moresand. The scale (enterprise clients, global travel data) and the fullstack ownership model match what I want to do next.

**7. Describe your experience with microservices and API design.**

At Moresand, I designed microservice boundaries for a multi-tenant SaaS platform — separating concerns across approval, configuration, client management, and data ingestion services. Each service had its own data contract: versioned REST APIs with explicit request/response schemas. At MAQ Software, I built a backend service that orchestrated across Azure AI Search, PostgreSQL, and LLM APIs — all wired through a clean REST API that the React frontend consumed. I default to RESTful APIs over GraphQL unless the client has genuinely complex query needs.

---

## Answers Requiring User Confirmation

- **Total years of experience** — resume shows ~3.7 years; JD asks for 4–6 years; confirm how to answer if asked directly
- **Current notice period** — confirm before answering
- **Expected compensation / salary range** — confirm before answering
- **Willingness to work hybrid from Bengaluru office** — confirm
- **Work authorization / visa status** — confirm before answering
