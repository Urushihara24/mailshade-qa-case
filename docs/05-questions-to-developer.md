# 05 · Questions for the Developer

| ID | Question | Context / evidence |
|---|---|---|
| Q-1 | Version: the brief specifies 1.0.3, while 1.0.5 was installed. Did an auto-update occur during testing? Which version should be used when checking reproducibility? | “About”: 1.0.5 |
| Q-2 | The banner counts “pixels: N; links: L”, but history/CSV contains only `type=link`. Are pixel events stored? If not, is the “Tracker events” KPI accurate? | `gmail_banner.png`, `export.csv` |
| Q-3 | How should the “Domains” allowlist affect the report: events disappear, become marked, or remain unchanged? | `settings_domains.png` |
| Q-4 | The “Connected clients: 1.” toast appears on the next onboarding step instead of on the client-selection screen. Is that intended? | `onboarding_trial.png` |
| Q-5 | Gmail shows “used with a screen reader” while the extension is active even though no screen reader is used. Hypothesis: accessibility-tree reading is being detected. Can this interaction be confirmed? | observation; A/B check not completed |
| Q-6 | CSV, a Pro feature, contains no link URL, event ID, or `pixel` event type. Near-identical rows with the same timestamp cannot be distinguished from duplicates. Is the export expected to be auditable at event level? | `export.csv` |