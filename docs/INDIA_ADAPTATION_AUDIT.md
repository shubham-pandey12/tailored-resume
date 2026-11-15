# India Adaptation Audit: ai-job-search

**Audited repo:** https://github.com/ai-job-search-dev/ai-job-search (upstream, MIT, cloned at HEAD `e9ab29d`, shallow)
**Audit date:** 2026-11-10
**Scope:** Phase 1 of the master prompt only. No code was changed in the audited repo.

---

## 1. Summary

ai-job-search is a Claude Code framework, not an application. There is no server, no database, and no scheduler. Its unit of work is a Claude Code slash command backed by a skill file, a subagent, and a set of Python or Bun CLI tools. The state lives in local files: `job_search_tracker.csv`, `job_scraper/seen_jobs.json`, and `documents/applications/<company>_<role>/`.

Its strengths map well onto the master prompt: a drafter-reviewer loop, a LaTeX compile-and-inspect loop, PDF and ATS text checks, posting integrity gating, deduplication keys, and an offline HTML dashboard. The main gaps are India-specific:

- **No Indian job source.** Every portal CLI targets a Danish or other European market. None of Naukri, Instahyre, Hirist, Wellfound, Cutshort, Foundit, iimjobs, Indeed India, or any India-located ATS board is integrated.
- **No ATS-board integration.** There is no Greenhouse, Lever, Ashby, or Workday connector. These are the best legitimate source for direct company postings.
- **No India compensation model.** Salary handling is index-based and Nordic-oriented (`salary_lookup.py`). There is no CTC (LPA) parsing, no minimum-CTC filter, and no currency handling.
- **No scheduled or daily run.** Nothing runs without an open Claude Code session. Phase 8 needs a launchd or cron wrapper.
- **No browser automation or form submission, by design.** The repo stops at drafts. The master prompt's Phase 6 asks for something the repo deliberately avoids, and some of it conflicts with the platforms' terms (see section 6).
- **Scoring model differs from the master prompt.** The repo uses five dimensions plus eligibility and language gates (`04-job-evaluation.md`). The master prompt's six-criterion weighting is not implemented. I have not yet read `04-job-evaluation.md` in full, so the exact dimension weights are unverified.

---

## 2. Existing architecture (verified)

| Layer | What it is | Evidence |
|---|---|---|
| Entry points | 14 user-facing commands: `/setup`, `/scrape`, `/rank`, `/apply`, `/interview`, `/outcome`, `/gmail-sync`, `/notion-sync`, `/html-report`, `/expand`, `/upskill`, `/add-template`, `/add-portal`, `/reset`. Twelve are files in `.claude/commands/`; `/scrape` and `/upskill` are implemented as skills. | `.claude/commands/*.md` (12 files) and `README.md` command table |
| Skills | `job-application-assistant` (profile, writing style, evaluation, CV templates, cover-letter templates, forms, interview prep, web research), `job-scraper`, `upskill` | `.claude/skills/*/SKILL.md` |
| Subagents | `posting-fetcher` (fetch one posting), `posting-scorer` (batch-score for `/rank`), `application-reviewer` (hiring-manager critique, drafter-reviewer pattern) | `.claude/agents/*.md`, each with a restricted tool list and no Edit/Write |
| Portal search | 6 Bun TypeScript CLIs: `jobbank-search`, `jobdanmark-search`, `jobindex-search`, `jobnet-search`, `linkedin-search`, `freehire-search` | `.agents/skills/*/cli/src/cli.ts`, invoked via `bun run` |
| Core tools | Python 3, about 5,300 lines in `tools/` | `tools/*.py` |
| Tests | 73 Python test files, about 906 test functions, plus TypeScript tests inside each portal CLI | `tests/`, `.agents/skills/*/cli/tests/` |
| CI | Skill and command lint, security-guards job, Python tests on 3.10 to 3.14, LaTeX smoke compile, CLI typechecks | `.github/workflows/ci.yml` |
| Permissions | Allowlist for the CLIs and tools. Denies reads of `.env`, `~/.ssh`, `~/.aws`, and POST-style `curl`. Asks before editing `tools/`, `.claude/`, `.agents/`, `.github/`. | `.claude/settings.json` |

### Key tools relevant to the master prompt

| Tool | Lines | Role | Reuse for India? |
|---|---:|---|---|
| `tools/posting_guard.py` | 525 | Deterministic integrity gate: hidden text, invisible characters, instruction-shaped lines, hidden links | Yes, as-is. Run on every new source. |
| `tools/job_key.py` | 392 | Dedup keys across runs | Yes. It is the seed for the duplicate-detection requirement in Phase 7. Check whether it normalizes URLs and company-role pairs. |
| `tools/scrape_state.py` | 148 | Persists seen jobs across scrapes | Yes. Extend the schema with `source`, `posted_at`, `discovered_at`. |
| `tools/rank_state.py` | 567 | Ranked-shortlist state, `seen_jobs.json` writes | Yes. Largest module, so read it before changing it. |
| `tools/verify_pdf.py` | 380 | Text layer, page count, ATS readability | Yes. Covers the "extract PDF text, check page count" requirement in Phase 5. |
| `tools/verify_layout.py` | 471 | Layout and overflow checks | Yes. Covers the layout and overflow requirement. |
| `tools/fetch_page.py` | 301 | HTTP fetch with `robots.txt` enforcement, deflate and zlib handling | Yes. Reuse for every direct career-page fetch. |
| `tools/robots_check.py` | 234 | `robots.txt` evaluation | Yes. Required for any new source. |
| `tools/security_guards.py` | 783 | CI guard against widening permissions or weakening gitignore | Keep. It protects any change this work makes. |
| `salary_lookup.py` | n/a | Fuzzy company salary benchmark from `salary_data.json` | Partly. Fuzzy matching is reusable. The index-based model is not. |

---

## 3. Existing capabilities mapped to the master prompt

| Master-prompt requirement | Status | Notes |
|---|---|---|
| Phase 1: audit docs | Done (this document) | |
| Phase 2: Indian job portals | **Missing** | No Naukri, Instahyre, Hirist, Wellfound, Cutshort, Foundit, or iimjobs CLI. `freehire-search` is an aggregator (`freehire.me`, "many countries and markets"). Its URL reference shows an `India` location value, so coverage is likely, but it needs a live query to confirm. |
| Phase 2: global sources | **Partial** | LinkedIn (`linkedin-search`, marked personal-use only in its own docs) and Indeed (mentioned in docs, no CLI). No Greenhouse, Lever, Ashby, or Workday connector. |
| Phase 2: required fields (company, title, JD, location, work mode, experience, skills, salary, posting date, apply URL, source, discovery time) | **Partial** | The portal CLIs return most of these. The tracker has no explicit `job_id`, `posted_at`, or `discovered_at` column yet. Verify in `scrape_state.py` before changing it. |
| Phase 3: configurable filters (roles, experience band, locations, min CTC, freshness, full-time only) | **Missing** | Filters live in prose in `job-application-assistant/`, not in a config file. No CTC or freshness filter. No YAML or JSON config. |
| Phase 4: six-criterion weighted scoring | **Different model** | Uses five scoring dimensions, with eligibility and language gates that run first. Would need a mapping layer or a rewrite of `04-job-evaluation.md`. Exact weights unverified. |
| Phase 4: explanation fields (why match, missing skills, gaps, recruiter concerns, ATS keywords, CV changes) | **Mostly present** | `/rank` returns strengths and gaps. `/apply` reviewer covers recruiter concerns and keywords. Not all six fields are in a single structured output. |
| Phase 5: LaTeX tailoring and compile loop | **Present** | `/apply` drafts, compiles with lualatex, inspects the rendered pages, and iterates. Enforces a 2-page CV. The master prompt's rule to keep the original design fits this loop. |
| Phase 5: PDF validation | **Present** | `verify_pdf.py` and `verify_layout.py`. |
| Phase 5: "do not regenerate if valid" | **Unverified** | Not checked. |
| Phase 6: browser automation and form filling | **Absent by design** | No Playwright, Puppeteer, or Claude in Chrome integration. `SECURITY.md` and the apply flow stop at drafts. Build only with explicit approval (section 6). |
| Phase 7: tracker with status vocabulary | **Present, differs** | `tests/test_tracker_status_vocab.py` exists. The master prompt's statuses (Discovered, Shortlisted, Resume Generated, Ready to Apply, Applied, Application Failed, Assessment Received, Interview Scheduled, Rejected, Offer Received) need a mapping check. |
| Phase 7: duplicate detection | **Partial** | `job_key.py` and `scrape_state.py` exist. Whether they cover normalized URLs and company-role pairs is unverified. |
| Phase 8: `/daily-search` | **Missing** | `/scrape` is interactive. No single command runs the whole chain. |
| Phase 8: scheduled run | **Missing** | No cron, launchd, or Claude Code scheduled task. |
| Phase 9: HTML dashboard | **Present, partial** | `/html-report` produces stat cards, status, sector, channel, and funnel charts, and a filterable table. Missing from the master prompt: match-score distribution, top-20 view, posting-date filter, and links to the tailored CV and cover letter. Verify before claiming any of these exist. |
| Phase 10: tests | **Present** | 73 Python test files and 906 test functions. Run `python -m pytest` before and after changes. Not run in this audit. |

---

## 4. Components to reuse

- Deterministic gates: `posting_guard.py`, `robots_check.py`, `fetch_page.py`.
- Dedup and state: `job_key.py`, `scrape_state.py`, `rank_state.py`.
- PDF validation: `verify_pdf.py`, `verify_layout.py`.
- Drafter-reviewer loop: `application-reviewer.md` and the `/apply` flow.
- Subagent split (`posting-fetcher`, `posting-scorer`): good model for an India batch scorer.
- Portal CLI template: `.agents/skills/*/cli/` shows the layout, test pattern, and `--ignore-scripts` install. A new India source should follow it exactly.
- `/add-portal`: already generates a new portal skill. Use it as the scaffolding path for new Indian sources.
- Security posture: `security_guards.py`, `settings.json` deny list, and posting-as-untrusted-data rules.

## 5. Components that need modification

1. **Profile and preferences.** Move target roles, experience band, locations, CTC floor, freshness window, and employment type into a config file (for example `config/search.yaml`) read by `/scrape` and `/rank`. Keep it out of the skill prose.
2. **Compensation.** Add a CTC parser that handles LPA, lakh, crore, INR monthly, and "not disclosed". Normalize to annual INR. Keep the Nordic salary tool separate.
3. **Tracker schema.** Add `job_id`, `source`, `posted_at`, `discovered_at`, `match_score`, `resume_path`, `cover_letter_path`, and the India statuses. Keep the CSV as the source of truth, since it is git-ignored and local.
4. **Scoring.** Map the master prompt's six criteria onto the existing five dimensions, or add a sixth. Keep the eligibility gate. Note that the framework's gate checks citizenship or PR. For an India-based candidate applying in India, it should pass by default, but confirm this with the user.
5. **Scraper scheduling.** Add a `/daily-search` command that chains existing steps, plus an optional launchd plist. Do not run it through an unattended Claude session.
6. **Dashboard.** Extend `/html-report` with the missing filters, score histogram, and top-20 list.
7. **Locale and config defaults.** `README.md` and the portal set assume a Danish or Nordic market. Check `CLAUDE.md`, `05-cv-templates.md`, and the language gate in `04-job-evaluation.md` for market-specific rules. I have not yet confirmed what the language gate assumes.

## 6. Constraints and risks

### Platform terms (this shapes Phase 2)
- **Naukri, Instahyre, Hirist, Wellfound, Cutshort, Foundit, iimjobs, Indeed, and LinkedIn** generally restrict automated access in their terms of service. I have not verified each one's current terms. Verify before writing any connector. The repo's own CI comment says LinkedIn automation violates its terms and keeps live portal tests out of CI.
- The master prompt says "use official APIs, public job feeds, supported integrations, and permitted access methods." Based on my knowledge, the lowest-risk India-relevant sources are:
  - **Greenhouse Job Board API** (public, no key): `boards-api.greenhouse.io/v1/boards/{token}/jobs`
  - **Lever postings API** (public): `api.lever.co/v0/postings/{company}?mode=json`
  - **Ashby job posting API** (public, per board): `api.ashbyhq.com/posting-api/job-board/{name}`
  - **Workday** career sites: per-tenant JSON endpoints, undocumented, so treat as unstable and verify before use.
  Confirm each endpoint and its terms before implementing. These endpoints return the job ID, location, and posting date. They do not return salary for every board.
- Some Indian portals may have partner APIs, but I have no verified evidence of any. Ask the user before pursuing a partner agreement.

### Application automation (Phase 6)
- Browser automation that fills and submits forms carries platform-ToS risk and can produce wrong answers in irreversible submissions. The repo's documented posture is drafts only, with the user submitting.
- The master prompt's own rule matches this: "Do not automate submission on platforms where it violates their terms" and "Keep final submission approval enabled by default." Any form automation needs an explicit per-platform decision from the user.
- Claude in Chrome or Playwright could fill fields for drafts without submitting. That is the smallest reliable integration and it can be built behind approval.

### Security and data
- Postings and portal output are untrusted. Existing trust-boundary rules and `posting_guard.py` cover this. Keep the rules for every new source.
- Personal data: `.gitignore` covers `job_search_tracker.csv`, `documents/`, and personal profile files. Verify it also covers any new `config/` file that holds CTC or contact details, and any new SQLite database.
- The master prompt says never commit the personal resume to a public repository. The audited repo is a public upstream. Work must happen in a private fork, as `SETUP.md` section 8 describes.
- The user's CV source is `resume.tex` in the working folder, not in the audited repo. This audit did not read it. Verify all profile facts against it before any tailoring.

### Repo mismatch
- The working folder `job-hunter/resume` is not the ai-job-search repo. Its parent git repo is `shubham-pandey12/job-hunter`, with a separate `AGENTS.md` describing a different `scraper/` and `app/` project. Confirm which codebase the work should land in.

### Known limitations of the upstream repo
- No Python dependency manifest at the root (no `requirements*.txt`, `pyproject.toml`, or `setup.py`). CI installs only `pyyaml` for the lint job. Confirm before adding new Python dependencies.
- Portal CLIs depend on Bun. The user must install it.
- All work runs inside a Claude Code session. Output depends on the model.

## 7. Implementation plan (prioritized)

| # | Work | Effort | Blocks | Needs user input? |
|---|---|---|---|---|
| 1 | Decide target: private fork of ai-job-search, or the existing `job-hunter` repo | S | everything | Yes |
| 2 | Read `04-job-evaluation.md` and `05-cv-templates.md`. Record the exact scoring rubric and mapping for the six-criterion model. | S | 4 | No |
| 3 | Run the existing test suite and CI locally. Record the baseline. | S | regression | No |
| 4 | Add `config/search.yaml` with the Phase 3 defaults. Wire it into `/scrape` and `/rank`. | M | 5, 6 | No (values given) |
| 5 | Add a CTC parser and an INR normalizer. Add unit tests for LPA, lakh, crore, monthly, and "not disclosed". | M | 6 | No |
| 6 | Add a Greenhouse + Lever + Ashby connector, following the portal CLI template and `posting_guard`. Use a `companies.yaml` list of Indian product companies. Add mock-based tests. Live tests stay local. | L | 7 | Yes: the company list |
| 7 | Verify whether `freehire-search` covers India. If yes, expose it as an India source. | S | none | No |
| 8 | Extend the tracker schema and status vocabulary. Add a duplicate detector keyed on job ID, normalized URL, and company-role. Add regression tests for the scenarios in Phase 10. | M | 9 | No |
| 9 | Add `/daily-search` that chains existing steps and ends at an approval gate. | M | 10 | No |
| 10 | Extend `/html-report` with the missing filters, histogram, and top-20. | M | none | No |
| 11 | Optional: launchd plist for a local run. | S | none | Yes: confirm the schedule |
| 12 | Browser-assisted draft filling, no submit, behind per-platform approval. | L | none | Yes: which platforms, and the approval rule |
| 13 | Security review of new connectors and config files. | S | merge | No |

## 8. Decisions needed from the user

1. **Target repo:** a private fork of ai-job-search, or the existing `job-hunter` repo? The audited repo is public upstream, and your personal data must not be committed to it.
2. **Indian portals:** may I proceed with Greenhouse, Lever, and Ashby as the first sources, and hold Naukri and the other portals until their terms are checked? I recommend this order.
3. **Application automation:** draft-only (fill but never submit), or a supervised submit flow on specific platforms?
4. **Profile source:** should the candidate profile come from `resume.tex` in the working folder?

## 9. Verification status

- Read: `README.md`, `AGENTS.md`, `SECURITY.md`, `.claude/settings.json`, the agent definitions, the `job-scraper` skill header, `.github/workflows/ci.yml` (first 80 lines), `04-job-evaluation.md` (first 40 lines), and the `/apply` flow section of the README.
- Searched: all files for Indian portal names, ATS names, and "India", plus browser-automation library names.
- **Not run:** the test suite, CI, portal CLIs, or any live network call.
- **Not verified:** exact scoring weights, freehire India coverage, each portal's current terms, the Greenhouse/Lever/Ashby endpoint behavior, and the `.gitignore` coverage of new files.
