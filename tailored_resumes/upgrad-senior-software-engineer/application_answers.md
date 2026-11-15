# Application Answers — upGrad | Senior Software Engineer

**Prepared:** October 30, 2026

---

## Application Form

Apply at: https://forms.gle/zsNeNqcvEPfDbFUd6 (linked in the LinkedIn job posting)

**LinkedIn:** https://www.linkedin.com/in/shubham-pandey-a74716199/  
**Portfolio:** https://shubham-portfolio-mocha.vercel.app/

---

## Likely Interview / Case Questions

**1. Walk me through how you'd diagnose a Core Web Vitals regression in production.**

Start with the data: RUM or field data (CrUX) to confirm the regression is real, not a fluke — which page, which metric (LCP, INP, CLS, TTFB), which user segment (device type, connection, geography). Then reproduce in lab with Lighthouse or WebPageTest to get a filmstrip and waterfall. For LCP, I look at what element is the candidate, when it starts loading, and what delays it — render-blocking resources, slow server response, unoptimized images, late discovery. For INP, I use Chrome DevTools Performance panel to find long tasks on the main thread — usually hydration, large event handlers, or layout thrash. For CLS, I check layout shifts in the DevTools Rendering tab and look for images without dimensions, dynamically injected content above the fold, or web fonts causing FOIT/FOUT. I fix one variable at a time and validate with Lighthouse before and after. This is exactly what I built WebHealth to do systematically — integrating Lighthouse so teams don't have to run this manually for each audit.

**2. When would you choose SSR vs SSG vs CSR in Next.js — and what are the trade-offs?**

SSG (Static Site Generation) is my default for content that doesn't change per-user and doesn't need to be real-time — documentation, marketing pages, blog posts. It gives you a pre-rendered HTML file on a CDN edge, the best possible TTFB, and no server compute on request. The trade-off: stale data between deploys; ISR (Incremental Static Regeneration) handles this when you need periodic freshness.

SSR (Server-Side Rendering) is for content that's user-specific or must be fresh at request time — a personalized dashboard, a search results page with session context. The trade-off: TTFB goes up because you're waiting on the server; you pay for compute on every request. I apply aggressive caching on SSR routes to mitigate this.

CSR (Client-Side Rendering) I use only for below-the-fold, low-priority, or highly interactive UI where SEO doesn't matter and hydration cost is acceptable. I avoid CSR for anything above the fold — it hurts LCP significantly.

For hydration, I use React 18's selective hydration and defer hydrating non-critical components. I also watch bundle size carefully — heavy third-party scripts that hydrate eagerly are a common LCP and INP killer.

**3. How do you design reusable frontend foundations that scale across teams?**

Three principles. First: design for the consumer, not the implementer — the component's API should be what a product engineer naturally reaches for, not a reflection of internal complexity. I spend time on the props interface before I write any implementation. Second: separate concerns clearly — a presentational component (pure render, no data fetching) from a container or hook that manages state and side effects. This makes the foundation testable and composable without hidden coupling. Third: document the constraints, not just the usage — what this component handles, what it deliberately doesn't handle, and what the caller is responsible for. At Moresand, I built a library of reusable widgets and templates that 5+ enterprise brands use; the key to reuse was making the data mapping contract explicit so each brand's integration was a config change, not a fork.

For scale across teams: versioned packages with changelogs, an internal design system doc with examples, and a contribution pattern so teams can extend without modifying the base. A shared component that two teams own is a component that neither team will maintain well.

**4. How do you use AI effectively in your engineering workflow — and where do you draw the line?**

AI is part of my standard toolkit — I use Claude for exploring unfamiliar codebases, generating test cases for edge conditions I might miss, and writing first drafts of boilerplate (API clients, form validators, data-fetching hooks). I use GitHub Copilot for in-editor completion where it saves keystrokes on patterns I already know well. I treat AI output as a starting point, not a final answer: I read every line it produces, understand what it does and why, and own the decision to ship it. I've caught confident-sounding bugs, missed edge cases, and performance anti-patterns in AI-generated code. The value of AI is speed on the parts of the problem that are well-defined; the engineering judgement on the parts that are not is still mine.

Where I draw the line: I don't use AI to make architectural decisions, I don't ship AI-generated code I can't explain, and I don't let it substitute for reading documentation when I'm learning something genuinely new. An AI that confidently fills in a gap it doesn't actually know is worse than admitting uncertainty.

**5. Describe a performance vs. maintainability trade-off you've had to make.**

At Moresand, I built a Redis-backed caching layer for high-traffic API endpoints that served brand-specific data across 5+ clients. The performance win was real — API response latency dropped significantly. But the trade-off was cache invalidation complexity: each brand had different data freshness requirements, and a stale cache for one client wasn't acceptable to another. The naive solution (short TTLs) defeated the purpose; the complex solution (event-driven invalidation on data mutations) added significant maintenance overhead.

I chose a middle path: tiered TTLs by data type (brand config vs. real-time inventory) with a forced invalidation endpoint that product teams could call on deploys. Not the most elegant engineering, but the simplest design that actually matched the access patterns and that the team could reason about under pressure. Simple over clever — the cache worked reliably in production and never caused an incident. More sophisticated invalidation would have been a better solution in theory; in practice it would have been a production liability.

---

## Answers Requiring User Confirmation

- **Current compensation** — confirm before answering
- **Expected compensation** — confirm before answering
- **Notice period** — confirm before answering
