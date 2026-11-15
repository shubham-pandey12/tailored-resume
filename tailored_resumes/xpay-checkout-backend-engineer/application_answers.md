# Application Answers: xPay Checkout | Backend Engineer

**Company:** xPay Checkout (Y Combinator W24)  
**Role:** Backend Engineer  
**Location:** Bengaluru, Karnataka (4th Floor, 1331 24th Main, HSR, Bengaluru)  
**Apply Link:** https://www.xpaycheckout.com/careers/backend-engineer *(Contact: hello@xpaycheckout.com)*  
**Prepared Date:** November 11, 2026  

---

## Critical Confirmations & Risks Before Applying

Review these items carefully before submitting or taking the intro call:

1. **Experience Bracket Risk (4–6 / 4–8 yrs required vs ~3.4 yrs FT / ~3.9 yrs incl. intern):**
   - Full-time timeline from July 2023 to November 2026 is ~3.4 years (~3.9 years counting the Jan–Jun 2023 GeekForGeeks internship). Confirm how you want to enter total experience on any form field (e.g., `3.5+ years` or `4 years including internship`) without overstating full-time tenure in conversation.
2. **Mandatory Java 21 + Spring Boot + MongoDB Production Depth:**
   - xPay states that hands-on production experience with **Java, Spring Boot, and MongoDB** is mandatory. Your master `resume.tex` lists `Java` and `MongoDB` in Skills Summary, while your primary shipped systems at Moresand, MAQ, and Techolution were built mostly in Node.js, TypeScript, Express, and SQL. Confirm your true comfort level with Java 21, Spring Boot, and MongoDB internals (indexing, transactions vs. atomic updates, document versioning) before coding and architecture rounds.
3. **Additional Stack & Domain Gaps (ClickHouse, AWS SQS/SES, On-Call, Multi-Currency Payments):**
   - Master `resume.tex` includes `Redis` and `AWS (ECS, S3)` but does not list production `ClickHouse`, `AWS SQS/SES`, formal on-call rotations, or cross-border multi-currency payment gateway work. Confirm you are ready to discuss transferable fundamentals honestly while ramping up fast on these areas.
4. **Logistics Requiring Confirmation:**
   - **HSR Bengaluru In-Office Work:** Confirm daily commute comfort to 24th Main, HSR Layout, Bengaluru.
   - **Notice Period:** `[USER TO FILL: confirm current notice period / buyout availability]`
   - **Current CTC / Expected CTC:** `[USER TO FILL: confirm numbers & equity openness for YC W24 startup]`

---

## 1. Standard Profile & Portal Fields

| Field | Value to Enter | Confirmation Status |
|---|---|---|
| **Full Name** | `Shubham Pandey` | Verified |
| **Email** | `mr.pshubham@gmail.com` | Verified |
| **Phone** | `+91-8174081896` | Verified |
| **Current Location** | `Bengaluru, Karnataka, India` | Verified |
| **Current Company & Title** | `Moresand Technologies (Software Development Engineer 2)` | Confirm current status |
| **Education** | `IIIT Vadodara (B.Tech in Information Technology)` | Verified |
| **LinkedIn** | `https://www.linkedin.com/in/shubham-pandey-a74716199/` | Verified |
| **GitHub** | `https://github.com/shubham-pandey12` | Verified |
| **Portfolio** | `https://shubham-portfolio-mocha.vercel.app/` | Verified |
| **Years of Experience** | `~3.4 yrs FT (~3.9 yrs incl. 6-mo intern)` | **Confirm how form asks** |
| **HSR Bengaluru On-Site** | `Yes (already based in Bengaluru)` | **Confirm commute to HSR** |
| **Notice Period** | `[USER TO FILL]` | **Requires your input** |
| **Current / Expected CTC** | `[USER TO FILL]` | **Requires your input** |

---

## 2. Draft Screening Answers (Human Tone: Confirm / Adjust Before Sending)

### Q1. Why do you want to join xPay Checkout?
> xPay is solving one of the hardest infrastructure bottlenecks for global B2B SaaS and travel companies: making cross-border, multi-currency payments reliable across 180+ countries. Having worked on multi-tenant travel platforms in Bengaluru, I have seen firsthand how messy regional integrations and partner contracts get as volume scales. Joining an early YC team where I can work closely with founders, own backend services end to end, and build high-reliability payment flows is the exact environment I want next.

### Q2. Walk us through a backend system you owned end to end from design to production.
> At Moresand Technologies, I architected a multi-tenant platform supporting 5+ luxury travel brands on a single codebase. I owned the schema design, API versioning, and service boundaries from scratch so each brand could integrate internal data cleanly without duplicating core logic. I also built a Redis caching layer for high-traffic endpoints, which cut API latency, lowered development effort by 50%, and cut new-brand onboarding time by 50%. On the delivery side, I set up automated testing and deployment pipelines so releases stayed predictable in production.

### Q3. What is your hands-on background with Java, Spring Boot, MongoDB, Redis, ClickHouse, and AWS?
> *(Note: Adjust this draft based on your actual off-resume Java/Spring Boot/MongoDB depth before sending.)*  
> My production work has centered on backend API architecture, caching with Redis, and running containerized services on AWS (ECS, S3, EC2). While much of my recent production delivery used Node.js and TypeScript alongside SQL and MongoDB, I have strong Java fundamentals and understand Spring Boot service patterns and MongoDB schema modeling, indexing, and atomic update vs. transaction tradeoffs. I have not used ClickHouse, SQS, or SES heavily in production yet, though I am comfortable with asynchronous queue patterns, analytical vs. transactional data separation, and picking up new AWS and data tooling quickly in a small team.

### Q4. How do you think about MongoDB transactions vs. atomic updates and schema versioning in high-throughput systems?
> In high-throughput systems, I prefer designing document models so most state changes stay within a single document and use atomic operators like `$set` or `$inc` paired with conditional filters, since that avoids multi-document transaction locking overhead. Multi-document transactions make sense only when two separate collections or records strictly need all-or-nothing consistency, such as paired ledger or balance updates where partial writes would break invariants. For versioning, storing an explicit schema version or optimistic concurrency version field on documents lets services evolve safely during zero-downtime rollouts and prevents stale concurrent writes from overwriting newer state.

### Q5. Are you comfortable with on-call support and working out of our HSR, Bengaluru office?
> `[Confirm before submitting]` Yes, I am already based in Bengaluru and comfortable working from the HSR office. While my past roles focused more on automated pre-release testing (up to 90% coverage at Techolution) and deployment reliability than formal PagerDuty rotations, I regularly debug production issues and take full ownership of the services I ship.

### Q6. Notice period, current CTC, and expected CTC?
> `[USER TO FILL: e.g., My notice period is X days (negotiable/buyout option). My current CTC is X LPA and my expected CTC is Y LPA + equity.]`
