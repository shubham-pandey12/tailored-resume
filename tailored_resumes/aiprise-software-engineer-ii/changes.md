# AiPrise - changes and verification
Prepared October 25, 2026.

## Scope and factual sources
The root resume.tex is the sole factual authority. Read prompt.md and the supplied full JD. Inventoried all existing tailored files, deduplicated their content by SHA-256, and programmatically reviewed text/source/report headings, PDF text and page counts, and preview dimensions for conventions. Read the recent Cardboard resume/cover sources and change report and Styli gap report in detail. This was not a visual audit of every historical preview. Older tailored claims supplied no new factual evidence.

Created a new aiprise-software-engineer-ii folder containing only the requested application deliverables. Original resume sources/PDF and all prior tailored files were preserved. No application was submitted or sent.

## Tailoring and preserved facts
- Prioritized end-to-end platform ownership, REST APIs, database schemas, API integration/data mapping, AI retrieval orchestration, testing and delivery.
- Reordered Moresand bullets: CMS ownership, schema/API contracts, reusable integration/data mapping and Redis, then test/CI/CD ownership.
- Used the established readable one-column layout: Summary, Work Experience, Projects, Skills Summary, Education, Achievements. Backend/data/infrastructure skills are prominent; less relevant Redux/GraphQL and extra project-tool listings were omitted for space.
- Retained all four employers, exact titles, employment dates and locations, contacts/links, degree, award/year/team size, and supported numerical outcomes (5+ brands, 50% onboarding, 50% effort, 28% accuracy, 90% coverage, 60% deployment time, 30% engagement, 40% performance).
- Preserved website/brand onboarding as such; did not relabel it KYC onboarding. Kept AI experience specific to assistant retrieval orchestration.
- Created matching cover letter, full supplied JD, likely screening answers, detailed minimum/preferred/responsibility evidence matrix and previews. Personal and unsupported-experience answers require confirmation.

## ATS-hostile baseline constructs
Baseline uses tabular contact/employment headings and a custom resumeSubheading column macro, an unsupported 20pt article option, aggressive negative spacing, and small-font helper macros. Replaced the table-based reading order and helpers with sequential text headings, standard 10pt article and 0.55-inch margins while retaining serif type and ruled sections. No multi-column body environment, fontawesome icons, hidden-text layers, ligature-manipulation package, or other reading-order trick found. Unused marvosym/symbol/template packages not retained. Standard font ligatures remain selectable and normalize correctly in the final text extraction.

## Checks actually performed
- Both sources compiled successfully with local Tectonic in an isolated temporary directory; final compiler output contained no errors or warnings. Only final PDFs were copied back, with no build auxiliaries or aliases.
- Both PDFs have exactly one A4 page (595.28 x 841.89 PDF points). Sources specify 10pt body text and 0.55-inch margins; extracted body glyph size is approximately 9.963 PDF points, the standard TeX/PDF unit conversion.
- Rendered both pages at 1600-pixel height and visually inspected the final previews. No clipping, overlap, broken headings, awkward page breaks, or illegible text found.
- Extracted PDF text with pdfplumber and Unicode NFKC normalization into resume.txt. Assertions passed for contacts, employer names, exact titles/dates, degree, metrics, ten bullets, key role terms, heading order, absence of replacement glyphs, and nonduplicated employers. Both documents' text bounding boxes remain inside 35-point page insets.
- An initial pypdf extraction introduced artificial spaces in kerned words and retained ligature characters; switched to pdfplumber with tighter character grouping and Unicode normalization for the final parsing check. This is not a guarantee that all external parsers behave identically.
- SHA-256 comparison passed for all 152 existing files captured before authoring, including original resume.tex, original resume.pdf and prior application files.
- Original resume.tex SHA-256 before and after: 3bd46be32fe8618267ba77113fc461bfb5623fab6791bb4d8177fb43d26d43e8.
- Original resume.pdf SHA-256 before and after: 45d87d6fde8b62bfa44bbfefa7545aea03094d9b5d0fadde27c81d46d3225166.

## Limits and confirmations
No external ATS checker, live job/company verification, or independent claim audit was run; the supplied JD is the application target. Flask/compliance domain, vendor scale, monitoring/incidents, mentoring and other gaps remain explicit in the matrix. Approximately 3 years 3 months of full-time tenure is based on month-only dates; the internship is separate. Confirm San Jose/in-person availability, relocation, work authorization/sponsorship, notice/start dates, compensation, exact employment/graduation dates if requested, metric methodology and actual mentoring/collaboration/debugging examples before using the relevant answers.
