# Evidence Index

Case rule: every finding has at least one supporting artifact. Filenames match the names referenced in reports. If an item was captured on video, the file uses the same base name with the `.mp4` extension.

| File | Findings | Comment |
|---|---|---|
| warning_same_urls.png | BUG-1, UX-7 | warning with identical URLs |
| dashboard_chart_utc.png | BUG-2 | chart shows “5 Aug.” while the table shows 06.08 |
| export.csv | BUG-2, UX-3, Q-6 | UTC timestamps, event batches, near-identical rows |
| video_flicker_artifact.mp4 | BUG-3, UX-3 | injection flicker + batch growth |
| onboarding_clients.png | UX-1, UX-8 | onboarding step 2 |
| dashboard_filters.png | UX-1 | all six checkboxes selected |
| settings_clients.png | UX-1 | only Gmail enabled |
| onboarding_trial.png | UX-2, Q-4 | trial activation + delayed toast |
| dashboard_74.png | UX-3 | 44+30 after repeated opens |
| activity_table.png | UX-4, UX-5, COS-3 | activity table |
| context_menu.png | UX-6 | menu inside an opened email |
| popup.png | UX-9 | popup KPI labels |
| dashboard.png | UX-9 | dashboard KPI labels |
| empty_dashboard.png | COS-1, COS-2 | extra period + “↔ 0%” |
| senders_empty.png | COS-1 | “No one yet” with extra period |
| about.png | COPY-1 | version shown without contacts |
| upgrade.png | COPY-2, COPY-4 | pricing and Pro feature list |
| locales_ru_messages.json | COPY-3, COPY-4, Q-2 | locale dump |
| settings_domains.png | Q-3 | allowlist |
| gmail_banner.png | “Verified” | banner showing “pixels: 0; links: 15” |
| theme_light.png, lang_en.png | “Verified” | themes/languages |
| confirm_dialog.png | “Verified” | clear-confirmation dialog |

Folders: `screenshots/` for PNG files, `videos/` for MP4 files, and the `evidence/` root for CSV/JSON data.