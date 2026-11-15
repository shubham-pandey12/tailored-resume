# Application Answers — Impact Analytics: Application Support Engineer

**Preparation Date:** October 29, 2026

> Items marked **[CONFIRM]** require your personal input before submission.
> Items marked **[DECISION]** require you to decide before applying.

---

## ⚠️ IMPORTANT — Read Before Applying

**[DECISION]** This role requires **rotational shifts including night shifts, weekends, and holidays** for 24×7 production support. This is a non-negotiable operational requirement. Confirm you are comfortable with this before submitting your application.

---

## 1. Why this role at Impact Analytics?

Impact Analytics operates at real enterprise scale — five continents, 300+ retailers, production systems that cannot fail. That environment means production support is a high-stakes, high-learning engineering function, not a help desk. I want to work on production systems where my troubleshooting and observability work directly reduces downtime for business-critical software. Impact Analytics's agentic-first AI product means the systems I'd be supporting are genuinely novel — not standard CRUD backends.

---

## 2. Describe your production support or incident management experience.

At Moresand Technologies (SDE 2) I own production reliability of a Node.js/Express.js backend serving 5+ luxury travel brands. This includes:
- Monitoring API health and service boundaries
- Triaging failures across distributed services
- Coordinating with engineering and infrastructure teams during active incidents
- Owning the full incident lifecycle: identification → investigation → mitigation → resolution → post-incident documentation
- Identifying recurring issues and filing root cause fixes with engineering

At MAQ Software I built and operated a production Node.js backend for an AI assistant. I was the point of contact for API failures, search degradation, and latency spikes — responsible for log analysis, trace investigation, and cross-team escalation.

---

## 3. Monitoring and observability tools experience.

- **Datadog**: used for APM, log queries, and dashboard monitoring at Moresand (can expand on this in interview)
- **Grafana**: metrics dashboards for latency and error rate monitoring
- **Log analysis**: structured log querying to isolate error patterns across distributed services
- **Alerting**: built custom alerting hooks in Node.js services; tuned alert thresholds to reduce false positives
- **Redis monitoring**: monitored cache hit rates and latency as a health indicator for the caching layer

**[CONFIRM]** — Add any specific tools from your current stack if more accurate (e.g., exact Datadog features, specific Grafana dashboards you own).

---

## 4. Database troubleshooting experience.

- **MySQL**: schema design and query optimisation at Moresand; able to investigate slow queries via EXPLAIN
- **MongoDB**: document design and aggregation queries; used in production across Moresand and Techolution
- **Redis**: caching layer design; TTL management, key eviction monitoring, latency analysis
- **PostgreSQL**: familiar with SQL fundamentals; able to triage query performance issues

---

## 5. Experience with Linux, shell scripting, and CLI-based debugging.

**[CONFIRM]** — Describe your actual Linux/shell comfort level. Suggested: "I work daily on Linux-based servers — SSH access, log tailing (`tail -f`, `journalctl`), process management (`ps`, `top`, `kill`), file system navigation, and basic shell scripting for automation tasks."

---

## 6. Experience with Kafka or messaging/queue systems.

At Moresand Technologies I have worked with **BullMQ** (Redis-based job queues) for async background processing. I understand queue depth monitoring, dead-letter queue patterns, and consumer lag as a health indicator. I am familiar with Kafka concepts (partitions, consumer groups, offset lag) from system design work and prior reading; hands-on Kafka production experience can be developed on the job.

---

## 7. How do you approach RCA (Root Cause Analysis) after a production incident?

1. **Timeline reconstruction**: correlate logs, metrics, and alert timestamps to identify when the failure began vs. when it was detected
2. **Blast radius scoping**: identify which services, users, and data were affected
3. **Hypothesis elimination**: rule out infra changes, deployments, traffic spikes, data anomalies systematically
4. **Fix and verify**: confirm the fix resolves the root cause, not just the symptom
5. **Documentation**: write a clear incident report — what happened, why, what was done, and what prevents recurrence
6. **Follow-up tickets**: file engineering tasks for permanent fixes; don't close the loop at mitigation

---

## 8. Shift work comfort.

**[DECISION]** The role requires rotational shifts including nights, weekends, and holidays. Answer honestly in your application about your availability and comfort with this arrangement.
