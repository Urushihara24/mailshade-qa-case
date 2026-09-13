# 01 · Test Plan

| Metadata | |
|---|---|
| Document version | 1.0 |
| Date | 2026-08-06 |
| Author | Vsevolod (QA) |
| Source | Client brief, two iterations: baseline run + expanded run |

## 1. Goals

1. Validate Mailshade extension user scenarios in a real environment.
2. Identify functional defects, UX problems, visual inconsistencies, and copy issues.
3. Collect reproducible evidence for every finding.
4. Provide the client with a concise risk summary and a holistic product assessment.

## 2. Scope

### In scope
- Clean installation, onboarding, and permission model: grant, revoke, and re-grant.
- Tracker detection: banner, eye indicator, counters, false positives, and duplicates.
- Report: filters, periods, empty states, refresh, clear, and CSV/JSON export.
- Settings: all sections, themes, languages, allowlisted domains, and sender lists.
- Tracking-link warning on a naturally encountered tracking wrapper.
- Popup, context menu, reload/restart, slow network, and Console.
- Exploratory sessions totaling ≥ 60 minutes with deliberate sequence disruption.
- Analysis of public extension resources: locale catalog and CSV export.

### Out of scope — per brief
- Paid activation and stress testing with 1000+ trackers.
- A second mail client, which was unavailable and marked N/A rather than omitted.
- Automated testing.

## 3. Strategy and techniques

- Checklist-based testing by brief sections; see document 02.
- Exploratory testing using charters such as “break the sequence”, “boundary states”, and “data consistency across surfaces”.
- Negative/edge testing: empty states, removing/restoring filters, and invalid form input.
- Data consistency: compare the same metrics across popup ↔ dashboard ↔ banner ↔ CSV.
- i18n/UX review: RU/EN, light/dark theme, tone, and terminology.
- Static resource analysis: `_locales/ru/messages.json` for hidden features and broken key↔text pairs.

## 4. Criteria

- **Entry:** extension installed from CWS; Gmail test account available; DevTools accessible.
- **Exit:** all brief items are covered or honestly marked N/A / not tested; every finding includes steps, expected/actual behavior, reproducibility, and evidence.

## 5. Severity classification

| Severity | Definition | Examples in this case |
|---|---|---|
| Critical | Data loss, security issue, blocking scenario | — |
| Major | A core feature does not deliver its promise, or data is materially misleading | BUG-1, UX-3 |
| Minor | Non-critical behavior/copy defect affecting trust or usability | BUG-2, BUG-3, UX-1… |
| Cosmetic | Visual artifact with no functional impact | COS-1…3 |

Priority was intentionally not assigned because prioritization belongs to the product owner. The report includes severity only; this is a deliberate documented decision.

## 6. Testing risks and mitigations

| Risk | Mitigation |
|---|---|
| Extension auto-update during testing, 1.0.3 → 1.0.5 | Version recorded in environment; Q-1 raised to the client |
| Environment timezone instability, expected +3 but observed +2 | Cross-checked arithmetically using CSV/local/chart data and documented in environment notes |
| Only one mail client available | Parallel-client cases marked N/A and partially compensated with multiple tabs/threads |

## 7. Artifacts

Findings spreadsheet, written report, indexed evidence folder, report generators, and this repository.