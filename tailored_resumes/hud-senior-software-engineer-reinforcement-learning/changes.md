# HUD tailoring and verification

Prepared October 25, 2026 for Senior Software Engineer, Reinforcement Learning.

## Scope and sources
Root resume.tex is the factual source; the supplied HUD description controls targeting. Existing tailored documents provided layout conventions only. No new employers, titles, dates, degrees, technologies, outcomes, or metrics were invented. Original contacts and live link destinations were retained. Existing folders were not overwritten; this is a newly created application folder.

## Changes
- Added a concise summary centered on full-stack products, APIs, and AI applications.
- Prioritized end-to-end CMS ownership and data/API contracts at Moresand; kept both supported 50% metrics.
- Emphasized the MAQ AI assistant backend, retrieval workflows, and React/TypeScript interfaces; kept the 28% prompt accuracy metric without redefining it as an RL evaluation.
- Moved Docker/Jenkins delivery impact first at Techolution; preserved the 60% deployment-time reduction and 90% test coverage.
- Retained the internship's 30% engagement and 40% performance metrics without turning performance into a more specific unsupported measure.
- Positioned WebHealth around consolidated automated audit reports. Did not relabel it as an RL evaluation or observability platform.
- Listed Python as a baseline skill only. Omitted unverified Postgres, Rust, Kubernetes, Terraform, Grafana and direct RL claims.
- Preserved education without adding dates. Kept original employer spelling GeekForGeeks.
- Added matching cover material, screening answer drafts and an explicit gap matrix.

## ATS and layout
The original uses tabular* for contacts and role headings, creating potential reading-order ambiguity. These were replaced by linear text. Original nested lists and manual spacing were simplified. No multi-column body, fontawesome macros, hidden text, keyword layer, or ligature-control packages were present. The unused icon package marvosym was removed. The tailored version uses a single column, visible contact text, ordinary headings, A4 paper, 0.55-inch margins, and nominal 10pt body text. PDF units report approximately 9.96 points because TeX points differ from PDF points.

## Checks performed
- Compiled resume and cover letter using local Tectonic in a dedicated temporary build directory.
- Both final PDFs are one page; build logs contain no LaTeX warnings or overfull/underfull box messages.
- Extracted final resume text with pdfplumber into resume.txt.
- Asserted the name, email, phone, all employers and employment dates, ordered section headings, and relevant stack terms were present. Checked for replacement glyphs.
- Rendered both PDFs with Poppler and visually inspected both page previews for readable text, clipping, overlap and page breaks.
- Checked cover letter page count and extracted contact details after final regeneration.
- Verified original resume.tex and adjacent resume.pdf SHA-256 values were unchanged.
- No external ATS checker was run; no ATS pass or score is claimed. Layout and extraction checks cannot guarantee a particular employer's parser or ranking.

## Original file integrity
resume.tex before and after: 3bd46be32fe8618267ba77113fc461bfb5623fab6791bb4d8177fb43d26d43e8
resume.pdf before and after: 45d87d6fde8b62bfa44bbfefa7545aea03094d9b5d0fadde27c81d46d3225166

## Limits and confirmations
Experience is grounded in the supplied baseline, not independently audited. Direct RL tooling, production Python depth, observability and research/vendor collaboration remain unverified. Location, working hours, work authorization, relocation, salary, availability and work-trial participation require confirmation in application_answers.md. Nothing was submitted or sent.
