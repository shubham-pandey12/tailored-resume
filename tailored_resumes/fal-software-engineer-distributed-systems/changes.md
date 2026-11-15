# Changes from Master Resume — fal | Software Engineer, Distributed Systems

**Prepared Date:** November 12, 2026  
**Target Company:** fal (`fal.ai`)  
**Target Role:** Software Engineer, Distributed Systems  
**Source URL:** https://www.workinslippers.com/jobs/fal-software-engineer-distributed-systems-mw30iptn  
**ATS URL:** https://jobs.ashbyhq.com/fal-ai/0acf2909-a4c4-4ad5-a0fb-61fba66eb89e/application?utm_source=workinslippers  

---

## 1. Master Resume Integrity Verification

- **Master resume path:** `/Users/shubhampandey/Desktop/SP/job-hunter/resume/resume.tex`
- **Initial SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Final SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Status:** Identical. Master `resume.tex` was never modified or overwritten.

---

## 2. LaTeX Preamble & Build Verification

- Updated `\addtolength{\topmargin}{-.45in}` to `\addtolength{\topmargin}{-.70in}` per `prompt.md` Rule 3.
- Preserved `\addtolength{\oddsidemargin}{-0.530in}`, `\addtolength{\evensidemargin}{-0.375in}`, `\addtolength{\textwidth}{1in}`, `\addtolength{\textheight}{1.15in}`, fonts, and custom macros verbatim from master.
- Compiled in isolated `/tmp/fal-ds-build/` using `/opt/homebrew/bin/tectonic -X compile` (`ShubhamPandeyResume.pdf`: `kMDItemNumberOfPages = 1`; `ShubhamPandeyCoverLetter.pdf`: `kMDItemNumberOfPages = 1`). No `.aux`/`.log` build artifacts left inside the folder.

---

## 3. Skills Summary Modifications

Replaced the 5 generic web/full-stack rows (`Backend`, `Frontend`, `Databases`, `Infrastructure`, `Testing`) with 5 `fal`-aligned distributed systems & GPU infrastructure rows:

| Row | Tailored Content | JD Coverage Mapped |
|---|---|---|
| **Core & Langs** | `Rust, Python, Async Runtimes, Zero-Copy, Memory-Safe Concurrency, Distributed Coordination` | Primary languages and high-performance distributed/concurrent systems fundamentals. |
| **AI & Compute** | `AI Inference & Training Infra, Multi-Tenant Compute, GPU Workload Scheduling, Worker Orchestration` | Core AI inference/training platform, multi-tenant compute, scheduling, and worker orchestration. |
| **Scaling & Fleet** | `Request Routing & Queuing, Autoscaling, App Deployment, Placement, Capacity Management, Fault Tolerance, Lifecycle Automation` | Global routing/queuing, autoscaling, deployment, placement, capacity, resilience, and GPU fleet lifecycle automation. |
| **Storage & Linux** | `Linux Systems, JuiceFS, Lustre, Global Storage & Caching, Containerization, RAM/VRAM Snapshotting, Kernel/Driver Debugging, Config Management` | Linux fleet engineering, distributed filesystems, global storage/caching, containers, VRAM snapshotting, kernel/driver debugging, config management. |
| **Net, GPU & Ops** | `BGP, ECMP, eBPF, Geneve, Tunnels, ACLs/Firewalls, Nvidia/AMD GPU, DCGM, NVLink, RDMA, InfiniBand/RoCEv2, Observability, AI Ops` | Global L3/L4 networking, GPU telemetry/fabric stack, observability, and AI-accelerated ops automation. |

---

## 4. Work Experience Bullet Modifications

Preserved every employer, location, job title, employment date range, bullet count (`4, 3, 2, 1`), and original numeric metric (`5+`, `50%`, `50%`, `28%`, `90%`, `60%`, `30%`, `40%`), while replacing unmentioned web/app technologies (`Node.js`, `Express.js`, `React.js`, `TypeScript`, `Angular.js`, `Next.js`, `JavaScript`, `Redis`, `Azure AI Search`, `Docker`, `Jenkins`) with `fal`'s exact JD vocabulary per Rule 1 & Rule 1b:

- **Moresand Technologies (`Mar 2025 - Present`, 4 bullets):**
  - Bullet 1 (`5+`, `50%`): Framed around architecting a `multi-tenant compute platform` (`Rust, Python`, `async runtimes`, `distributed coordination`, `containerization`) across `5+ clusters` with `placement` and `fault tolerance`, cutting onboarding `50%`.
  - Bullet 2: Framed around designing `global IP backbone` and datacenter `private networking`, `elastic public IPs`, `ACLs/firewalls`, `BGP`, `ECMP`, `tunnels`, `eBPF`, and `Geneve` for `private connectivity`.
  - Bullet 3 (`50%`): Framed around `request routing`, `queuing`, and `global file storage, caching, and distribution` across `JuiceFS` and `Lustre` with `zero-copy` I/O, cutting effort `50%` and accelerating `app deployment`.
  - Bullet 4: Framed around `observability`, `alerting`, and `GPU fleet lifecycle automation` (`Nvidia/AMD GPU`), `provisioning`, `DCGM`, `NVLink`, `RDMA`, `InfiniBand/RoCEv2` `diagnostics`, `safe upgrades`, and `recovery`.
- **MAQ Software (`Apr 2024 - Feb 2025`, 3 bullets):**
  - Bullet 1 (`28%`): Preserved `Python` and `28%` accuracy gain; framed around `Python/Rust AI inference` and `training infrastructure` utilizing `AI ops automation` for `alerting` and `recovery`.
  - Bullet 2: Framed around `worker orchestration`, `GPU workload scheduling`, `memory-safe concurrency`, `RAM/VRAM snapshotting`, and `async runtimes` under shifting capacity.
  - Bullet 3: Framed around reusable `GPU fleet autoscaling`, `capacity management`, and `tracking` in `Rust` for `multi-tenant compute` and global `workload placement`.
- **Techolution (`Jul 2023 - Mar 2024`, 2 bullets):**
  - Bullet 1 (`90%`): Framed around `Rust and Python` `distributed coordination`, `Linux configuration management`, `diagnostics`, and `90% test coverage`.
  - Bullet 2 (`60%`): Framed around `fleet automation`, `app deployment`, `containerization`, `observability`, `alerting`, and `safe upgrades`, cutting rollout time by `60%`.
- **GeekForGeeks (`Jan 2023 - Jun 2023`, 1 bullet):**
  - Bullet 1 (`30%`, `40%`): Preserved `30%` and `40%` metrics; framed around `Linux kernel and driver` debugging and `Python/Rust` `globally distributed filesystem` `caching`.

---

## 5. Frozen Sections Verified Unchanged

- **Header:** Copied verbatim from master `resume.tex` (with exact 9-tilde spacing before `Portfolio:`).
- **Education:** Copied verbatim (`Indian Institute Of Information Technology Vadodara`, `Bachelor of Technology - Information Technology;`).
- **Projects:** Copied verbatim (`WebHealth` only, unchanged tech line & description; commented `Mobivax` block preserved untouched).
- **Achievements:** Copied verbatim (`HACKIIITV`, `2019`, `Best Idea Award`, `team of 5`).

