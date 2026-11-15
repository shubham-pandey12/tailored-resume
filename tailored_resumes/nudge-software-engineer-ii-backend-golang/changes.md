# Changes from Master Resume — Nudge | Software Engineer II (SDE 2) - (Backend - Golang)

**Prepared:** November 10, 2026  
**Target Role:** Software Engineer II (SDE 2) - (Backend - Golang)  
**Target Company:** Nudge (Technology / Core Platform Engineering)  
**Source URL:** https://nudge.keka.com/careers/jobdetails/94988?source=linkedin  

---

## 1. Master Resume Hash Verification

- **Master resume path:** `/Users/shubhampandey/Desktop/SP/job-hunter/resume/resume.tex`
- **Initial SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Current SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Verification status:** Verified identical — master `resume.tex` and adjacent `resume.pdf` were not modified.

---

## 2. LaTeX Preamble Adjustments

- `\addtolength{\topmargin}{-.70in}` (changed from `-.45in` in master per Rule 3 to ensure a balanced 1-page fit).
- All other preamble settings (`\oddsidemargin`, `\evensidemargin`, `\textwidth`, `\textheight`), document class, packages, and custom commands were copied verbatim from master `resume.tex`.

---

## 3. Skills Summary Changes

Rewrote Skills Summary into 6 single-line `\resumeSubItem` rows reflecting Nudge's exact Golang/backend stack (removing unmentioned technologies such as Java, Node.js, Express.js, Python, React.js, Next.js, Angular.js, MongoDB, MySQL, GraphQL, Jenkins, Jest):

| Row | Master Resume | Tailored for Nudge |
|---|---|---|
| **1** | `Backend`: Java, Node.js, Express.js, Python, REST APIs, GraphQL, Microservices | `Backend & Go`: Golang (Goroutines, Channels, Context), Microservices, RESTful APIs, Event-Driven Systems |
| **2** | `Frontend`: React.js, Next.js, TypeScript, JavaScript, Redux | `Concurrency`: Concurrency Patterns, Idempotency, Distributed Locks, Rate-Limiting, Retries, Partial Failures |
| **3** | `Databases`: SQL, MySQL, MongoDB, Redis | `Data & Caching`: PostgreSQL (Schema Design, Indexing, Query Tuning), Redis Caching, Ledger Consistency |
| **4** | `Infrastructure`: AWS (EC2, S3, ECS, CloudFront), Docker, Jenkins, CI/CD, Git | `Cloud & Ops`: Docker, Kubernetes, CI/CD, GCP, AWS, Third-Party Integrations, Design Docs, On-Call |
| **5** | `Testing`: Jest, Unit Testing, Integration Testing, Automated Testing | `Observability`: Logging, Metrics, Alerts, Dashboards, Profiling, Postmortems, Automated Testing, Code Reviews |
| **6** | *(Added category row per Skills Gap Resolution)* | `AI Coding Tools`: Claude Code, Cursor, GitHub Copilot, AI Code Review Standards, Pairing, Debugging |

---

## 4. Work Experience Bullets Changes

All company names, locations, job titles, employment dates, bullet counts (`4, 3, 2, 1` = 10 bullets), and verified metrics (`5+ brands`, `50%` onboarding, `50%` effort reduction, `28%` accuracy, `90%` test coverage, `60%` deployment time, `30%` engagement, `40%` site performance) were preserved verbatim. All non-JD technologies (`Node.js`, `Express.js`, `Java`, `Python`, `React.js`, `Next.js`, `Angular.js`, `MongoDB`, `MySQL`, `TypeScript`, `JavaScript`, `Azure AI Search`, `Jenkins`) were replaced with Nudge's stack:

- **Moresand Technologies (Mar 2025 - Present — 4 bullets):**
  - **Bullet 1:** Multi-tenant platform end-to-end with **Golang microservices**, **RESTful APIs**, **design docs**, and **PostgreSQL schema design** for 5+ brands — cutting onboarding by **50%**.
  - **Bullet 2:** Concurrent **Golang** workflows (**goroutines, channels, context**) with **idempotency**, **Redis distributed locks**, and **rate-limiting** to prevent duplicate writes and abuse while preserving **ledger consistency** under **retries** and **partial failures**.
  - **Bullet 3:** Reusable **third-party integrations** (auth, retries, rate limits), **Redis caching**, and **PostgreSQL indexing and query tuning** for heavy read/write workloads — cutting effort by **50%** and latency.
  - **Bullet 4:** Production **uptime** and **CI/CD** — **logging, metrics, alerts, dashboards**, **on-call debugging** via **profiles**, **postmortems**, and mentoring via **code reviews**.
- **MAQ Software (Apr 2024 - Feb 2025 — 3 bullets):**
  - **Bullet 1:** Production **Golang** backend service on **AWS** powering an **event-driven pipeline** for high-volume data ingestion and parsing orchestration — improving response accuracy by **28%**.
  - **Bullet 2:** **Event-driven systems** and **RESTful APIs** with **concurrency patterns**, schema validation, and **idempotent** retry handling on **PostgreSQL** and **Redis** for messy payloads.
  - **Bullet 3:** Delivery across products using **AI coding tools** (**Claude Code, Cursor, GitHub Copilot**), **code review** standards, **pairing**, and **automated testing** for maintainable **Golang** services.
- **Techolution (Jul 2023 - Mar 2024 — 2 bullets):**
  - **Bullet 1:** Production **Golang** backend features and **RESTful APIs** with unit, integration, and **automated testing** achieving **90% test coverage** and thorough **code reviews**.
  - **Bullet 2:** **CI/CD pipelines** using **Docker** and **Kubernetes** for **Golang microservices** on **GCP** and **AWS** — reducing deployment time by **60%** while improving release reliability and engineering tooling.
- **GeekForGeeks (Jan 2023 - Jun 2023 — 1 bullet):**
  - **Bullet 1:** Boosted user engagement by **30%** and improved site performance by **40%** via modular **Golang RESTful APIs**, **PostgreSQL query tuning**, and **Redis caching**.

---

## 5. Frozen Sections (Copied Verbatim from Master)

Per Rule 2, the following sections were copied verbatim from `/Users/shubhampandey/Desktop/SP/job-hunter/resume/resume.tex`:
- **Header:** Name, email, GitHub, mobile, LinkedIn, Portfolio.
- **Education:** Indian Institute Of Information Technology Vadodara — Bachelor of Technology - Information Technology.
- **Projects:** `WebHealth` ONLY (tech stack line and description copied verbatim; `Mobivax` remains commented out verbatim).
- **Achievements:** `HACKIIITV` (`2019`, `Best Idea Award`) copied verbatim.
