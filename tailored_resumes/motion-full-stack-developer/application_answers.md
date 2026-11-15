# Application Answers — Motion | Full Stack Developer

**Prepared:** October 30, 2026

---

## Application Form

The Rippling ATS form collects standard contact info only — no screening questions visible. Submit: name, email, phone, location (city), resume/CV, LinkedIn, website.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Walk me through your TypeScript full-stack experience.**

TypeScript is my primary language across the stack. At Moresand, I use TypeScript end-to-end — Next.js SSR frontend with typed component props, React hooks, and API calls, and Express.js backend with typed request/response schemas, service layers, and PostgreSQL query results. At MAQ Software, I built a Next.js + TypeScript frontend consuming typed Express.js REST APIs I designed myself. TypeScript's contract layer between frontend and backend — knowing at compile time that a field exists, is the right type, and is non-null — is one of the main things I value about the stack.

**2. How have you used Next.js SSR/SSG in production?**

At Moresand, I use Next.js SSR for the multi-tenant SaaS platform — server-side rendering client-specific data at request time so each enterprise client sees their own context without client-side data fetching delays. At MAQ Software, I used Next.js SSR for the AI assistant frontend to preload search results server-side before hydrating the client. At GeeksForGeeks, I built Next.js components with SSR that improved page load performance by 40% on a high-traffic platform — code-splitting and lazy loading on top of SSR for the pages that didn't need fresh server data.

**3. Describe your experience with Express.js backend APIs.**

Express.js is my primary backend framework. At Moresand, I own the Express.js API layer serving the Next.js frontend — typed TypeScript middleware, PostgreSQL integration, complex join queries, pagination, and error handling. At MAQ Software, I built Express.js services integrating vector search, PostgreSQL, and LLM APIs under a unified typed contract. WebHealth — a self-initiated project — also has a Node.js/Express.js backend handling crawl orchestration, Lighthouse API calls, and structured result storage. I structure Express.js services in controller/service/repository layers with TypeScript interfaces at each boundary.

**4. How do you approach clean, testable code in a full-stack TypeScript codebase?**

TypeScript is the first layer: strict mode, no `any`, typed all the way through. For testability: pure functions where possible, dependency injection for services that touch databases or external APIs, Jest for unit and integration tests. At Techolution, I maintained 90% test coverage across unit, integration, and automated acceptance tests. At Moresand, I established clean TypeScript standards through code review — if a PR introduces `any` or skips a type guard, I flag it and explain why before approving.

**5. How have you worked with PostgreSQL?**

At Moresand, I own the PostgreSQL schema design for a multi-tenant SaaS — entity tables with foreign keys, complex joins across 5+ tables, indexing strategies for high-read API endpoints, and transactional integrity for concurrent write paths. At MAQ Software, I integrated PostgreSQL with vector search for high-volume AI data retrieval — optimising queries under SLA constraints. I write raw SQL for complex queries and use ORMs (Prisma/TypeORM) for standard CRUD — knowing when each is the right tool.

**6. Why Motion?**

Fleet management is a domain full of real operational pain — fuel costs, back-office friction, data that doesn't flow between systems. Building the technology to remove that friction, for companies that run on tight margins and depend on every truck moving efficiently, is a meaningful engineering problem. The tech stack (TypeScript, Next.js, Express.js, PostgreSQL) is exactly what I work in day-to-day, and the startup pace at Motion matches the environment where I do my best work.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
- **City for location field** — confirm (Bengaluru?)
