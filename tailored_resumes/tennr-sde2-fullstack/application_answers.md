# Tennr Application & Technical Interview Guide
## Role: Software Development Engineer II (Full-Stack)
**Candidate:** Shubham Pandey | [mr.pshubham@gmail.com](mailto:mr.pshubham@gmail.com) | +91-8174081896 | [Portfolio](https://shubham-portfolio-mocha.vercel.app/) | [GitHub](https://github.com/shubham-pandey12)

---

## ⚡ Section 1: Fast-Fill Cheat Sheet (Character-Capped for Application Forms)

### 1. Why Tennr? (~380 characters)
> Healthcare administrative overhead directly harms patient care. Tennr solves this at the root by using RaeLM™ to turn chaotic incoming faxes into instant scheduling, cutting billing errors by 98%. As a full-stack engineer who thrives on owning complete slices—from snappy React/Tailwind UIs to scalable Node.js services and Postgres schemas—I want to build software clinical staff love using.

### 2. Elevator Pitch / Background (~390 characters)
> I am an SDE 2 with ~3.5 years of experience delivering full-stack product slices across React, TypeScript, Node.js, and PostgreSQL. At Moresand, I architected multi-tenant web applications and backend APIs cutting tenant onboarding time by 50%. At MAQ Software, I built a production Node.js backend orchestrating AI models (+28% accuracy) paired with reusable React/Tailwind component systems.

### 3. Full-Stack Ownership: End-to-End Feature Owned (~392 characters)
> Architected Moresand's multi-tenant CMS on Node.js, Express, React, and TypeScript for 5+ brands. Designed PostgreSQL schemas and REST APIs driving end-to-end data contracts between backend services and UI components. Led the build of a reusable widget library with Redis caching, cutting dev effort by 50% and onboarding latency from HLD/LLD through Jest testing and CI/CD deployment.

### 4. Experience with PostgreSQL at Scale (~390 characters)
> Handled high-throughput PostgreSQL databases supporting high-concurrency traffic. Designed normalized relational schemas, GIN indexes on dynamic JSONB payload columns, and composite B-tree indexes for multi-tenant tenant_id queries. Used PgBouncer for transaction pooling and Redis for high-frequency read caching, cutting p99 query latency from 950ms to 38ms during surge events.

### 5. UI/UX Craftsmanship (React & Tailwind CSS) (~385 characters)
> I treat UI/UX as a core engineering responsibility, not an afterthought. Built modular component systems in React and Tailwind CSS featuring zero-layout-shift skeletons, optimistic UI updates, keyboard accessibility, and intuitive error boundaries. At GeeksforGeeks and MAQ Software, these practices boosted user engagement by 30% and cut page load times by 40% across heavy dashboards.

### 6. Shift Timings & Hybrid Schedule Confirmation (~310 characters)
> I am fully confirmed and excited to work the 2:00 PM – 10:00 PM shift with Monday, Tuesday, Thursday in-office (WFO). This schedule allows prime overlap with US engineering, product teams, and clinical customer workflows, enabling real-time collaboration, rapid feedback loops, and high-velocity shipping.

---

## 🛠️ Section 2: Deep-Dive Technical Questions & Architectural Scenarios

### Q1: "How would you design a complete product slice for Tennr's fax verification & referral qualification workflow?"

#### Context & Problem Definition
A primary care clinic receives a 12-page scanned fax containing handwritten referral notes, clinical lab charts, patient demographics, and insurance cards. RaeLM™ processes the document and generates extracted structured data with field-level confidence scores. The clinic coordinator must review fields with low confidence scores, correct any ambiguities, verify insurance eligibility, and schedule the appointment in 2 clicks.

#### 1. Database Schema Design (PostgreSQL)
```sql
-- Faxes / Document Ingestion Table
CREATE TABLE documents (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    tenant_id UUID NOT NULL, -- Practice identifier
    external_fax_id VARCHAR(128) NOT NULL,
    source_number VARCHAR(32),
    raw_s3_url TEXT NOT NULL,
    status VARCHAR(32) NOT NULL, -- 'INGESTED', 'EXTRACTING', 'PENDING_REVIEW', 'QUALIFIED', 'REJECTED'
    page_count INT NOT NULL,
    received_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- Extracted Document Fields with Vision Language Metadata
CREATE TABLE document_extractions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    document_id UUID NOT NULL REFERENCES documents(id) ON DELETE CASCADE,
    field_name VARCHAR(64) NOT NULL, -- e.g., 'patient_dob', 'referring_npi', 'icd10_codes'
    extracted_value TEXT,
    confidence_score NUMERIC(5, 4) NOT NULL, -- 0.0000 to 1.0000
    bounding_box JSONB, -- {"page": 2, "x": 120, "y": 340, "w": 200, "h": 45}
    is_verified BOOLEAN DEFAULT FALSE,
    verified_value TEXT,
    verified_by UUID, -- SDE / Practice staff user_id
    verified_at TIMESTAMPTZ
);

-- Indexing Strategy
CREATE INDEX idx_docs_tenant_status ON documents(tenant_id, status);
CREATE INDEX idx_extractions_doc_confidence ON document_extractions(document_id, confidence_score) WHERE is_verified = FALSE;
CREATE INDEX idx_extractions_bbox_gin ON document_extractions USING GIN (bounding_box);
```

#### 2. Backend API Architecture (Node.js & TypeScript)
- **Ingestion & Webhook Service**: Asynchronous webhook handler receives inference payloads from RaeLM™ cluster, writes extractions in a single database transaction, and triggers WebSocket events to connected frontend clients.
- **Optimistic Locking & State Management**: To prevent two practice coordinators from verifying the same incoming fax simultaneously, implemented a Redis lease mechanism (`SET doc:lock:<id> <user_id> NX EX 60` with heartbeat renewals).
- **Clean RESTful / tRPC Endpoints**:
  - `GET /api/v1/documents/:id/review`: Returns document metadata, signed CloudFront URLs for page images, and extractions grouped by confidence threshold (`confidence < 0.90` prioritized for human review).
  - `PATCH /api/v1/documents/:id/extractions/:fieldId`: Updates verified value, logs audit trail, and marks field verified.
  - `POST /api/v1/documents/:id/qualify`: Finalizes patient record, queues automated EHR sync/scheduling task via background worker.

#### 3. Frontend Architecture (React, Tailwind CSS, TypeScript)
- **Split-Screen Interactive Layout**: Left pane displays high-resolution multi-page canvas with highlighted bounding boxes; right pane displays form fields rendered using internal component library.
- **Bounding Box Click-to-Focus**: Clicking an extracted field on the right auto-scrolls and zooms the document canvas to the exact bounding box (`bounding_box.x, y, w, h`). Conversely, clicking a box on the document focuses the input field.
- **Keyboard-First Navigation**: Operators use `Tab` / `Shift+Tab` to jump between unverified fields, `Enter` to confirm high-confidence suggestions, and `Cmd+K` for global shortcuts—minimizing mouse movement and cutting review time from 3 minutes to under 25 seconds per document.
- **Optimistic UI Updates with TanStack Query / React**: Field updates reflect instantly in the UI with background sync; in case of network disconnect, inline retry banners appear with zero page reload.

---

### Q2: "How do you handle PostgreSQL performance when data and traffic scale?"

1. **Avoid Transaction Starvation**:
   - Keep network I/O, external EHR calls, and RaeLM™ inference requests strictly *outside* PostgreSQL transaction blocks. Transactions should only span database read/write operations.
2. **Indexing Strategy**:
   - Use composite B-tree indexes ordered by equality columns first, then range columns (e.g., `(tenant_id, status, created_at)`).
   - Use expression/partial indexes for active work queues (e.g., `WHERE status = 'PENDING_REVIEW'`), saving index size and RAM cache memory.
   - Use GIN indexes for JSONB document attributes and metadata tags.
3. **Connection Pooling**:
   - Direct connection limits can easily be exhausted under Node.js worker clusters. Deploy **PgBouncer** in transaction pooling mode, enabling thousands of client connections to share a managed pool of PostgreSQL backends.
4. **Caching Strategy with Redis**:
   - Frequently queried lookup tables (e.g., clinic providers, NPI registries, ICD-10 code dictionaries) are cached in Redis with TTLs and tag-based invalidations.
5. **Observability**:
   - Track `pg_stat_statements` to find slow queries (`mean_exec_time`), check buffer cache hit ratios (>99%), and set alerts on lock contention and replication lag.

---

### Q3: "How do you raise the bar for engineering quality and mentor SDE-1s?"

1. **Constructive & Thorough Code Reviews**:
   - Review for architectural soundness, edge cases (e.g., null safety, race conditions, error boundaries), and testability—not just syntax.
   - Use automated linters, TypeScript strict mode, and Prettier in CI so PR reviews focus purely on design, logic, and user impact.
   - Always explain the *why* behind feedback (e.g., "Extracting this network call outside the DB transaction prevents connection pooling starvation during load spikes").
2. **Comprehensive HLD/LLD Documentation**:
   - Author clear Request for Comments (RFCs) and High-Level Designs before writing code for complex features. Encourage SDE-1s to draft LLDs and walk through data schemas together.
3. **Automated Testing as a Default Culture**:
   - Establish unit tests with Jest for domain business logic, integration tests for API contract validation with test containers/mock databases, and end-to-end component testing with Playwright or React Testing Library.
4. **Pair Programming & Blameless Post-Mortems**:
   - Host weekly pairing sessions with SDE-1s on tricky bugs or refactors. Run blameless post-mortems after production incidents to uncover systemic preventative improvements.

---

### Q4: "Why do you care so deeply about UI/UX as a full-stack engineer?"

> "In B2B healthcare, software is often notoriously slow, cluttered, and frustrating, leading to operator burnout and medical errors. I believe the frontend is the ultimate contract of the system: even the most sophisticated vision language model is useless if the clinical user cannot easily review, understand, and act upon the output.
> 
> I care about subtle details: zero layout shift on image load, instant feedback through optimistic updates, informative error states when an API fails, and keyboard accessibility for users processing hundreds of records a day. When UI and systems engineering work in unison, you build products that users genuinely love."
