# Application Answers — Apple | Senior UI Engineer - Web

**Prepared:** October 30, 2026

---

## Application Form

Apple Careers (jobs.apple.com) — submit resume, contact info, work authorization.

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Describe a high-performance web application you architected — how did you approach component architecture and design systems?**

At Moresand, I architected the frontend of a multi-tenant SaaS platform from scratch — the design constraint was that a single codebase had to serve 5+ distinct enterprise clients with different branding, data models, and feature sets. The solution was a design token system: every visual decision (typography, color, spacing) was abstracted to CSS custom properties, and a configuration layer swapped token values per client at build time. On top of that, I built a component library with a strict contract — each component accepted only typed props, had no internal styling opinion, and was composed rather than overridden. The result: adding a new client required zero new component code, only a new token config. Performance was a first-class constraint from day one: I set performance budgets per route (bundle size ceilings, LCP targets), used code splitting and lazy loading at the route boundary, and monitored production with custom RUM metrics. When a rendering regression appeared post-deploy, structured logs pinpointed it within an hour.

**2. How do you measure and optimize Core Web Vitals in production?**

My discipline on this comes directly from the WebHealth project — I built a system that runs Google Lighthouse programmatically and reports LCP, INP, CLS, FCP, and TTFB per URL into a dashboard. Building the tooling yourself forces you to understand exactly what each metric measures and what degrades it. In production: I instrument Real User Monitoring (RUM) to capture field CWV data, not just lab data, because Lighthouse lab results and real user results diverge for dynamic content. For LCP: I trace what the browser is actually painting first — usually a hero image or a large text block — and optimize the critical path: preloading the resource, eliminating render-blocking scripts, inlining critical CSS. For CLS: I set explicit width/height on every image and avoid late-loading layout-shifting ads or banners. For INP: I move heavy synchronous work off the main thread with `requestIdleCallback` or Web Workers for non-visual computation. I enforce all of this in CI with a Lighthouse CI budget configuration that fails builds on regressions.

**3. Tell me about your experience integrating LLM/AI APIs into a frontend application — what did you build and how did it work?**

At MAQ Software, I built the frontend for an enterprise AI assistant. The engineering challenge was not simply calling an LLM endpoint — it was making the UX feel responsive and reliable while the model was generating. The design choices: I used streaming responses (the API sent tokens as they were generated) and built a progressive rendering layer that updated the UI incrementally as each chunk arrived, rather than waiting for the full response. This made the interaction feel immediate rather than showing a spinner for several seconds. The retrieval backend (Azure AI Search) returned structured context to the frontend before the LLM call — I used that to render source citations and confidence indicators alongside the generated answer, so users could verify the AI's reasoning. I also built error boundary handling for the AI layer specifically: LLM calls have higher latency variance and failure rates than ordinary REST calls, so I designed graceful degradation — if the LLM call failed, the UI showed the retrieved context alone rather than a generic error message.

**4. How do you approach building accessible, cross-browser compatible interfaces?**

Accessibility is a constraint I apply at the design phase, not a checklist I run at the end. At Moresand, I established accessibility standards in the component contract: every interactive element in the design system had required ARIA attributes defined in its TypeScript props, keyboard event handlers alongside click handlers, and focus management on dynamic content changes. I also owned the accessibility audit process — I ran axe-core in CI on every PR, so regressions surfaced in code review, not in a quarterly audit. For cross-browser compatibility: I define a browser support matrix at project start (typically last 2 stable versions of Chrome, Firefox, Safari, and Edge), use `@supports` feature queries for progressive enhancement, and test critical flows in Safari specifically because WebKit diverges most from Chromium on CSS grid and custom properties behavior. I treat Internet Explorer as dead and never write IE-specific workarounds; when a client requirement changes that, I escalate the engineering cost explicitly.

**5. Describe your approach to building reusable component libraries and design systems.**

A component library is a product with its own API surface, not a collection of files. I approach it with the same discipline as a backend API: the public interface (props) is versioned and stable; breaking changes require a major version bump; every component has a documented contract. At Moresand, I built the component library before any application feature code — I established: (1) a token layer (CSS custom properties for every design decision, never hardcoded values), (2) a primitive layer (Button, Input, Typography — layout-agnostic, fully accessible, zero visual opinion), and (3) a composition layer (forms, cards, data tables — assembled from primitives, accepting tokens). This separation meant that restyling for a new client required only a new token config, not touching component code. I colocated unit tests with every component (Jest + Testing Library), wrote tests against behavior not implementation, and tracked bundle size per component so that importing one button never pulled in the whole library.

**6. How do you use AI-assisted development tools in your workflow?**

My approach is: AI accelerates the tedious and amplifies the careful. I use Claude and GitHub Copilot daily. For code generation: I use them for boilerplate (test stubs, type definitions, repetitive transformations), not for logic I don't understand — I always read and verify AI-generated code before committing, especially for anything security-adjacent (auth flows, input validation, data access). For debugging: I use AI to synthesize large log outputs and error traces into a prioritized hypothesis list, then verify each hypothesis myself. For architecture: I use AI to pressure-test a design decision — I describe my approach and ask it to argue against it, which surfaces blind spots faster than solo thinking. I never commit AI-generated code I haven't read and understood line by line. The productivity gain is real; the engineering judgment has to stay human.

**7. Why Apple IS&T specifically — what draws you to the Retail and Marcom Engineering team?**

IS&T operates at a scale most engineers never touch — 2.5 billion active devices, billions of transactions, the technology behind every Apple purchase. The constraint that makes this interesting is not just scale in the abstract; it is the combination of scale with Apple's design standards. The Retail and Marcom Engineering team has to build systems that are simultaneously enterprise-grade reliable and consumer-grade beautiful — that is a rare and genuinely hard engineering problem. I am specifically drawn to the AI-Powered Product Experiences responsibility. Apple's retail and marketing surfaces are where AI-powered product discovery and personalization will have real consumer impact. Building the frontend for intelligent recommendation and conversational interfaces on a platform of this scale is the kind of problem I find most compelling.

**8. Describe a time you significantly improved frontend performance — what did you measure, what did you change, and what was the outcome?**

At GeeksForGeeks, I took over a set of high-traffic page templates that were loading slowly on mobile — the platform served millions of monthly users, and the engineering bar for mobile performance on Indian networks (low bandwidth, high latency) was higher than the current implementation could meet. I started by instrumenting the pages with Lighthouse and field CWV data from Google Search Console. LCP was the primary problem: 4.2s at P75. Root cause: a large hero image with no explicit dimensions was loading eagerly and causing layout shift (CLS 0.28 too). I applied: (1) `loading="lazy"` on below-fold images, `fetchpriority="high"` on the LCP image; (2) explicit `width` and `height` on all images to eliminate CLS; (3) extracted and inlined critical CSS so the first paint was unblocked; (4) deferred third-party scripts to after `load`. Result: LCP improved to 2.1s at P75 (50% reduction), CLS dropped to 0.04, and measured user engagement improved by 30% — lower bounce rate on mobile correlated with the performance improvement over the following four weeks.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
- **Work authorization** — confirm India work authorization status
