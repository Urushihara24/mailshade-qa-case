# 04 · UX / Cosmetic / Copy Findings

## UX

**UX-1 · Minor · Dashboard “Clients” filter does not reflect actual permissions.**  
Where: dashboard ↔ settings ↔ onboarding. Problem: with only Gmail connected, all six clients are checked in the filter.  
Why it matters: the user deliberately granted access to one site, while the interface implies that everything is enabled.  
Expected: only the connected client should be active; the rest should be unchecked or marked as unavailable. The locale even contains “Access required on this device”, but that message is not used. Evidence: `onboarding_clients.png`, `dashboard_filters.png`, `settings_clients.png`.

**UX-2 · Minor · Pro trial activates automatically without opt-out.**  
Where: onboarding, step 3. Problem: the screen states “14-day Pro trial activated” with no skip action.  
Why it matters: consent to the trial and related conditions is implicit.  
Expected: explicit user choice. Evidence: `onboarding_trial.png`.

**UX-3 · Major · Events multiply every time an email is opened; no deduplication.**  
Where: report and KPI surfaces. Problem: each email open logs a complete batch of link events: 48 → 74 → 164 with only two unique emails. Why it matters: the metrics are a product showcase, and inflation misrepresents the scale of tracking.  
Expected: deduplicate by email/link pair or expose a separate “unique links” metric.  
Evidence: `dashboard_74.png`, `export.csv`, `video_flicker_artifact.mp4`.

**UX-4 · Minor · “Recent activity” is limited to 50 rows with no pagination.**  
Expected: pagination or “show more”; anything above 50 is currently visible only in CSV. Evidence: `activity_table.png`.

**UX-5 · Minor · Tables have no sorting** by time, tracker count, or client. Evidence: `activity_table.png`.

**UX-6 · Minor · Mailshade context menu is available only inside an opened email.**  
Right-clicking an inbox row does not expose “Mailshade: …” actions, even though that is a natural interaction point. The feature is difficult to discover and was found through the locale catalog. Evidence: `context_menu.png`.

**UX-7 · Minor · “Open directly” / “Open original” actions are ambiguous.**  
The user cannot tell which navigation path is safer; with BUG-1 present, the choice becomes effectively blind. Evidence: `warning_same_urls.png`.

**UX-8 · Minor · Privacy text in onboarding is difficult to read.**  
The block is small, gray, low-contrast, and uses jargon such as accessibility label, host grants, and Chrome Sync.  
Expected: 3–4 concise bullets with technical detail collapsed below. Evidence: `onboarding_clients.png`.

**UX-9 · Minor · The same metrics use different names in popup and dashboard.**  
Popup: “Trackers detected / Senders with trackers / Tracking links found”; dashboard: “Tracker events / Unique senders / Link trackers”. Evidence: `popup.png`, `dashboard.png`.

## Cosmetic

| ID | Finding | Evidence |
|---|---|---|
| COS-1 | Extra period in card-style empty states on dashboard chart and sender list, while inline “Domains” empty state has no period; likely component inconsistency | `empty_dashboard.png`, `senders_empty.png` |
| COS-2 | “↔ 0%” on a completely empty report vs the more appropriate “—” when data exists but there is no history | `empty_dashboard.png` |
| COS-3 | Column headers are centered while cells are left-aligned | `activity_table.png` |

## Copy / i18n

| ID | Finding | Evidence |
|---|---|---|
| COPY-1 | “About” promises “Version and contacts”, but no contacts are shown and no contact strings exist in the locale at all | `about.png`, `locales_ru_messages.json` |
| COPY-2 | “Upgrade” section is effectively a Pro price list; USD is shown in RU locale | `upgrade.png` |
| COPY-3 | Mixed RU tone: informal “Use the email from your receipt” vs formal language elsewhere | `locales_ru_messages.json` |
| COPY-4 | Key `upgrade_feature_link_unwrap` contains the message “Export report to CSV”, creating a key/message mismatch | `locales_ru_messages.json`, `upgrade.png` |

> Process-quality note: an early COPY-5 finding about “terminology drift” was removed during self-review. The settings intro subtitle is static, while “Domains” and “Senders” are genuinely different lists with legitimately different names. Withdrawn findings are not erased from case history; see retrospective document 07.