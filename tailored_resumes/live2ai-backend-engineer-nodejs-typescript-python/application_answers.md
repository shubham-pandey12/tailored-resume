# Application Answers — Live2.ai | Backend Engineer (NodeJS/TypeScript/Python)

**Source URL:** https://jobs.clanx.ai/o/backend-engineer-nodejstypescriptpython-bengaluru/c/new  
**Prepared Date:** November 12, 2026  

## Standard & Screening Fields (Review/Adjust Before Submitting)
- **Full name:** `Shubham Pandey` · **Email:** `mr.pshubham@gmail.com` · **Phone:** `+91 8174081896`
- **CV:** `ShubhamPandeyResume.pdf`
- **Years of experience (Backend Engineer):** `3 - 4 years`
- **Relocate to Bengaluru:** `Yes`
- **Notice period:** `15 - 30 days` *(Assumed default — verify)* · **Negotiable:** `Yes`
- **Product-based company experience?** `Yes` · **Citizen of India & based in India?** `Yes`
- **What does current company mainly do?** `Builds technology or products mainly for its own customers or business`
- **Product/services of current company:**
  > Moresand Technologies is the engineering hub for Moresand Group (https://moresandtechnologies.com/ / https://www.moresand.co.uk/), building proprietary consumer travel platforms (such as Luxtripper and Crystal Travel) as well as B2B wholesale booking and travel ERP systems (Air Travel Guide and Penguin Travel Technology). Travelers, corporate clients, and partner travel agencies use these platforms to search, customize, and book multi-supplier flights, hotels, and bespoke holiday packages globally.
- **Current CTC range:** `15 - 20 Lakh` *(Assumed placeholder — update)*
- **Current CTC breakup:** `Fixed: 16L, Variable: 2L, ESOPs: 0` *(Assumed placeholder — update)*
- **Expected annual CTC (INR):** `2400000` *(Assumed placeholder — update)*
- **LinkedIn:** `https://www.linkedin.com/in/shubham-pandey-a74716199/`
- **Mandatory Loom Video:** `[PASTE YOUR LOOM VIDEO LINK HERE]`
  - *Suggested talking points:* Walk through Moresand's multi-tenant backend platform (Node.js/TypeScript/SQL/Redis, tenant-scoped data models & API versioning across 5+ brands, 50% faster onboarding, post-launch latency/CI/CD ownership).
- **Async / Queue Workflow Failure & Recovery Answer:**
  > While building data-ingestion and AI retrieval/integration workflows across Moresand Technologies and MAQ Software, a partial failure mid-pipeline (e.g., an external API timeout or rate-limit after initial records were written) risked leaving downstream state out of sync with cached/indexed records. To prevent inconsistent state and duplicate side effects, I decoupled ingestion from processing using idempotency keys per request/tenant, transactional state transitions (pending -> processing -> completed/failed) before dispatching downstream updates, and bounded retries with exponential backoff and dead-letter handling for persistent failures. When a third-party endpoint intermittently returned 504s mid-batch during rollout, only the failed items were retried without duplicating already-committed entries, which we verified through integration failure-injection tests and cache/DB consistency checks.
- **Live2.ai Company Research & Product/Backend Fit:**
  > Live2.ai is building an AI-native Social Content & Campaign Intelligence OS for Fortune 500 consumer brands—monitoring brand conversations and UGC across platforms like Instagram, TikTok, YouTube, and Reddit, running specialized AI agents (for campaign auditing, compliance, crisis detection, and trend scouting), and turning cleared social/influencer content into shoppable commerce experiences. Its key backend challenges are ingesting and normalizing high-volume, rate-limited social streams asynchronously, enforcing strict multi-tenant data isolation across competing enterprise brands, and versioning APIs safely for enterprise customers whose systems evolve independently. At Moresand Technologies, I architected a multi-tenant platform across 5+ brands with strict schema boundaries, API versioning, and Redis caching (cutting onboarding time by 50%), and at MAQ Software I owned a production Node.js AI orchestration backend that improved prompt accuracy by 28%—directly preparing me to own Live2.ai's multi-tenant models, async queues, and enterprise APIs.
- **Why do you want to leave your current role?**
  > At Moresand Technologies, I've already designed and shipped the core multi-tenant architecture across 5+ brands. I want to take on an IC backend ownership role at an AI-native enterprise SaaS company like Live2.ai where multi-tenant data isolation, async queue reliability, and API versioning operate at Fortune 500 scale.
- **Where did you find this job opportunity?** `Job board (NA)` *(Update if referred)*

