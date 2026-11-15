# Application Answers — Fynd Python Developer SDE 2

**Role:** Python Developer | SDE 2 | JCP — Fynd
**Date:** October 29, 2026

---

## Standard Application Questions

### 1. Years of professional software development experience?
**Answer:** 3 years 9 months (July 2023 – present, including internship from January 2023).

**[CONFIRM]** JD requires 4–8 years. Actual tenure is ~3.7 years full-time. Round to "nearly 4 years" if asked, and emphasize breadth of ownership (SDE 2 title, architecture decisions, CI/CD ownership) rather than raw tenure. Do not misrepresent.

---

### 2. Years of Python backend development experience?
**Answer:** Python has been used throughout my backend work — for scripting, data pipelines, API services, and AI orchestration backends. I am comfortable answering "2+ years of hands-on Python" in production contexts.

**[CONFIRM]** If the form asks for a number, use 2. Be ready to discuss specific Python use cases in interview.

---

### 3. Do you have experience with Flask or Django?
**Answer:** Yes. I have built production Flask-based REST APIs for an AI assistant backend at MAQ Software, and have applied Django ORM patterns for structured data retrieval workflows.

**[CONFIRM]** Flask is stronger claim; Django is supplementary. Be ready to discuss both in interview.

---

### 4. Do you have experience building RESTful APIs?
**Answer:** Yes — extensively. I have designed and built RESTful APIs at every role: multi-tenant APIs at Moresand, AI retrieval APIs at MAQ Software, and full-stack APIs at Techolution.

---

### 5. Current CTC / Expected CTC?
**[CONFIRM]** Fill in based on current offer/expectation. Do not leave blank; negotiate after shortlist.

---

### 6. Notice period?
**[CONFIRM]** Confirm actual notice period at Moresand Technologies.

---

### 7. Are you open to relocating to Mumbai?
**[CONFIRM]** Confirm willingness. Mumbai relocation may be required for on-site work at Fynd HQ.

---

### 8. Why Fynd?
**Answer:** Fynd operates at a scale and in domains — retail tech, generative media, physical AI — where backend systems face genuinely hard reliability and performance problems. I want to work on systems where the engineering choices have direct business impact at millions of users, and where the company is still moving fast enough to give engineers real ownership.

---

### 9. Describe a time you optimized a high-traffic backend system.
**Answer:** At Moresand, high-traffic endpoints for multiple luxury travel brands were hitting latency issues under concurrent load. I introduced a Redis-backed caching layer with TTL-based invalidation tied to content update events, reducing API response latency measurably and enabling the platform to scale across new brands without proportional infrastructure cost.

---

### 10. How do you approach code reviews?
**Answer:** I treat code review as a design conversation, not a gatekeeping step. I focus on: correctness (does it do what it claims?), maintainability (will the next engineer understand this?), and surface area (is this change scoped appropriately?). I give specific, actionable feedback and prefer suggesting alternatives over blocking without a path forward.

---

## Notes for Gaps

- **Experience gap (4–8 years required, ~3.7 actual):** Lead with ownership depth and SDE 2 title. Emphasize that the work done — architecture decisions, CI/CD ownership, multi-tenant system design — reflects senior-level responsibility, not tenure alone.
- **Django:** Honest claim is familiarity and ORM-level usage. If Fynd's stack is primarily Django, study Django-specific patterns (class-based views, middleware, signals, Celery integration) before interview.
- **Scale:** Fynd processes far more traffic than Moresand. Be ready to discuss how you would approach designing for 10x or 100x current scale.
