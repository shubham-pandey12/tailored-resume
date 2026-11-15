# Application Answers — PhonePe | Product Solution Engineer

**Preparation Date:** October 29, 2026

---

## Why PhonePe?

PhonePe operates at a scale few companies in India reach — 70 Crore registered users and 5 Crore+ merchants. Every production decision I make here would have direct, visible impact on millions of people's daily financial transactions. I want to work on systems where reliability and observability genuinely matter, not just as good engineering hygiene but as a product promise. PhonePe's culture of ownership from day one and speed of execution resonates with how I already work.

---

## Why this role (Product Solution Engineer)?

I've spent the last 3+ years in environments where I'm responsible for both building and keeping systems stable in production. I've written Python and Shell/Bash automation scripts to eliminate manual operational tasks, built monitoring solutions for high-traffic endpoints, maintained MySQL-backed data layers, and kept incident resolution logs as part of on-call practices. This role formalises that blend of engineering and operational ownership — and the cross-functional aspect of feeding user issues back to product teams is something I've done at both Moresand and MAQ Software.

---

## Describe a production incident you diagnosed and resolved

At Moresand Technologies, we saw intermittent latency spikes on high-traffic REST API endpoints serving luxury travel brand data. I diagnosed the issue as N+1 query patterns in the MySQL data layer — complex joins were being executed per-record rather than batched. I rewrote the affected queries, added a Redis-backed caching layer for read-heavy endpoints, and deployed Shell/Bash scripts to automate cache warming on deployment. Latency dropped significantly, and I added monitoring scripts to alert on query execution time regressions going forward.

*[Candidate should confirm exact latency figures and timeline from memory before the interview.]*

---

## Describe an automation you built that replaced a manual process

At MAQ Software, the data retrieval pipeline for an AI assistant was partly manual — engineers were running Python scripts by hand and checking outputs before feeding them to the AI orchestration layer. I automated the full pipeline: wrote Python scripts that pulled data, applied transformation logic, ran validation checks, and fed results directly into the orchestration layer without human intervention. This eliminated a 30–45 minute daily manual workflow and reduced error rates in the data layer.

*[Candidate should confirm exact time savings figures from memory before the interview.]*

---

## Scripting experience (Python / Shell)

- **Python:** Used at MAQ Software for AI orchestration automation and data pipeline scripting; reinforced at Moresand for monitoring and deployment automation scripts.
- **Shell/Bash:** Used at Moresand and Techolution to automate CI/CD pipeline steps, deployment sequences, and environment setup tasks. Jenkins pipeline scripts at both companies.
- **Perl:** Not current production experience — listed in JD as "strong plus" not required. Candidate should flag this honestly and note Perl/Shell scripting patterns are closely related.

---

## Database / SQL experience

- Designed MySQL and PostgreSQL schemas from scratch at Moresand Technologies.
- Wrote complex SQL joins for brand-specific data integration across internal systems.
- Worked with MySQL at WebHealth project (personal project) for audit data storage.
- Redis for caching layer design.

---

## How do you handle cross-functional communication about production issues?

At Moresand, I own the communication between engineering and the business teams when production issues arise. My practice: (1) acknowledge with timeline when first detected, (2) share root cause in plain language — not technical jargon — with estimated fix time, (3) provide a post-incident summary with what changed and how recurrence is prevented. At MAQ Software, I translated AI model performance issues into actionable product feedback for the PM team, including specific edge cases and suggested UX guard-rails.

---

## Experience depth / gap notes requiring confirmation

- **Perl scripting:** No production Perl experience; Shell/Bash and Python are strong. Candidate should confirm whether to disclose proactively or wait for interview.
- **C++/Java/RubyOnRails bonus:** Java listed in Skills Summary from master resume. Candidate should confirm Java experience depth before technical screen.
- **On-call tracking systems:** Informal practice (incident logs, resolution records) at Moresand and MAQ. No formal PagerDuty/OpsGenie experience — confirm before interview.
- **Salary / notice period / work authorisation:** Not assumed — confirm before applying.
