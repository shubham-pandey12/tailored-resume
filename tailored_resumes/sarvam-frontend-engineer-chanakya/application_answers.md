# Application Answers — Sarvam AI | Frontend Engineer, Chanakya

**Prepared:** October 30, 2026

---

## Application Form

Direct apply via: https://www.sarvam.ai/careers/jobs/10a352d0-a65b-4599-8998-e09deef34349

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Website / Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview Questions

**1. Describe a production-grade frontend you built end-to-end — component architecture to deployment.**

At Moresand, I own the entire frontend layer of a multi-tenant SaaS platform serving 5+ enterprise clients. The architecture challenge was building one frontend that works correctly for every brand with different data models, workflows, and visual configurations. I designed the component architecture ground-up: a shared component library with clearly defined prop interfaces, a composition model where brand-specific configurations are injected rather than forked, and a Redux state management layer with typed slices per domain. I built CI/CD pipelines (Jenkins, Docker) that ran Jest unit and integration tests on every PR before deploying. Post-deployment, I set up structured logging and custom metrics dashboards to watch component-level rendering issues and API failure rates in production. When a caching bug caused stale state for one client, the observability I had built pinpointed the Redux selector that wasn't invalidating on the right event — fixed in under two hours. Owning end-to-end means the logging and alerting are part of the delivery, not a follow-up.

**2. How do you approach state management in complex React applications?**

I think about state in three tiers: server state (data fetched from APIs — cache invalidation, loading/error states), UI state (what is selected, what is open — usually local to a component or feature), and global shared state (user session, cross-feature coordination — Redux or Zustand depending on scale). The mistake most React codebases make is putting server state in Redux and then fighting cache invalidation forever. I separate them: REST API data lives in a query layer with controlled invalidation; global UI coordination lives in a Redux slice with typed actions; local UI state lives in component state. At Moresand, this separation made the codebase much easier to reason about — a new engineer could understand the state shape for any feature by reading one slice file, without tracing through thunks. For async patterns: I handle loading, error, and empty states explicitly at the component level, never leaving users looking at stale data or a spinner with no timeout.

**3. Describe your data visualization experience — what have you shipped in production?**

WebHealth is my strongest data viz project: a full-stack auditing platform with a React.js + TypeScript frontend that uses Recharts for multi-metric dashboards — performance scores, SEO metrics, accessibility scores over time, and comparative views across URLs. I also integrated Three.js for 3D visual reporting — a 3D site structure visualization showing crawl depth, page relationships, and link density. The design challenge was making complex, multi-axis data readable at a glance: I used composable Recharts components (LineChart, BarChart, RadialBarChart) with a consistent color encoding and tooltip pattern. At MAQ Software, I built data dashboards for an AI assistant backend — visualizing retrieval quality metrics, response latency distributions, and accuracy trends across prompt versions. The key discipline: start with the question the user needs to answer, then choose the chart type, not the other way around.

**4. How do you engineer frontend performance in resource-constrained environments?**

First, measure before optimizing. I use Google Lighthouse and browser DevTools to identify the actual bottleneck — it is rarely what you expect. Common fixes I apply: lazy loading routes and heavy components with React.lazy + Suspense; code splitting at the route boundary so the initial bundle is small; memoization (React.memo, useMemo, useCallback) at component boundaries that re-render on unrelated state changes; virtualizing long lists with a windowing approach; and compressing images aggressively with correct formats. At GfG, the 40% performance improvement came from a combination of Next.js image optimization, removing render-blocking scripts, and eliminating unnecessary re-renders through proper component decomposition. For low-bandwidth environments specifically, I minimize the number of API calls on initial load, prefetch critical data, and design graceful degradation when requests are slow or fail — the UI should always be useful, even on a 2G connection.

**5. Tell me about building reusable component libraries and shared frontend infrastructure.**

At Moresand, I built a shared component library from scratch: a set of primitive components (inputs, modals, tables, data grids) with a typed prop interface designed for composition, not configuration. Each component has a clear boundary — it owns its rendering and internal state, not the business logic of the feature using it. I documented the composition pattern so other engineers could build features without needing to understand the internals. The dividend: new features took 50% less time to build because engineers assembled from primitives instead of rewriting UI from scratch for each client. The key discipline is restraint — a shared component should do one thing extremely well, not ten things mediocrely. When a component starts growing conditionals for specific business cases, that is a signal to extract a variant rather than contaminate the base component.

**6. How do you debug across the frontend-backend boundary?**

I treat the API contract as the boundary. When something breaks, I check three things in order: (1) is the frontend sending the request correctly — correct endpoint, correct headers, correct payload shape? (2) Is the API responding correctly — correct status code, correct response shape, no unexpected nulls? (3) Is the frontend consuming the response correctly — are all code paths handled? I use browser DevTools network tab to inspect actual requests and responses, compare against the API spec, and isolate which side of the boundary owns the bug. At MAQ Software, half the production issues we investigated were frontend assumptions about the API response shape that weren't validated — I introduced explicit runtime validation of API responses in the frontend to make boundary mismatches visible immediately rather than manifesting as UI bugs. Sufficient backend awareness to read a Node.js or Python service log and understand what it is doing is essential — I have that from building the backends myself.

**7. Why Sarvam? Why sovereign AI for India?**

The problem Sarvam is solving is real and specific: AI that works for India at population scale, in India's languages, in India's infrastructure constraints, for India's institutions. That is a harder engineering problem than building an AI product for an idealised broadband user in a data-rich environment. The "constrained environments" requirement in this JD is not a footnote — it is the core engineering challenge, and it is the kind of problem I want to work on. Sarvam's atoms model — replicable, deployable product components that can be composed and embedded into client environments — is also a strong fit for how I think about frontend engineering: components as building blocks that travel, not monolithic apps that need rearchitecting for each deployment.

**8. Describe your experience with Three.js or 3D visualization.**

WebHealth uses Three.js to render a 3D site structure visualization — a graph where nodes are pages and edges are internal links, with depth encoded as the Z-axis and link density affecting node size. The goal was to make the crawl structure of a website visually scannable at a glance: which pages are deeply buried, which are highly linked, where are the isolated clusters. I used Three.js's WebGL renderer with OrbitControls for interactive rotation and zoom, implemented click-to-inspect for individual nodes, and managed the scene graph efficiently to handle sites with 100+ pages without frame rate drops. It was my first production Three.js integration — I learned the performance model (draw calls, geometry instancing, raycasting) hands-on.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
