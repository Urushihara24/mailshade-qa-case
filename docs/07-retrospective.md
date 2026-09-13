# 07 · Retrospective

## What strengthened the case
- **Data triangulation:** comparing the same metrics across popup ↔ dashboard ↔ banner ↔ CSV produced most of the strongest confirmations and also proved consistency where it existed.
- **Static locale analysis:** exposed hidden features such as the context menu, missing contact information, a broken key↔text pair, and mixed tone — issues that are difficult to discover through clicking alone.
- **CSV forensics:** UTC vs local-time arithmetic closed BUG-2 and explained the duplicate-looking batches in UX-3.
- **Manual base64 decoding** proved that the real destination in BUG-1 was technically extractable.
- **Video evidence** was necessary for flickering artifacts in BUG-3; still screenshots could not prove the behavior.
- **Scope honesty:** N/A and “not tested” were recorded explicitly rather than silently omitted.

## What weakened the case / lessons learned
- Environment details such as OS, Chrome version, and extension version were recorded too late and required several reminders.  
  **Rule for future work:** environment passport is the first step before execution.
- Evidence chronology: the order of two dashboard screenshots remained unclear for too long, and the early BUG-002 hypothesis that a filter reset the report was rejected only after a direct rerun.  
  **Rule:** capture every artifact immediately with a timestamp and sequence number.
- The first timezone hypothesis, “the table renders +2 while the user is at +3”, was inverted: the table was accurate and the system timezone was not.  
  **Rule:** validate environment assumptions with a direct command such as `date` before publishing them in a report.
- A weak COPY-5 finding entered the draft and was removed only after critical review.  
  **Rule:** perform a self-check — “is this actually a defect, or a legitimate design choice?” — before adding a finding.

## Case metrics
- 19 final findings: 3 BUG / 9 UX / 3 COS / 4 COPY; 1 finding withdrawn during self-review; 6 developer questions.
- 15 “verified and working” scenarios.
- Evidence: 14+ screenshots, 6 videos, 2 data files, CSV and locale dump.
- Brief coverage: 100% of executable items; 2 items marked N/A because of environment constraints.