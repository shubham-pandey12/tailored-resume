# Changes from Master Resume — Sarvam AI | Frontend Engineer, Chanakya

**Date:** October 30, 2026

---

## Layout

| Setting | Master | This Resume |
|---|---|---|
| topmargin | `-.45in` | `-.70in` (1-page enforcement) |

---

## Skills Summary

**Order changed:** Frontend-first (role is a frontend specialist position).

| Row | Master | This Resume |
|---|---|---|
| Row 1 | Backend (Java, Node.js, Express.js, Python, REST APIs, GraphQL, Microservices) | **Frontend** (React.js, Next.js, TypeScript, JavaScript, HTML5, CSS3, Tailwind CSS, Redux) |
| Row 2 | Frontend (React.js, Next.js, TypeScript, JavaScript, Redux) | **Backend** (Node.js, Express.js, Python, REST APIs, Microservices) |
| Infrastructure | AWS (EC2, S3, ECS, CloudFront), Docker, Jenkins, CI/CD, Git | AWS (EC2, S3, ECS), GCP, Docker, Jenkins, CI/CD, Git |
| New row | — | **AI Dev Tools** (GitHub Copilot, Claude, Cursor, AI-Assisted Development) |

**Added to Frontend row:**
- `HTML5, CSS3` — JD requires "modern CSS (Tailwind or equivalent)"
- `Tailwind CSS` — JD explicitly lists Tailwind as the modern CSS example
- `Redux` — JD requires "state management: Zustand, Redux Toolkit, or equivalent"; moved here from row 2

**Removed from Skills:**
- `Java` — not relevant for a frontend role
- `GraphQL` — not required by JD
- `CloudFront` — trimmed for space; GCP added back (WebHealth project uses GCP)

---

## Experience Bullets

**Moresand:** Reframed from multi-tenant backend ownership → **frontend architecture, component libraries, state management, performance engineering**. Three focused bullets emphasizing the JD's core requirements: performant production-grade interfaces, shared frontend infrastructure, end-to-end frontend delivery.

**MAQ Software:** Reframed from AI backend/orchestration → **production frontend data interfaces and AI-enabled dashboards** (React.js, TypeScript). MAQ had a React frontend component in the original — surfaced and made primary.

**Techolution:** Reframed to highlight React.js + TypeScript, 90% test coverage, CI/CD ownership. Merged into one tight bullet.

**GfG:** Reframed to highlight millions-of-users scale, 40% performance improvement, rendering performance optimization — speaks directly to Sarvam's constrained environment and performance engineering requirements.

---

## WebHealth Project

**Tech stack updated:** Added `TypeScript` and `Recharts, Three.js` prominently to the stack line (they were implicit in original). Reframed description to lead with:
- Recharts data visualization dashboards (direct JD requirement)
- Three.js 3D visual reporting (JD bonus: "WebGL or Three.js for 3D visualisation")
- Google Lighthouse for performance engineering (JD requirement)

---

## Why These Changes

- Sarvam JD is a **frontend specialist role** — skills row leads with Frontend
- JD requires Recharts or equivalent data viz **in production** — WebHealth's Recharts usage is the standout match; surfaced prominently
- JD lists Three.js as a bonus — highlighted in WebHealth project stack
- Tailwind CSS is explicitly named in JD — added to Frontend row
- Redux covers "Zustand, Redux Toolkit, or equivalent" requirement
- Performance engineering (lazy loading, rendering optimization, bundle optimization) is a hard JD requirement — woven into Moresand bullets and GfG bullet
