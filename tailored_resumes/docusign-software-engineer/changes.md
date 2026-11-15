# Changes from Master Resume — DocuSign | Software Engineer (Req 30628)

**Prepared:** November 11, 2026  
**Target Company:** Docusign  
**Target Role:** Software Engineer (Storage as a Service)  
**Req ID:** `30628`  

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

Rewrote the 5 `\resumeSubItem` rows to mirror DocuSign's Storage as a Service stack cleanly:

| Category | Tailored Content | Rationale |
|---|---|---|
| **Languages & Core** | `Java (OOP), Scripting, Configuration Platforms, Microservices, Distributed Systems` | Covers OOP (`Java`), scripting/config platforms, microservices, distributed systems. |
| **Cloud & Storage** | `AWS, Azure, GCP, Azure Blob, Google Cloud Storage, Azure Event Hub, GCP Pub/Sub` | Covers Azure/GCP/AWS, cloud object storage, and eventing/messaging platforms. |
| **IaC & Automation** | `Terraform (IaC), CI/CD Pipelines, Cloud Deployment, Infrastructure Automation, Data Platforms` | Covers Terraform IaC, CI/CD, cloud deployment, automation, data platforms. |
| **Reliability & Sec** | `Cloud Security, Security Hardening, Lifecycle Management, Cost Optimization, On-Call` | Covers security hardening, lifecycle management, cost optimization, on-call. |
| **Architecture & QA** | `Cross-Cloud Abstraction Patterns, SaaS, Incident Response, Test Coverage, System Reliability` | Covers cross-cloud abstractions, SaaS, incident response, testing, reliability. |

---

## 4. Work Experience Bullet Changes

Per Rule 1 & Rule 1b (`Java only (no Node.js) -> replace Node.js/JS frontend references with Java` + cloud/IaC stack, no unrequested tech in bullets), updated framing while keeping every company, role, date, location, bullet count (`4 + 3 + 2 + 1`), and original metric (`50%`, `50%`, `28%`, `90%`, `60%`, `30%`, `40%`) intact:

- **Moresand Technologies (4 bullets):** Framed around `Java` `microservices frameworks`, `distributed systems`, multi-tenant `SaaS`, `Product Management` collaboration (`50%` onboarding), `cross-cloud abstraction patterns` across `cloud object storage` (`Azure Blob`, `Google Cloud Storage`, `AWS`) and `data platform` services with `lifecycle management` and `security hardening`, `eventing/messaging platforms` (`Azure Event Hub`, `GCP Pub/Sub`) (`50%` effort cut & latency), and `Terraform` (`IaC`), `cloud security`, `cost optimization`, `test coverage`, `on-call rotations`, and `incident response`.
- **MAQ Software (3 bullets):** Framed around `Java microservices` and `cloud-based data platform` services across `Azure` and `GCP` (`28%` response accuracy improvement), resilient distributed architectures with `Azure Event Hub`, `GCP Pub/Sub`, `Azure Blob`, and `Google Cloud Storage`, and `cross-functional teams` shipping testable `SaaS` modules with `security hardening` and `cost optimization`.
- **Techolution (2 bullets):** Framed around scalable `Java` and `microservices` in cloud `SaaS` (`90% test coverage`), and `cloud deployment`, `configuration tools`, `scripting`, `configuration platforms`, `Terraform (IaC)`, and `CI/CD pipelines` on `AWS` (`60%` faster deployments).
- **GeekForGeeks (1 bullet):** Kept `30%` engagement and `40%` performance metrics while removing unrequested frontend framework names (`React`/`Next.js`) in favor of `testable software components` and `automation scripts`.

---

## 5. Frozen Sections

- **Header** (including 9-tilde `Portfolio` spacing), **Education**, **Projects** (`WebHealth` only, verbatim; `Mobivax` commented out verbatim), and **Achievements** (`HACKIIITV 2019`) copied verbatim from master `resume.tex`.

