# Solum Health - changes and verification
Prepared October 25, 2026.

## Scope and factual authority
Read prompt.md and original resume.tex as the authoritative baseline. Captured SHA-256 hashes for 190 pre-existing root/application files before authoring. Inventoried prior tailored materials and deduplicated identical copies: inspected 94 unique text files for conventions, extracted text/read page counts from 30 unique PDFs, and checked 31 unique preview images for valid metadata. Historical previews were not all visually audited. Read the Asha Health resume, cover letter, application answers, changes and gap report in detail as formatting references only. Unsupported claims in historical drafts were excluded.

Created a new solum-health-ai-full-stack-engineer folder. The exact position title is absent from the supplied description: AI / Full-Stack Engineer is an inferred folder/report label, and the cover letter uses engineering role. No application was submitted or sent.

## Tailoring
- Summary leads with production AI assistant work, documented 28% prompt accuracy improvement, integrations, retrieval and full-stack ownership.
- Retained reverse chronological employment order, moving database/API/data-contract ownership ahead of caching under Moresand to emphasize integration work.
- Emphasized production AI orchestration and React/TypeScript delivery at MAQ without claiming autonomous agents or specific LLM providers.
- Retained the WebHealth crawler and audit integrations as website automation, without relabeling them browser automation or healthcare experience.
- Put AI/backend and data integration skills first; retained Next.js, Python and testing at their documented scope. Omitted less relevant skill details to keep one readable page.
- Preserved name/contact/link destinations, all four employers, locations, titles and dates, institution/degree, award/year/team size and supported metrics: 5+ brands, 50% onboarding, 50% development effort, 28% prompt accuracy, 90% test coverage, 60% deployment time, 30% engagement and 40% performance.
- Added a grounded cover letter, full supplied description, screening drafts and explicit requirement/evidence matrix.

## ATS and source scan
Original contains tabular contacts/employment headings and a custom two-column resumeSubheading macro, unsupported article 20pt option, negative spacing and small-font helper macros. No fontawesome icons, multi-column body, hidden keywords or ligature package found. Used the existing clean tailored format with sequential headings/contacts and employment text, standard article 10pt and A4 geometry with 0.55-inch margins. No tables, graphics or icon macros in the tailored resume.

## Completed verification
- Compiled resume.tex and cover_letter.tex with local Tectonic in a dedicated temporary directory. Both succeeded; no compiler warnings reported. Only final PDFs copied into application folder; logs/auxiliary files excluded.
- Both PDFs are exactly one A4 page. Checked all text bounds against a 35-point inset and found no clipping outside that safe area.
- Extracted resume PDF text with pdfplumber and Unicode NFKC normalization, saved as resume.txt. Assertions passed for name/email/phone, employers, exact titles/dates, degree/institution, supported numerical metrics, section order, ten bullets and relevant technology/integration terms. No replacement or null characters found; employer names occur once each.
- Rendered and visually inspected every final PDF page at 1600-pixel height. No overlap, clipping, broken headings or awkward page breaks found. The short cover letter leaves normal whitespace below the signature.
- Rechecked all 190 pre-existing file hashes: unchanged. No original or prior tailored material overwritten.
- Original resume.tex SHA-256 before/after: 3bd46be32fe8618267ba77113fc461bfb5623fab6791bb4d8177fb43d26d43e8.

## Limits and required confirmations
No external ATS checker, live listing/company verification, independent factual audit or application submission performed. Month-only dates support approximately 3 years 3 months full-time tenure, excluding the internship.
Confirm majority coding-agent use and real review workflow; LLM architecture, prompt design/versioning, evals and live-traffic A/B testing; metric methodology; third-party/webhook/browser/document specifics; startup cadence and customer rollout examples. Healthcare, FastAPI and n8n remain unverified gaps. Personal confirmations include motivation, exact employment/graduation dates, location/authorization/relocation, compensation, notice/start dates and willingness to work more than 12 hours/day with common weekends. See application_answers.md for flagged drafts.
