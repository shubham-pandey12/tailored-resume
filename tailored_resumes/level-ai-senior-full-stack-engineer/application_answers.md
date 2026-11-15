# Application Answers — Level AI, Senior Full Stack Engineer

---

## Why Level AI?

Level AI is solving one of the most technically demanding problems in enterprise AI: delivering real-time, context-aware assistance to human agents during live customer interactions — where latency, accuracy, and reliability are all critical at once. That is not a generic LLM wrapper; it is infrastructure-grade AI engineering. I am drawn to Level AI because the engineering challenges (real-time pipelines, multi-tenant isolation, agent-facing UX, LLM integration at production scale) are exactly what I have been building toward with my full-stack and AI workflow experience. I want to contribute to a product where the stack I know — React, TypeScript, Node.js, Redis, GraphQL — directly powers AI capabilities that contact-center teams depend on every day.

---

## Multi-Tenant Architecture Experience

At Moresand Technologies I architected a multi-tenant SaaS CMS from scratch, serving 5+ luxury travel brands on shared Node.js/NestJS infrastructure. Each tenant operates with isolated data schemas and configurable API integrations while sharing the same backend services and React component library. I designed the tenancy model, owned the PostgreSQL schema strategy, versioned the APIs to support brand-specific customization, and built the Redis caching layer that kept high-traffic endpoints performant across all tenants. The system cut new-brand onboarding time by 50%.

Key decisions I made and can discuss in depth: schema-per-tenant vs. row-level isolation tradeoffs, JWT-based tenant context propagation, and cache invalidation strategy per tenant.

---

## Real-Time AI Product Experience

At MAQ Software I built the backend service powering a real-time AI assistant. The system integrated Azure AI Search as a retrieval layer, assembled context for LLM prompts, and delivered responses under strict latency constraints. I owned the full retrieval-to-response pipeline: API design, search query construction, orchestration logic, and error handling for graceful degradation when the LLM or search layer was slow. This improved prompt accuracy by 28% vs. the previous approach.

I understand the engineering reality of real-time AI workflows: you cannot treat the LLM as a black box in production — you need deterministic fallbacks, context budget management, and observability at every stage of the pipeline.

---

## Full-Stack Ownership

At Moresand I own the full lifecycle of every feature: I write the PostgreSQL migration, design the REST or GraphQL API, implement the Node.js/NestJS handler, build the React component consuming it, write the unit and integration tests, and ship it through CI/CD. I have never handed off work mid-feature — full ownership is the mode I operate in by default.

At MAQ I repeated this pattern on AI product features: backend retrieval service, API contract, frontend component library, all owned by the same engineer (me).

---

## Experience with AI-Assisted Workflows

[CONFIRM: Feel free to add any additional context about AI tools or products you have personally used or developed beyond what is in the resume, before submitting.]

At MAQ Software, I built the backend for a production AI assistant that surfaces contextually relevant information to users in real time. The system needed to handle concurrent requests, manage LLM prompt size constraints, and degrade gracefully when retrieval was slow. I also developed the React + TypeScript frontend that consumed streaming responses and displayed them in a low-latency UI.

I am familiar with the UX patterns of agent-assist tools: progressive disclosure of AI suggestions, confidence indicators, fallback copy when the AI is uncertain, and keyboard-first interaction design for contact-center agents who operate under time pressure.

---

## Salary Expectation

[CONFIRM: Fill in your current/expected CTC before submitting.]

---

## Notice Period

[CONFIRM: Confirm your current notice period before submitting.]
