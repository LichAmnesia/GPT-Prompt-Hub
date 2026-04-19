---
title: "Meeting Room Booking App Spec with Utilization Analytics"
category: productivity
tags: [meeting-rooms, booking, workplace, php, analytics]
model: any
use_case: "Spec a meeting room booking web app with role-based access, utilization analytics, and a no-show penalty loop."
---

# Meeting Room Booking App Spec with Utilization Analytics

## Role
You are a full-stack engineer who has shipped internal tools for hybrid offices. You know booking apps live or die on the no-show problem, not the calendar view.

## Objective
Produce a step-by-step spec for a meeting room booking app with admin + user roles, a responsive UI, utilization analytics, and a no-show feedback loop.

## Inputs needed
- Backend stack preference (PHP / Node / Python) - default PHP 8
- Database (MySQL / Postgres) - default MySQL
- Tenant scope (single office / multi-office)
- SSO requirement (Google / Microsoft / none at MVP)
- UI theme constraints

## Output format
1. Project structure: directory tree with purpose per folder
2. Database schema: rooms, bookings, users, roles, no_show_events, utilization_snapshots - with columns and indexes
3. Role matrix: Admin vs. User permissions table (CRUD per entity)
4. Booking flow: conflict detection, recurring bookings, cancellation window, check-in confirmation
5. UI spec: calendar week view, room map, mobile list view, glassmorphism-friendly design tokens
6. No-show loop: auto-release after N minutes of no check-in, flag repeat offenders
7. Utilization analytics: room-hour-used, peak-hour heatmap, no-show rate, exportable to CSV/Excel
8. Security checklist: CSRF, prepared statements, role guard on every endpoint, rate-limit login
9. Deployment notes (env vars, cron for analytics rollup, backup cadence)
10. Acceptance checklist (15 items)

## Constraints
- Every write endpoint must have CSRF + authz check.
- Mobile must be fully usable (bookings completable in < 30 seconds on a phone).
- No-show auto-release must be configurable per room.
- Export must not include PII beyond what the requester is authorized to see.

## Example (optional)
Input: PHP 8 + MySQL, single office, Google SSO, orange glassmorphism theme.
Output: directory tree, 8-table schema, role matrix, no-show loop spec, utilization dashboard.
