# 08 · Environment and Tools

## Environment
| Parameter | Value | Note |
|---|---|---|
| OS | Zorin OS 18.1 Education | Linux, Ubuntu-based |
| Browser | Chrome 149.0.7827.155, 64-bit | `chrome://version` |
| Extension | Mailshade 1.0.5 | “About”; brief specified 1.0.3, see Q-1 |
| Mail | Gmail test account | personal/work mail was not used |
| TZ | system behaves as UTC+2 while Moscow time was expected | documented as an environment characteristic |

## Tools
- Chrome DevTools: Network with Slow 3G and Console filtered for Errors.
- `chrome://extensions` and `chrome://version` for permissions and version checks.
- `_locales/ru/messages.json` dump through DevTools for static string analysis.
- CSV analysis in spreadsheet/text form to compare timestamps and event batches.
- Manual base64 decoding of tracker wrappers.
- Screen recording and screenshots; Python with `openpyxl` and `python-docx` for report generators in `tools/`.

## Techniques
Checklist-based testing against the brief; exploratory testing with charters; negative/edge checks for empty states, invalid input, filter removal/restoration; data consistency across product surfaces; i18n/theme review; A/B checks with extension disable/enable.