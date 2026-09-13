# QA Case: Manual Testing of the Mailshade Chrome Extension

Portfolio case based on real freelance work: user-facing and exploratory testing of the Mailshade extension (tracking-pixel blocking in webmail, local reporting, and tracking-link warnings). The report and findings table were accepted by the client; this repository contains an expanded version of the case documented using structured QA practices.

<p align="center">
  <img src="https://img.shields.io/badge/Chrome-Extension-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Chrome">
  <img src="https://img.shields.io/badge/Gmail-Integration-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  <img src="https://img.shields.io/badge/Linux-Zorin_OS-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Python-Report_Tools-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
</p>

| Scope | Investigation | Result |
|---|---|---|
| Chrome extension, Gmail integration, UX and localization | Exploratory sessions, CSV and locale analysis, screenshots and video evidence | 19 findings, including major link-unwrapping and event-deduplication risks |

**Start here:** [final summary](docs/06-final-summary.md) · [bug reports](docs/03-bug-reports.md) · [evidence index](evidence/EVIDENCE_INDEX.md)

## Case profile

| Parameter | Value |
|---|---|
| Product | Mailshade, Chrome Web Store public build |
| Work type | Manual user-facing testing + exploratory testing |
| Role | QA tester and documentation author |
| OS / browser | Zorin OS 18.1 Education (Linux) / Chrome 149.0.7827.155 (64-bit) |
| Extension version | 1.0.5; the brief specified 1.0.3, and the mismatch is documented in Q-1 |
| Mail client | Gmail, test account |
| Duration | ~4–5 hours including exploratory sessions |

## Results in numbers

- **19 findings**: 3 BUG, including 1 Major in a core feature; 9 UX, including 1 Major; 3 Cosmetic; 4 Copy/i18n;
- **6 developer questions** covering versioning, pixel-event data model, allowlist behavior, and export semantics;
- **15 “verified and working” scenarios** covering permissions, restart, Slow 3G, export, themes/languages, and more;
- **Evidence**: 14+ screenshots, 6 videos, CSV export, and a locale-catalog dump.

## Key findings — top 4

1. **BUG-1 (Major)** — the link warning shows identical URLs in “Original” and “Real address”: Customer.io unwrap does not work, so the advertised click-tracking bypass is not achieved.
2. **UX-3 (Major)** — event inflation: every email open logs a complete batch of link events, growing 48 → 74 → 164 for only two unique emails, with no deduplication.
3. **BUG-2** — the chart buckets events by UTC day while the table uses local time, causing date mismatches around midnight.
4. **BUG-3** — visual instability of Gmail injections: the eye icon/banner flickers and email content ghosts during transitions. Captured on video; data counters were not affected.

## Documentation navigation

| Document | Purpose |
|---|---|
| [01-test-plan.md](docs/01-test-plan.md) | Goals, scope, strategy, criteria, classification |
| [02-checklists-and-coverage.md](docs/02-checklists-and-coverage.md) | Checklists and brief → check → status traceability |
| [03-bug-reports.md](docs/03-bug-reports.md) | Full bug reports for BUG-1…BUG-3 |
| [04-ux-copy-findings.md](docs/04-ux-copy-findings.md) | UX / Cosmetic / Copy findings |
| [05-questions-to-developer.md](docs/05-questions-to-developer.md) | Questions requiring development input |
| [06-final-summary.md](docs/06-final-summary.md) | Final report version delivered to the client |
| [07-retrospective.md](docs/07-retrospective.md) | What strengthened and weakened the case |
| [08-environment-and-tools.md](docs/08-environment-and-tools.md) | Environment, tools, techniques |
| [templates/](templates/) | Bug-report and UX-finding templates |
| [evidence/EVIDENCE_INDEX.md](evidence/EVIDENCE_INDEX.md) | Evidence index: file → finding |

## Methods that made this case stronger

- **Locale forensics**: analysis of `_locales/ru/messages.json` exposed nonexistent contact information, a key/message mismatch, mixed formal/informal tone, and hidden functionality such as the context menu.
- **CSV forensics**: comparing UTC timestamps from the export with the local table and chart axis proved the bucketing defect in BUG-2 and explained the event duplication pattern in UX-3.
- **Video evidence**: content ghosting and injection flicker in BUG-3 could not be demonstrated reliably with still screenshots.
- **Manual base64 decoding** of the tracker wrapper proved that the real destination in BUG-1 was technically extractable.

## Confidentiality

No personal emails, addresses, or private data are stored in this repository. All senders used during testing were marketing messages in a test account; domains were pseudonymized where necessary. Tokens, keys, and passwords were not collected.

## Status

Documentation is frozen at the version accepted by the client. See [CHANGELOG.md](CHANGELOG.md).