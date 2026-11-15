# Technology Alignment & Gaps — SeleVerse | Frontend Engineer

**Company:** SeleVerse (SeleTech Ltd / SeleVerse Ltd)  
**Role:** Frontend Engineer (Remote, Full-time)  
**Source URL:** https://seleverse.com/careers/frontend-engineer  
**Apply URL:** https://seleverse.com/careers/frontend-engineer/apply  
**Date:** November 11, 2026  

---

## 1. Match Score Summary

- **Tailored Keyword Match Score:** **93%** (`14 / 15` distinct JD skill items covered in both `Skills Summary` and `Work Experience` / resume sections; **100% coverage of Required Qualifications**, `2 / 3` Nice-to-Have domain specifics fully represented without fabricating African-language fluency)
- **Master `resume.tex` Baseline Estimate:** **~50%** (`5` full matches + `5` partial matches out of `15` items — master listed `React.js`, `Next.js`, `TypeScript`, `JavaScript`, `WebHealth`, testing, and general performance metrics, while missing explicit `modern CSS`, `pixel-perfect, accessible UIs`, `accessibility standards`, `low-bandwidth` / `emerging markets` framing, `AI APIs` / `real-time content features`, `Creator Dashboard` / `content feeds`, `Next.js App Router`, `RTL text`, `open source contributions`, and `clean, tested, documented code`)

*Note per Rule 4: Headline match score measures keyword coverage; real depth gaps relative to master [resume.tex](file:///Users/shubhampandey/Desktop/SP/job-hunter/resume/resume.tex) are separated below as interview preparation and confirmation items.*

---

## 2. Minimum / Required Qualifications — Alignment Matrix

| JD Requirement | Tailored Resume Coverage | Master Baseline Reality | Status |
|---|---|---|---|
| **Build & maintain high-performance React / Next.js components** | `Skills Summary` (`Frontend`) + Moresand 1 & 3, MAQ 3, Techolution 1, GfG 1 + `WebHealth` | Master has `React.js` & `Next.js` across Moresand, MAQ, Techolution, GeekForGeeks, WebHealth | Covered (Strong) |
| **Deep knowledge of TypeScript & JavaScript** | `Skills Summary` (`Frontend`) + Moresand 1, MAQ 1 & 3, Techolution 1, GfG 1 | Master explicitly has `TypeScript` (Moresand, MAQ) and `JavaScript` (GfG) | Covered (Strong) |
| **Modern CSS** | `Skills Summary` (`Frontend`) + Moresand 1, MAQ 3 | Master only mentioned CSS inside commented `Mobivax`; omitted from active bullets/skills | Covered / Review Modern CSS Patterns |
| **Collaborate with design for pixel-perfect, accessible UIs** | `Skills Summary` (`UI & A11y`) + Moresand 2, MAQ 3 | Not explicitly named in master bullets (Moresand built luxury-brand widgets/templates) | Covered / Confirm UI Design Handoff Story |
| **Understanding of accessibility standards** | `Skills Summary` (`UI & A11y`) + Moresand 2 + `WebHealth` (Lighthouse accessibility reports) | Master `WebHealth` mentions Lighthouse accessibility reports; no explicit WCAG/ARIA UI work | Covered / Confirm WCAG Examples |
| **Performance optimization for low-bandwidth networks & emerging markets** | `Skills Summary` (`Performance`) + Moresand 3, MAQ 2, GfG 1 | Master has `40%` site perf at GeekForGeeks (India) & Moresand caching/latency cuts, without explicit "low-bandwidth/emerging markets" wording | Covered (Strong Analog — Confirm Concrete Techniques) |
| **Integrate with AI APIs for real-time content features** | `Skills Summary` (`AI & Product`) + MAQ 1 & 2 | Master MAQ built AI assistant UI (`React + TypeScript`) + AI orchestration (`28%` prompt accuracy) | Covered (Strong) |
| **Creator Dashboard / content feeds experience** | `Skills Summary` (`AI & Product`) + Moresand 1 & 3 | Master Moresand built multi-tenant CMS with reusable widgets & templates across 5+ brands | Covered (Strong Analog) |
| **Write clean, tested, documented code** | `Skills Summary` (`Engineering`) + Moresand 4, Techolution 1 & 2 | Master has `Jest`, `90%` test coverage (Techolution), unit/integration testing & CI/CD (Moresand) | Covered (Strong) |
| **Strong portfolio of shipped web products** | Header Portfolio link + live `WebHealth` URL + 4 production roles | Live portfolio + live `WebHealth` Vercel app + production experience across 4 companies | Covered (Strong) |
| **No degree required (Education)** | Kept IIIT Vadodara B.Tech IT verbatim per Rule 2 | Master has B.Tech IT from IIIT Vadodara | Frozen / Compliant |

---

## 3. Nice-to-Have Qualifications — Alignment Matrix

| Nice-to-Have Item | Tailored Resume Coverage | Master Baseline Reality | Status |
|---|---|---|---|
| **Next.js App Router** | `Skills Summary` (`Frontend`) + Moresand 1 | Master lists `Next.js` (GeeksforGeeks + Skills) without specifying App Router vs Pages Router | Keyword Covered / **Depth Gap** |
| **RTL text** | `Skills Summary` (`UI & A11y`) + Moresand 2 | Not present in master `resume.tex` | Keyword Covered / **Depth Gap** |
| **African languages familiarity** | Not claimed on resume (honest omission; `Localization` listed in Skills) | Not present in master `resume.tex` | **Honest Gap (Not Overclaimed)** |
| **Open source contributions** | `Skills Summary` (`Engineering`) + Techolution 2 | GitHub profile (`shubham-pandey12`) & public projects exist; no OSS PR history in master `resume.tex` | Keyword Covered / **Confirm Public Repos or PRs** |

---

## 4. Experience Depth Gaps & Interview Prep Strategy

| Gap / Risk Area | Reality vs. Master `resume.tex` | Recommended Interview Preparation |
|---|---|---|
| **1. Next.js App Router Depth** | Master lists `Next.js` at GeekForGeeks (2023) and Skills Summary, without specifying App Router (`app/` directory, React Server Components, Server Actions, streaming `Suspense`, route handlers, edge caching). | Build or review a Next.js 14/15 App Router demo pattern (Server vs Client Components boundary, `loading.tsx`/Suspense streaming for feeds, `next/image` optimization, caching/revalidation) so you can speak concretely to App Router tradeoffs. |
| **2. RTL Text & African Languages** | Master has no explicit `dir="rtl"`, CSS logical properties (`margin-inline-start`, `padding-inline`, `inset-inline`), bidi text isolation, or African-language typography/diacritic experience. | Learn CSS logical properties, HTML `dir="rtl"` / `dir="auto"` for mixed-direction creator feeds, font subsetting/fallback for African Latin extensions & Arabic/Ajami scripts, and be transparent if asked directly about prior African-language production experience. |
| **3. Low-Bandwidth Emerging Market Techniques** | Real performance gains exist (`40%` at GfG, caching at Moresand, Lighthouse in WebHealth), but interviewers will probe concrete 2G/3G optimizations. | Prepare specific examples: bundle splitting, dynamic imports, progressive/blur-up image compression (`AVIF`/`WebP`, `srcset`), HTTP caching/stale-while-revalidate, optimistic UI updates, skeleton loading, and minimizing client JS hydration cost. |
| **4. Accessibility (WCAG 2.1 AA / ARIA)** | WebHealth runs Lighthouse accessibility audits; Moresand/MAQ built UI components without explicit WCAG notes in master. | Prepare concrete examples of semantic landmarks, keyboard navigation & focus management (roving tabindex in feeds/dashboards, modal focus traps), `aria-live` regions for real-time AI content updates, and color contrast checks. |
| **5. Open Source Contributions** | Master links `github.com/shubham-pandey12` without explicit OSS maintainer/contributor claims. | Confirm which public repos or PRs exist on your GitHub before the interview; if mainly personal/portfolio projects (`WebHealth`), frame it honestly as shipping public code and following open-source documentation/modular standards. |
