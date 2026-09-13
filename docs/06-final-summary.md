# 06 · Final Report — Version Delivered to the Client

## 1. Environment
- OS: Zorin OS 18.1 Education, Linux / Ubuntu-based
- Browser: Google Chrome 149.0.7827.155, official 64-bit build
- Extension: Mailshade 1.0.5; the brief specified public version 1.0.3 and the mismatch was documented
- Mail: Gmail, one test account; no personal or work mailbox was used
- Locale/theme: Russian / dark “Auto”; English and light theme were also checked
- Timezone: expected Moscow UTC+3; system behavior observed as UTC+2

## 2. Functional bugs
BUG-1 … BUG-3 — full reports are available in [03-bug-reports.md](03-bug-reports.md).

## 3. UX issues
UX-1 … UX-9 — see [04-ux-copy-findings.md](04-ux-copy-findings.md).

## 4. Copy / visual / i18n
COS-1 … COS-3 and COPY-1 … COPY-4 are documented in the same file.

## 5. Verified and working correctly
- Clean installation and onboarding; site permission revoke and re-grant.
- Banner/eye/counters; values remain consistent between banner, report, and popup, for example 15=15, 164=164, and 33+15=48.
- No false positives observed; tabs and email threads behave correctly.
- Filters, Refresh, allowlist, clear-with-confirmation, CSV export, empty states, themes, and languages.
- Page reload, full Chrome restart, and Slow 3G: data remains available and no additional artifacts appear.
- Console: no explicit extension errors observed.

## 6. Risk summary
1. BUG-1: the advertised click-tracking bypass does not work, creating a reputation risk in a core product feature.
2. UX-3: event inflation undermines trust in the metrics, which are a central product surface.
3. Version mismatch between 1.0.3 and 1.0.5 complicates reproducibility checks.
4. After the trial, history is reduced to seven days and CSV becomes Pro-only; without clear communication this can read as “my data disappeared”.
5. BUG-2: midnight date mismatches make the report look internally inconsistent.

## 7. Overall impression
Mailshade feels like a thoughtfully designed product with strong privacy communication: onboarding is short, permission boundaries are explained honestly, dangerous actions require confirmation, empty states are meaningful, accessibility strings are present, English localization is complete, and theme/language switching is synchronized.

Pixel detection and the banner ↔ report ↔ popup chain are stable and numerically consistent. The main mismatch is between the quality of the shell and the core link-warning behavior: the warning triggers, but it does not reveal the real destination and the UI masks that by showing duplicate URLs. The metrics need a “trust pass”: deduplicate events across repeated opens and unify terminology.

The collection of smaller findings points to a need for final polish rather than systemic instability. Before a broad release I would close BUG-1 and UX-3 first; the rest is mainly lower-impact polish. The Linux run did not expose platform-specific critical issues, which is a positive result for an extension of this type.