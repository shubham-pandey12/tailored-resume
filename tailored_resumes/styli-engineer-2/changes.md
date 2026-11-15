# Styli Engineer 2 - changes and verification
Prepared October 25, 2026.

## Scope and evidence
Created a new application folder containing the resume, cover letter, supplied JD, screening drafts, alignment matrix, extracted text and previews. Original resume.tex is the sole factual baseline. Existing tailored files were inventoried and deduplicated by SHA-256; selected resume sources, cover letter source and reports were reviewed for conventions. Older documents were not exhaustively read or visually reviewed, and no additional factual claims were imported from them.

## Tailoring
- Ordered sections: Summary, Skills Summary, Work Experience, Projects, Education, Achievements.
- Prioritized React.js, Redux, Node.js, Express.js, RESTful APIs, MongoDB, TypeScript, cloud tooling, Docker and testing, at the level supported by baseline evidence.
- Surfaced fullstack CMS ownership, API integration, reusable widgets, Redis caching and measured delivery/test outcomes.
- Preserved contacts/links, employers, job titles, locations, dates, education, award and supported metrics. Kept internship separate and general experience duration distinct from MERN-specific tenure.
- Included Google OAuth and GCP as listed project technologies without inventing authentication implementation details or production deployment ownership.
- Deprioritized unrelated Java/Python and AI tooling in the skills summary while retaining truthful MAQ work outcomes.

## ATS and layout
Baseline uses tabular contacts and role headings, a custom subheading macro, an unsupported 20pt article option, negative spacing and small-font helper macros. Replaced these with a sequential one-column body, visible contact text, ordinary headings, standard 10pt article, 0.55-inch margins and selectable text. No fontawesome icons, multi-column body, hidden text or ligature-manipulation package found in the baseline. The tailored version contains none of those constructs. Retained the formal serif type and ruled section style.

## Checks actually performed
- Compiled resume and cover letter using local Tectonic in an isolated temporary directory. Final compiler output reported no warnings or errors.
- Both final PDFs have one A4 page. Body font is nominal 10 TeX points (approximately 9.963 PDF points).
- Extracted text with pdfplumber, checked contacts, employers, dates, degree, impact metrics and relevant keywords; asserted section order, unique employer occurrence, no replacement glyphs and text bounds within margins. Rechecked the revised resume after the final wording edit.
- Rendered both final PDFs using Poppler and visually inspected previews for spacing, readability, overlap and clipping.
- All 134 pre-existing files in the preservation manifest remain byte-for-byte unchanged; no existing tailored folder was overwritten.
- Original resume.tex SHA-256 before and after: 3bd46be32fe8618267ba77113fc461bfb5623fab6791bb4d8177fb43d26d43e8.
- No application was sent or submitted. No redundant PDF aliases or build intermediates were placed in the application folder.

## Limits and confirmation
No external ATS checker or independent claim audit. MongoDB query optimization, JWT, serverless, specific cloud operations ownership and three years of full MERN experience remain unverified. Screening drafts mark personal details, metric methodology, detailed tool usage, Agile practices, designer collaboration and debugging examples for confirmation.
