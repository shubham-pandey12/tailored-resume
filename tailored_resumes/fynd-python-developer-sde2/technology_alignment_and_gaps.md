# Technology Alignment and Gaps — Fynd Python Developer SDE 2

**Role:** Python Developer | SDE 2 | JCP — Fynd
**Date:** October 29, 2026

---

## Alignment Matrix

| JD Requirement | Strength | Evidence |
|---|---|---|
| Python | ✅ Strong | In Skills Summary (lead position); in Moresand bullets 1, 2, 3; MAQ bullets 1, 2 |
| REST APIs | ✅ Strong | Core of every role; Moresand (multi-tenant APIs), MAQ (AI retrieval APIs), WebHealth project |
| Flask | ✅ Present | MAQ bullet 1 (Python/Flask backend service); Moresand bullet 3 (Flask-style REST APIs) |
| Django | ⚠️ Supplementary | MAQ bullet 2 (Django ORM-style patterns); Skills Summary. Honest claim: ORM-level familiarity, not full Django app development |
| FastAPI | ✅ Skills | Listed in Skills Summary; interview prep needed if Fynd uses FastAPI specifically |
| Microservices | ✅ Strong | Moresand (service boundaries), Techolution (CI/CD for microservices), Skills Summary |
| Redis / Caching | ✅ Strong | Moresand bullet 3 (Redis-backed caching layer for high-traffic endpoints) |
| PostgreSQL / SQL | ✅ Present | PostgreSQL in Skills Summary; MySQL experience; Moresand schema design |
| CI/CD | ✅ Strong | Moresand bullet 4 (owned CI/CD), Techolution bullet 2 (Jenkins/Docker, 60% deployment time reduction) |
| Automated Testing | ✅ Strong | Techolution (90% test coverage), Moresand (test strategy ownership) |
| Cloud (AWS/GCP) | ✅ Present | AWS (EC2, S3, ECS, CloudFront) in Skills Summary; GCP in WebHealth project |
| Docker | ✅ Strong | Techolution bullet 2; Skills Summary |
| Scalable backend systems | ✅ Present | Multi-tenant platform (5+ brands), Redis caching, API latency reduction |
| Cross-functional collaboration | ✅ Strong | Moresand (data contract between backend and frontend), MAQ (AI + product teams) |

---

## Honest Gaps

| Gap | Detail | Mitigation |
|---|---|---|
| **Years of experience** | JD requires 4–8 years; actual is ~3.7 years (Jul 2023 – Oct 2026 including internship) | SDE 2 title, architecture ownership, CI/CD ownership demonstrate senior-level responsibility beyond raw tenure |
| **Django depth** | Claim is ORM-level familiarity, not full Django app development (views, middleware, signals, Celery) | Study Django-specific patterns before interview; honest framing in application |
| **Fynd-scale traffic** | Fynd processes millions of retail transactions; largest system at Moresand serves 5+ brands | Emphasize Redis caching design, API latency work, and multi-tenant architecture as evidence of scalability thinking |
| **Manufacturing / Physical AI domain** | No domain experience in Fynd's newer verticals | Transferable: backend reliability, API design, and service architecture principles are domain-agnostic |

---

## Match Score

**Overall: 78/100**

- Core Python backend: 80/100 (strong claim, some Django depth gap)
- API design: 95/100 (extensive, multi-context)
- CI/CD and testing: 90/100 (owned in two roles)
- Scalability / performance: 75/100 (Redis caching strong; Fynd-scale gap)
- Years of experience: 60/100 (3.7 vs 4–8 required — most significant gap)
- Cloud and infrastructure: 80/100 (AWS strong, GCP present)

---

## Pre-Interview Study List

1. Django: class-based views, middleware, signals, Django REST Framework, Celery
2. Flask: blueprints, application factory pattern, Flask-SQLAlchemy, Flask-Migrate
3. Python performance: async/await, threading vs multiprocessing, profiling tools
4. Fynd engineering blog / tech stack (search for Fynd engineering Medium or blog)
5. PostgreSQL: indexing strategies, query optimization, connection pooling
6. System design: design a high-traffic product catalog API (Fynd's core use case)
