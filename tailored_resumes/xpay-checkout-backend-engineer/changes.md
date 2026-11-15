# Changes from Master Resume — xPay Checkout | Backend Engineer

**Prepared:** November 11, 2026  
**Target Company:** xPay Checkout (Y Combinator W24)  
**Target Role:** Backend Engineer  
**Source URL:** https://www.xpaycheckout.com/careers/backend-engineer  

---

## 1. Master Resume Hash Verification

- **Master resume path:** `/Users/shubhampandey/Desktop/SP/job-hunter/resume/resume.tex`
- **Initial SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Post-completion SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Verification status:** Verified identical — master `resume.tex` was never modified.

---

## 2. LaTeX Preamble Adjustment

- Updated `\addtolength{\topmargin}{-.45in}` to `\addtolength{\topmargin}{-.70in}` per Rule 3.
- Kept `\oddsidemargin` (`-0.530in`), `\evensidemargin` (`-0.375in`), `\textwidth` (`1in`), `\textheight` (`1.15in`), packages, fonts, and custom commands verbatim from master `resume.tex`.

---

## 3. Skills Summary Changes

Rewrote the 5 `\resumeSubItem` rows to mirror xPay Checkout's Java 21 / Spring Boot / MongoDB / AWS backend stack and remove unrequested frontend/Node.js items per Rule 1 ("Java only, no Node.js"):

| Category | Tailored Content | Rationale |
|---|---|---|
| **Languages \& Core** | `Java 21, Spring Boot, REST APIs, API Design, System Design, Distributed Systems` | Mirrors xPay's core Java 21 + Spring Boot service stack and architectural fundamentals. |
| **MongoDB \& Modeling** | `MongoDB, MongoDB Data Modeling, Indexing, Transactions vs. Atomic Updates, Versioning` | Explicitly covers every mandatory MongoDB modeling concept from "What We're Looking For". |
| **Caching \& Analytics** | `Redis, ClickHouse, Update Patterns, Consistency, Scalability, High-Performance Querying` | Covers Redis, ClickHouse, update patterns, consistency, and scalability requirements. |
| **Cloud \& Payments** | `AWS (ECS, SQS, S3, SES), Multi-Currency Payment Systems, Production Deployment` | Covers all four named AWS services, multi-currency payment systems, and production deployment. |
| **Operations \& Quality** | `Monitoring, On-Call Support, Production Debugging, Reliability, Unit & Integration Testing` | Covers lifecycle ownership, monitoring, on-call support, debugging, reliability, and testing rigor. |

---

## 4. Work Experience Bullet Changes

Per Rule 1 (`Java only, no Node.js`) and Rule 1b, replaced `Node.js`, `Express.js`, `React.js`, `Next.js`, `Angular.js`, `TypeScript`, `JavaScript`, `Azure AI Search`, `Jenkins`, and `Docker` references with xPay's mandatory backend stack while preserving every company, title, location, date, bullet count (`4 + 3 + 2 + 1`), and original metric (`50%`, `50%`, `28%`, `90%`, `60%`, `30%`, `40%`):

- **Moresand Technologies (4 bullets):**
  - Bullet 1 (`50%` onboarding): Framed around `Java 21`, `Spring Boot`, `MongoDB`, `system design`, `API design`, `versioning`, and `distributed systems` across 5+ travel brands.
  - Bullet 2: Framed around `MongoDB data modeling`, `indexing`, `REST APIs`, `transactions vs. atomic updates`, `update patterns`, `multi-currency payment systems`, `consistency`, and `scalability`.
  - Bullet 3 (`50%` effort cut & latency): Framed around modular `Spring Boot` services, `REST APIs`, `Redis` caching, `ClickHouse` analytics, and `AWS (SQS, S3, SES)`.
  - Bullet 4: Framed around end-to-end feature lifecycles, `AWS ECS` production `deployment`, `monitoring`, `on-call support`, automated testing, and production `debugging` to eliminate bottlenecks and strengthen `reliability`.
- **MAQ Software (3 bullets):**
  - Bullet 1 (`28%` accuracy): Framed around `Java 21`, `Spring Boot`, `MongoDB`, `Redis`, and `ClickHouse` query orchestration.
  - Bullet 2: Framed around scalable `REST APIs`, `distributed systems`, and `AWS (ECS, SQS, S3)` storage and asynchronous queues.
  - Bullet 3: Framed around product/engineering collaboration, modular `Java` services, strict `versioning`, `MongoDB indexing`, and systematic production `debugging`.
- **Techolution (2 bullets):**
  - Bullet 1 (`90% test coverage`): Framed around `Java 21`, `Spring Boot`, `REST APIs`, unit/integration/automated testing, `reliability`, and `performance`.
  - Bullet 2 (`60%` deployment reduction): Framed around automated production `deployment` on `AWS (ECS, S3, SQS, SES)` for distributed `Java` services with `monitoring` and `on-call support`.
- **GeekForGeeks (1 bullet):**
  - Bullet 1 (`30%` engagement, `40%` performance): Replaced `JavaScript, React.js, and Next.js` with modular `Java` software components, `REST APIs`, and latency-optimized backend data workflows.

---

## 5. Frozen Sections

- **Header** (including exact 9-tilde `Portfolio:~~~~~~~~~` spacing), **Education**, **Projects** (`WebHealth` only, verbatim; `Mobivax` commented out verbatim), and **Achievements** (`HACKIIITV 2019`) copied verbatim from master `resume.tex`.
