# Flick tailoring changes and verification
Prepared October 25, 2026.

## Scope and sources
Original resume.tex is the sole factual baseline. Read the saved workflow and baseline. Inventoried all 162 existing tailored files, deduplicated by SHA-256 (132 unique contents), scanned text/source structures, extracted PDF text and preview metadata for conventions. Read the Cardboard resume, letter, changes, gap matrix and answer drafts in detail as formatting references. This was not an audit of prior applications; no additional candidate claims were imported.

All changes are confined to the new flick-founding-full-stack-engineer folder: 12 requested deliverables. No application code, callers, fixtures, tests, configuration or exports need changes. Root files and existing applications remain untouched.

## Changes and preserved facts
- Moved production experience ahead of education; added a compact summary of supported full-stack and backend experience.
- Prioritized CMS architecture, schemas, API versioning, service boundaries and production AI orchestration for Flick's backend-heavy role.
- Led applicable bullets with supported outcomes: onboarding -50%, development effort -50%, prompt accuracy +28%, deployment time -60%, test coverage 90%, internship engagement +30% and performance +40%.
- Put delivery reliability first at Techolution; grouped backend, React/TypeScript, AI/data, infrastructure and testing skills.
- Preserved contacts and URLs, employers, locations, employment titles/dates, degree, project name, award/year, team size and supported metrics. Condensed WebHealth's technology list while retaining its actual auditing scope.
- Added a matching cover letter, screening drafts, full supplied JD and qualitative evidence matrices. Python remains a listed skill; media, WebGL, distributed scale, concurrency, observability and model training are not claimed as experience.

## ATS-hostile baseline scan
Found tabular contact/role headings, a custom tabular subheading macro, manual alignment spacing, negative spacing, an unsupported 20pt article option and small-text helper macros. The body is not multi-column. No fontawesome/icon macros, explicit ligature-manipulation packages, hidden text layers or other reading-order tricks were found. Unused symbol packages were not retained.

Tailored sources use standard 10pt article, Latin Modern type, 0.55-inch margins, visible contact details, ordinary headings and sequential single-column text. Removed table macros and manual alignment. Natural font ligatures remain. pypdf extraction introduced false spaces in some employer names; final resume.txt uses pdfplumber extraction with NFKC Unicode normalization and preserves names correctly. Universal parser compatibility is not asserted.

## Checks actually performed
- Both actual sources successfully compiled with Tectonic in an isolated temporary directory. Final logs contain no overfull/underfull boxes, missing characters or LaTeX/package warnings. An initial command referenced a nonexistent temporary source and failed before compilation; it was corrected without affecting deliverables.
- Both final PDFs are one A4 page with selectable text. Sources use nominal 10pt body type (approximately 9.963 PDF points). Assertions checked A4 dimensions, minimum font size and all text within a 0.5-inch safety boundary.
- Rendered both PDFs to 1600-pixel-height PNGs with pdftoppm and visually inspected them, including a larger cropped inspection of the letter text. No clipping, overlap, awkward breaks or illegible text found. Letter closing whitespace is normal.
- Extracted final resume text with pdfplumber into resume.txt. Assertions checked contacts, every employer/title/date, degree, metrics, key technologies, unique employer headings, section order and absence of replacement/null characters.
- Verified the four expected contact hyperlinks in each PDF; the resume also retains the project hyperlink. A preliminary link-count check expected five links in both PDFs and was corrected to verify the actual four contact URLs individually.
- Compared all 164 pre-existing files captured in the preservation manifest (162 tailored files and root resume.tex/resume.pdf): all remain byte-for-byte unchanged. Existing folders were not overwritten.
- Only requested deliverables are in the application folder. Build logs and auxiliary files remain temporary. No external ATS checker or numerical score was used.

## Original integrity
- resume.tex SHA-256 before and after: `3bd46be32fe8618267ba77113fc461bfb5623fab6791bb4d8177fb43d26d43e8`.
- resume.pdf SHA-256 before and after: `45d87d6fde8b62bfa44bbfefa7545aea03094d9b5d0fadde27c81d46d3225166`.

## Limits and confirmations
No independent audit of baseline claims/metrics, external ATS scoring, company-link research or live skill validation was performed. Supplied JD is used as given. Exact employment start days and graduation dates are absent. application_answers.md flags film/art interest, creative/open-source work, additional technical depth, product collaboration, metric methodology, availability, location, work authorization and compensation for confirmation. No application was submitted or sent.
