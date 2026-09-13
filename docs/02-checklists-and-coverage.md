# 02 · Checklists and Coverage

Traceability: brief item → checks → result/finding.

## Block 1. Installation and permissions
| # | Check | Status | Reference |
|---|---|---|---|
| 1.1 | Clean installation and onboarding | ✔ | UX-2, UX-8 |
| 1.2 | Enable one client, Gmail | ✔ | UX-1 |
| 1.3 | Revoke and re-grant permission | ✔ | “Verified” |
| 1.4 | Behavior on an unconnected site | ✔ | — |

## Block 2. Email tracker detection
| # | Check | Status | Reference |
|---|---|---|---|
| 2.1 | Marketing emails: banner / eye / counters | ✔ | “Verified” |
| 2.2 | False positives on regular emails | ✔ no detections | “Verified” |
| 2.3 | Duplicate/event inflation | ✖ defect | UX-3 |
| 2.4 | Banner ↔ report ↔ popup consistency | ✔ | “Verified” |

## Block 3. Tabs and navigation
| # | Check | Status | Reference |
|---|---|---|---|
| 3.1 | Multiple tabs | ✔ | “Verified” |
| 3.2 | Folders and threads | ✔ | “Verified” |
| 3.3 | Two clients in parallel | N/A | Gmail only |

## Block 4. Reload and network
| # | Check | Status | Reference |
|---|---|---|---|
| 4.1 | Page reload | ✔ | “Verified” |
| 4.2 | Full Chrome restart | ✔ | “Verified” |
| 4.3 | Slow 3G | ✔ | “Verified” |
| 4.4 | Data consistency after restarts | ✔ | “Verified” |

## Block 5. Popup and report
| # | Check | Status | Reference |
|---|---|---|---|
| 5.1 | Popup | ✔ | UX-9 |
| 5.2 | Period/client filters | ✔ | UX-1 |
| 5.3 | Domain allowlist | ✔ add flow | Q-3 |
| 5.4 | Clear with confirmation | ✔ | “Verified” |
| 5.5 | CSV/JSON export | ✔ | BUG-2 data, F-11* |
| 5.6 | Empty states | ✖ artifact | COS-1, COS-2 |

## Block 6. Tracking-link warning
| # | Check | Status | Reference |
|---|---|---|---|
| 6.1 | Warning on tracking wrapper | ✖ core defect | BUG-1, UX-7 |

## Block 7. Console
| # | Check | Status | Reference |
|---|---|---|---|
| 7.1 | Explicit extension errors | ✔ no errors | “Verified” |

## Block 8. Exploratory
- Sessions: themes/languages, extension disable/enable, right click, period boundaries, locale and CSV analysis.
- Session findings: BUG-3, UX-4…UX-6, COPY-1…COPY-4, Q-4, Q-5.

*F-11 is an observation about CSV quality: no URL/event ID is included. It was moved into the developer questions.