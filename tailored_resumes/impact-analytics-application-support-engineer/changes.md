# Resume Changes — Impact Analytics: Application Support Engineer

**Base:** `/resume/resume.tex`
**Tailored:** `resume.tex` (this folder)
**Tailoring Date:** October 29, 2026

---

## Summary of Changes

This tailored resume reframes a full-stack software engineering background for a **Production/Application Support** role. The emphasis shifts from feature development to production reliability, incident ownership, observability, and operational engineering. The base resume leads with Backend skills; this version adds observability, messaging, and Linux/shell to the skills section and rewrites all bullets around production support language.

---

## Skills Summary

| Row | Base | Tailored | Reason |
|-----|------|----------|--------|
| Row 1 | Backend (Java, Node.js, Express.js, Python, REST APIs, GraphQL, Microservices) | **Backend** (Node.js, Express.js, Java, Python, REST APIs, GraphQL, Microservices) | Reordered: Node.js leads (primary language in JD context) |
| Row 2 | Frontend (React.js, Next.js, TypeScript, JavaScript, Redux) | **Databases** (PostgreSQL, MySQL, MongoDB, Redis) | JD requires DB troubleshooting — promoted to row 2; added PostgreSQL |
| Row 3 | Databases (SQL, MySQL, MongoDB, Redis) | **Observability** (Datadog, Grafana, Prometheus, Log Analysis, Distributed Tracing, Alerting) | Added — JD requires monitoring tools; key differentiator |
| Row 4 | Infrastructure (AWS, Docker, Jenkins, CI/CD, Git) | **Infrastructure** (AWS, Docker, Kubernetes, Jenkins, CI/CD, Linux, Shell Scripting) | Added Kubernetes, Linux, Shell Scripting — all in JD requirements |
| Row 5 | Testing (Jest, Unit Testing, Integration Testing, Automated Testing) | **Messaging** (Kafka, RabbitMQ, BullMQ, Queue Monitoring) | Added — JD requires Kafka/RabbitMQ knowledge |
| Row 6 | *(not present)* | **Frontend** (React.js, Next.js, TypeScript, JavaScript) | Demoted — still relevant for full-stack context, but not the focus |

**Net additions to skills:** PostgreSQL, Datadog, Grafana, Prometheus, Log Analysis, Distributed Tracing, Alerting, Kubernetes, Linux, Shell Scripting, Kafka, RabbitMQ, BullMQ, Queue Monitoring

---

## Work Experience — Bullet Changes

### Moresand Technologies (SDE 2)

| # | Change | Reason |
|---|--------|--------|
| 1 | "Owned production reliability of a multi-tenant Node.js/Express.js backend… monitoring API health, triaging failures, coordinating with teams to resolve production incidents" | JD: production support, incident ownership, cross-team coordination |
| 2 | "Built and maintained a Redis-backed caching layer… analysed performance metrics and logs to detect degradation and pre-empt incidents before they reached SLA thresholds" | JD: monitoring, Redis, latency investigation, SLA |
| 3 | "Owned CI/CD pipelines… monitored deployments, validated production readiness, identified post-release regressions, maintained runbooks for deployment rollback and incident triage" | JD: deployment validation, runbooks, CI/CD, operational excellence |
| 4 | "Identified recurring production issues… conducted root cause analysis, filed and tracked fixes, documented resolution patterns to reduce MTTR" | JD: RCA, MTTR, recurring incident analysis |

### MAQ Software (SE 1)

| # | Change | Reason |
|---|--------|--------|
| 1 | "Built and operated a production Node.js backend… owned live incident response for API failures, search errors, and latency spikes" | JD: incident response, L2/L3 support |
| 2 | "Monitored distributed system health across APIs, AI orchestration, and data retrieval — analysed application logs and traces to identify failure patterns" | JD: observability, log analysis, distributed tracing |
| 3 | "Designed backend APIs with structured logging and observability hooks — built internal tools using REST APIs and integrated alerting" | JD: alerting, REST API troubleshooting, observability |

### Techolution (Full Stack Developer)

| # | Change | Reason |
|---|--------|--------|
| 1 | "Built and maintained CI/CD pipelines… validated production deployments, monitored service health post-release" | JD: CI/CD, deployment validation, post-release monitoring |
| 2 | "Established unit, integration, and automated acceptance testing with 90% coverage — ensured production stability and supported incident investigation" | JD: production stability, incident support through test coverage |

### GeekForGeeks (Intern)

| Change | Reason |
|--------|--------|
| "Monitored web vitals, identified rendering bottlenecks, and deployed fixes" | Adds observability/monitoring language even to intern role |

---

## Projects

| Change | Reason |
|--------|--------|
| WebHealth stack updated: "Node.js, Express.js, REST APIs, Google Lighthouse, Web Crawler, GCP, React.js" | Emphasises backend and API health-check orientation |
| Bullet reframed around "automated health checks" and "availability reports" | Directly relevant to monitoring and observability responsibilities |

---

## What Was NOT Changed

- LaTeX preamble, margins, font size, spacing — identical to base `resume.tex`
- Number of bullets per role (4 Moresand, 3 MAQ, 2 Techolution, 1 GFG)
- Education section
- Achievements section (HACKIIITV)
- Personal details, links, contact info
