# Application Answers — Impact Analytics: Senior Software Engineer (Frontend - React)

**Preparation Date:** October 29, 2026

> Items marked **[CONFIRM]** require your personal input before submission.

---

## 1. Why Impact Analytics?

Impact Analytics's agentic-first approach to retail AI is compelling because it is a real production problem at global scale — not a demo. The combination of deep domain expertise and cutting-edge AI (LLMs, Generative AI, Google partnership) means the frontend work has genuine complexity: data-dense interfaces, AI-generated content that needs to be presented intuitively, and enterprise clients who need reliability. That is the kind of frontend challenge I find most interesting.

---

## 2. Describe your React expertise and component architecture approach.

I think in React — meaning I design components to be composable, testable, and state-aware from the first line. At Moresand Technologies (SDE 2) I build reusable component libraries using Redux for global state and Context API for scoped state, serving 5+ luxury travel brands from a single shared codebase. Every component is built through empty, loading, and error states from the start — not retrofitted. I own the end-to-end: from design handoff to production deployment, including REST API integration and performance optimisation.

---

## 3. How do you approach frontend performance optimisation?

- Profiling first: I use React DevTools and browser performance tools to identify actual bottlenecks before optimising.
- Memoisation: `React.memo`, `useMemo`, `useCallback` applied where re-renders are measurable, not by default.
- Code splitting: lazy loading routes and heavy components to reduce initial bundle size.
- API layer: Redis-backed caching at Moresand reduced API response latency by 50% on high-traffic endpoints; the frontend benefited directly from fewer waterfall fetches.
- Cross-browser: I test in Chrome, Firefox, and Safari; catch CSS issues with feature queries and progressive enhancement.

---

## 4. Testing approach — Jest and React Testing Library.

My standard: a test should fail if the feature it covers breaks. At Techolution I built unit and integration test suites achieving 90% coverage using Jest and React Testing Library — written to test components the way a user meets them (interactions, not implementation details). At Moresand I set coverage thresholds in CI/CD and established React Testing Library patterns as team conventions. I do not write tests that mock everything and assert nothing.

---

## 5. Experience with state management (Redux, Context API).

Both in production:
- **Redux**: used at Moresand for global application state across a multi-brand CMS — actions, reducers, selectors, and middleware for async API calls.
- **Context API**: used for scoped feature state (e.g., per-brand theme and config) where Redux would be overkill.
- Decision rule: Redux for state that is shared across distant components or needs time-travel debugging; Context for state that is local to a feature tree.

---

## 6. Agile / Scrum experience.

**[CONFIRM]** — Describe your sprint cadence (e.g., 2-week sprints), how you participate in planning, retrospectives, and standups. Suggested: "I work in 2-week Agile sprints at Moresand — daily standups, sprint planning with story pointing, and retrospectives. I own my own tickets from spec to PR to production."

---

## 7. AI-powered application experience relevant to Impact Analytics.

At MAQ Software I built React + TypeScript components for an agentic AI assistant — translating structured LLM outputs into data-dense, navigable interfaces for enterprise users. The challenge was the same one Impact Analytics faces: AI-generated content is often structured differently each time, so components must handle variability gracefully rather than assuming a fixed schema. I used AI coding tools (Claude Code, GitHub Copilot) daily and have clear opinions on where they generate plausible-but-wrong UI code.
