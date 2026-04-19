---
title: "Eisenhower-Matrix Todo App Spec with GTD Inbox"
category: productivity
tags: [todo, eisenhower-matrix, gtd, task-management, frontend]
model: any
use_case: "Spec a todo app that combines GTD inbox flow with Eisenhower-matrix prioritization and energy-based scheduling."
---

# Eisenhower-Matrix Todo App Spec with GTD Inbox

## Role
You are a senior front-end engineer who has read the GTD and Eisenhower classics and refuses to ship yet another generic checkbox list.

## Objective
Spec a todo app with a GTD inbox, 2x2 Eisenhower prioritization, energy-tagged scheduling, and an honest "overdue triage" flow.

## Inputs needed
- Target user (solo operator, team member, both)
- Storage (local-only / BYO-cloud / hosted)
- Integrations (calendar, Slack, email capture) - optional
- Platforms (browser-first / mobile PWA / desktop)
- Offline requirement

## Output format
1. Philosophy statement (max 5 lines): why this app is not another Todo MVC clone
2. Core flows: Capture -> Clarify -> Organize -> Engage -> Review (GTD)
3. Eisenhower matrix UI spec: 2x2 grid, drag between quadrants, auto-decay rules
4. Energy tagging: High / Medium / Low energy; scheduled against time-of-day profile
5. Overdue triage flow: never "mark done by default"; force reschedule/drop/delegate decision
6. Data model: Task, Project, Context, Tag, EnergyLevel, Review
7. Weekly review screen: prompts, required artifacts, streak tracking
8. Keyboard shortcuts (20+, composable like Vim motions if possible)
9. Offline/sync conflict resolution (last-write-wins vs. CRDT-lite)
10. Accessibility and micro-interaction guidelines

## Constraints
- No "Inbox Zero shame" UI; default to "carried forward" not "overdue red".
- Drag-drop must have keyboard equivalent.
- Energy tag is required for any task older than 72 hours.
- Do not add social / streak gamification that creates anxiety.

## Example (optional)
Input: solo operator, local-first, mobile + desktop, no integrations at launch.
Output: 13 MVP features, GTD 5-step flow, 7-entity data model, 22 shortcuts, weekly-review screen spec.
