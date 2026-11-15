# Application Answers — Diagrid | Fullstack Senior Software Engineer

**Company:** Diagrid  
**Role:** Fullstack Senior Software Engineer (AI & DevEx)  
**Location:** Remote India (Bangalore)  
**Application URL:** https://jobs.ashbyhq.com/Diagrid/06fdf2f3-fff0-4628-b58c-2c07d408e656/application?src=LinkedIn  
**Prepared Date:** November 10, 2026  

---

## 1. Autofill & Basic Fields

| Form Field | Value to Enter | Status |
|---|---|---|
| **Name** | `Shubham Pandey` | Verified |
| **Email** | `mr.pshubham@gmail.com` | Verified |
| **Resume** | Attach `ShubhamPandeyResume.pdf` | Ready (1 page verified) |
| **Phone Number** | `+91-8174081896` | Verified |
| **LinkedIn** | `https://www.linkedin.com/in/shubham-pandey-a74716199/` | Verified |
| **GitHub** | `https://github.com/shubham-pandey12` | Verified |
| **Twitter, blog, portfolio, or personal website** | `https://shubham-portfolio-mocha.vercel.app/` | Verified |
| **Location** | `Bengaluru, Karnataka, India` | Verified |

---

## 2. Long-Form Screening Questions (Copy-Paste Drafts)

### Q1: What is it about Diagrid that makes you interested to work here?
> **Draft Answer:**  
> I've spent the last few years building full-stack platforms in TypeScript/Node.js and React, and at my previous job I worked on an AI assistant backend in production. Getting AI features working in a demo is easy, but making them reliable once real users hit them is the hard part. Since Diagrid comes from the Dapr and KEDA side of distributed systems and is applying that to AI agents and developer tooling, this role is right in line with the kind of engineering work I actually enjoy doing.

### Q2: Describe a time you made a distributed or event-driven system more reliable. What was failing or at risk, and what specifically did you do (e.g., retries, idempotency, handling message ordering, observability)?
> **Draft Answer:**  
> At Moresand, our multi-tenant CMS serves 5+ travel brands from one codebase and pulls data from multiple external brand integrations. During traffic bursts or when an upstream brand API got slow, requests piled up, response latencies spiked, and one shaky integration could slow down pages across the platform. I put a Redis cache in front of our high-traffic endpoints with clear cache keys and invalidation rules, added strict timeouts and versioned contracts around the external API integrations so upstream slowdowns wouldn't hang our services, and paired that with integration tests in CI so contract changes didn't slip into prod. That kept endpoint latencies predictable and cut down on brand deployment issues.

### Q3: Describe a feature or service you owned from design through production. What was the stack, what decisions did you make, and what was the hardest problem you solved?
> **Draft Answer:**  
> At Moresand, I owned our multi-tenant CMS platform end to end, from database schema design to production releases. The stack was Node.js, Express, TypeScript, and React, with relational SQL schemas, Redis for caching, and Dockerized CI/CD. Instead of spinning up separate codebases for every new travel brand, I pushed to keep everything on one shared codebase with versioned REST APIs and a reusable React widget/template library. The toughest part was designing the data mapping layer between our frontend components and each brand's backend data. Every brand had slightly different schemas and internal APIs, so getting a clean contract that worked for all 5+ brands without turning the codebase into a mess of special-case conditionals took a lot of iteration, but it ended up cutting new-brand onboarding time by about 50%.

### Q4: What AI tools do you use in your daily work? How frequently?
> **Draft Answer:** *(Add the exact tools you use daily, e.g., Cursor, Claude, GitHub Copilot)*  
> I use AI coding tools pretty much every day while working, mostly for exploring unfamiliar parts of a codebase, scaffolding repetitive TypeScript/Node.js boilerplate, writing unit tests, and sanity-checking tricky bugs. I also work with LLM APIs when building AI features.

### Q5: Can you give me an example how you automated or improved any part of your work using AI?
> **Draft Answer:**  
> At MAQ Software, I built a Node.js backend service for an internal AI assistant using Azure AI Search. Early on, retrieval quality was inconsistent because prompts and search results weren't structured cleanly. I built an orchestration layer that refined how context was retrieved, filtered, and passed into the model, which improved prompt accuracy by 28%. Outside of product code, I regularly use AI tools to generate initial test cases for new API endpoints and catch missed edge cases before I open a PR.

---

## 3. Multiple-Choice & Logistics Questions

| Question | Suggested Answer | Confirmation Status |
|---|---|---|
| **TypeScript/Node.js experience** | `2–4 years` | Verified (~3.4 yrs FT Jul 2023–Nov 2026 / ~3.9 yrs incl. Jan–Jun 2023 internship) |
| **In your last role, how was your work split between frontend and backend?** | `Pretty much 50/50. On the backend I handled database schemas, REST APIs, API versioning, Redis caching, and CI/CD in Node.js/TypeScript. On the frontend I built and maintained our reusable React/TypeScript widget and template library.` | **Confirm exact ratio** |
| **What are your compensation expectations for the role?** | `[USER TO FILL — enter target INR / USD annual expectation]` | **Requires your input** |
| **What is your official notice period (share Immediate / ≤30 days / 31–60 / 61–90 / 90+)? Also comment on your last working day if serving notice.** | `[USER TO FILL — e.g., 30 days / 60 days, and state whether serving notice or buyout/negotiable]` | **Requires your input** |
| **Do you now or will you in the future require immigration sponsorship to work at Diagrid?** | `No` (for Remote India role) | **Confirm** |
| **Are you legally authorized to work in the country/state/province where this position is located?** | `Yes` (authorized to work in India) | **Confirm** |
| **Core US overlap window of 8:30 PM to 12:00 AM IST (12:00 PM IST start). Does this work for you?** | `[USER TO SELECT — Yes / No]` | **Requires your confirmation** |
| **Are you currently based in India? Which city?** | `Yes — Bangalore (Bengaluru), Karnataka` | **Confirm** |
| **If you selected "other city in India" please specify below** | *(Leave blank if Bangalore is a selectable option; otherwise enter `Bengaluru, Karnataka`)* | Verified |
