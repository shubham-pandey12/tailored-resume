# Application Answers — Arcana Analytics | Senior Frontend Engineer

**Prepared:** October 30, 2026

---

## Greenhouse Application Fields

The form only asks for: First Name, Last Name, Email, Phone, Country, City, Resume/CV, LinkedIn, Website. No screening questions beyond contact and resume.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Describe how you have architected a React frontend for a compute-intensive or data-heavy application.**

At Moresand Technologies, I architected the React.js + TypeScript frontend for a multi-tenant enterprise SaaS with complex data-heavy UI — multi-step approval flows, data tables with thousands of rows, and real-time status updates. For performance: virtualised list rendering, memoisation at component boundaries, code splitting per route, and lazy loading below the fold. At MAQ Software, I built a React frontend rendering high-volume, real-time Azure AI search results — the I/O-intensive challenge there was minimising re-renders while streaming new results in, solved with controlled state batching and optimised component trees.

**2. How do you approach building a backend API server that integrates with a data infrastructure layer?**

I start from the data contract: what does the frontend need, in what shape, at what latency? Then I design the API layer (Node.js/REST or GraphQL) with typed request/response schemas that abstract the infrastructure layer from the frontend. At Moresand, I built Node.js REST APIs integrating MySQL and PostgreSQL schemas — handling complex joins, pagination, and transactional integrity. At MAQ Software, I built a Node.js backend service integrating vector search, PostgreSQL, and LLM APIs into a single structured data pipeline that the React frontend consumed. The principle is the same: the API server is a translation layer between raw infrastructure and the consumer's needs.

**3. Tell me about a time you improved system scalability or fixed a performance bottleneck.**

At Moresand, I identified that high-traffic API endpoints were hammering the database on every request. I built a Redis-backed caching layer on the Node.js side with TTL-based invalidation, reducing database load significantly and enabling 50% reduction in development effort through predictable response times. On the frontend, I profiled with React DevTools and identified unnecessary re-renders in the data table components — added memoisation at the row level and virtual rendering, measurably improving render time for large datasets.

**4. How do you collaborate with Product and Design to define feature specifications?**

At MAQ Software, I partnered with the Product and Design teams on the AI assistant frontend — attended spec reviews, pushed back on designs where the technical cost of animation or layout complexity wasn't worth the UX gain, and proposed simpler component-level solutions that shipped faster. I document my decisions in comments and PRs so the product team can track the tradeoff without reading the code.

**5. Walk me through a project you owned end-to-end.**

WebHealth — a self-initiated website health auditing platform. I identified that website auditing required switching between multiple tools manually, designed a unified platform from scratch: React.js frontend with responsive UI, Node.js/Express.js backend API server, a custom multi-page web crawler, Google Lighthouse integration for performance profiling, passive security scanning, and automated consolidated audit reporting. Deployed on GCP. No one asked for it — I spotted the gap, designed the system, built it, and deployed it.

**6. What is your experience with object-oriented software design?**

OOP is my default design approach. At Techolution, I enforced OOP principles and SOLID design patterns across the codebase — single responsibility for each service, dependency inversion through interfaces, and open/closed principle for adding new features without modifying existing logic. At Moresand, I applied OOP design patterns when structuring the Node.js API layer — each resource has its own controller, service, and repository layer with clear boundaries. I reviewed code against these principles in every code review.

**7. Why Arcana Analytics?**

Analytics infrastructure is one of the hardest engineering domains — data-intensive, performance-critical, and the gap between a slow dashboard and a fast one is the gap between a product people use and one they don't. The role's combination of deep React frontend and backend API server ownership is exactly what I want: full-stack with a clear frontend emphasis, where my performance optimisation and system design experience both matter.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
