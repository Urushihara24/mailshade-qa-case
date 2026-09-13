# 03 · Bug Reports

Status of all reports at publication time: **Reported** and delivered to the client.  
Template: [templates/bug-report.md](../templates/bug-report.md).

---

**ID:** BUG-1  
**Title:** Link warning does not reveal the real destination address; Customer.io unwrap does not work  
**Severity:** Major · **Type:** Functional / Data  
**Client/URL:** Gmail, email from notifications@mail.remotehunter.com using an `e.customeriomail.com` wrapper  
**Environment:** Zorin OS 18.1 / Chrome 149.0.7827.155 / Mailshade 1.0.5

**Steps to reproduce:**
1. Open a RemoteHunter marketing email in Gmail.
2. Click the “Apply Now” link whose href is an `e.customeriomail.com/e/c/<base64>` wrapper.

**Expected result:** the “Real address” field shows the unwrapped destination, such as `https://www.remotehunter.com/apply-with-ai/…`; the target href is present in the base64 wrapper and can be extracted directly.  
**Actual result:** “Original URL” and “Real address” are identical and both show the wrapper; the “Open directly” action therefore does not guarantee tracking bypass. Reproduced on two different links.  
**Reproducibility:** 2/2.  
**Evidence:** `warning_same_urls.png`; manual base64 decoding, which produced the real addresses within a minute.  
**Notes / hypothesis:** detection triggers correctly, but destination extraction is either not performed or not surfaced. The wrapper format is standard Customer.io and is technically unwrap-able. The issue is aggravated by unclear button semantics, tracked as UX-7.  
**Status:** Reported.

---

**ID:** BUG-2  
**Title:** Chart buckets events by UTC day while the table uses local date  
**Severity:** Minor · **Type:** Data / Visual  
**Client/URL:** Gmail / report dashboard  
**Environment:** same as above; see document 08 for the timezone nuance

**Steps to reproduce:**
1. Open emails shortly after local midnight, producing events around 00:5x–01:1x on 06.08.
2. Compare the date in “Recent activity”, the chart X-axis, and the CSV export.

**Expected result:** table and chart display the same calendar date.  
**Actual result:** the table shows 06.08 local time; CSV contains `2026-08-05T22:5xZ`, which is correct UTC; the chart plots the point under “5 Aug.” using the UTC day. “Today” periods in popup and dashboard use local time and remain consistent with each other.  
**Reproducibility:** always for events after midnight when TZ > 0.  
**Evidence:** `dashboard_chart_utc.png`, `export.csv`.  
**Notes / hypothesis:** UTC storage and the local-time table are correct; only chart aggregation is inconsistent.  
**Status:** Reported.

---

**ID:** BUG-3  
**Title:** Injected UI renders unstably: eye indicator and banner flicker, email content ghosts during transitions  
**Severity:** Minor · **Type:** Visual  
**Client/URL:** Gmail inbox and opened email

**Steps to reproduce:**
1. Open the inbox containing RemoteHunter emails.
2. Open a marketing email, return to the inbox, and open it again.
3. Observe the eye indicator in email rows and the “Tracking detected in this email…” banner.

**Expected result:** the eye indicator and banner render once and remain stable.  
**Actual result:** the eye disappears/reappears; the banner collapses, disappears, and expands; email content temporarily duplicates during transitions. Counter values are not affected, which was verified separately.  
**Reproducibility:** always in the captured video.  
**Evidence:** `video_flicker_artifact.mp4`, which also demonstrates batch growth related to UX-3.  
**Notes / hypothesis:** repeated injection on Gmail DOM mutations without idempotent rendering.  
**Status:** Reported.