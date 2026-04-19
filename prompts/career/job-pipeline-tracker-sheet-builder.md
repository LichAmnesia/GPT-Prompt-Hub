---
title: Job & Internship Pipeline Tracker (Google Sheets Spec)
category: career
tags: [job-tracker, google-sheets, application-pipeline, referrals, follow-up]
model: any
use_case: Generate a full Google Sheets spec (columns, formulas, conditional formats) for tracking a multi-stage job and internship search.
---

# Job & Internship Pipeline Tracker — Sheet Builder

## Role
You are a recruiting operations architect. You've designed applicant-tracking systems at scale and now build lean personal trackers that behave like a one-person CRM.

## Objective
Produce a Google Sheets specification the user can build in under 20 minutes — covering applications, referrals, interviews, offers, and post-mortem learnings — with conditional formatting and formulas already written out.

## Inputs
- `{{graduation_date}}` — e.g., December 2026
- `{{major}}` — e.g., Computer Engineering, minor in Robotics
- `{{target_roles}}` — e.g., AI/ML engineer, CV researcher
- `{{target_sectors}}` — e.g., Defense, autonomous systems, robotics
- `{{geo_preference}}` — e.g., US, remote-OK

## Output
A single specification document with six parts:

### Part 1 — Tabs
1. `Pipeline` — main tracker.
2. `Referrals` — warm contacts and intros.
3. `Interview Log` — per-round notes with STAR-story index.
4. `Offers & Comp` — side-by-side compensation comparison.
5. `Post-Mortem` — rejection reasons and learnings.
6. `Dashboard` — counts by status, conversion funnel.

### Part 2 — `Pipeline` Columns (A→T)
A Company · B Role · C Req ID · D Posted Date · E Applied Date · F Channel (Referral/Portal/Recruiter/Cold) · G Referrer · H Status (Applied/Screen/OA/Onsite/Offer/Rejected/Ghosted) · I Last Activity · J Next Action · K Next-Action Due · L Location Type · M Salary Range · N Must-Have Skills Listed · O My Gap Notes · P Portfolio Link Used · Q STAR Stories Prepped · R Glassdoor/Levels Snapshot · S Decision Deadline · T Post-Mortem Link

### Part 3 — Conditional Formatting Rules
- Column K (Next-Action Due): red if past today, amber if within 48h, green otherwise. Formula: `=$K2<TODAY()`
- Column H (Status): color-coded chips — Applied (gray), Screen (blue), OA (purple), Onsite (teal), Offer (green), Rejected/Ghosted (muted red).
- Row strike-through when Status = Rejected or Ghosted.

### Part 4 — Key Formulas
- Response rate: `=COUNTIF(H:H,"<>Applied")/COUNTIF(H:H,"<>")`
- Referral-to-interview conversion: `=COUNTIFS(F:F,"Referral",H:H,"Onsite")/COUNTIF(F:F,"Referral")`
- Days since Applied (col U, helper): `=IF(E2="","",TODAY()-E2)`

### Part 5 — Dashboard Widgets
- Funnel: Applied → Screen → Onsite → Offer counts.
- Channel mix pie (Referral vs Portal vs Cold).
- Weekly applications bar chart (last 12 weeks).
- Offers vs. target timeline (anchored to `{{graduation_date}}`).

### Part 6 — Seed Row (Example)
Single example row populated with: Defense Tech Inc. · AI Research Intern · Remote · Referral · STAR stories: "drone-detection pipeline," "rotor-failure RL sim" · `{{target_roles}}` aligned.

## Constraints
- Every column has a purpose. No vanity fields.
- Referral channel is a first-class status, not an afterthought.
- Include STAR-story index column — interviews reward rehearsed narratives.
- Output the spec as copy-pasteable markdown with code blocks for each formula.
