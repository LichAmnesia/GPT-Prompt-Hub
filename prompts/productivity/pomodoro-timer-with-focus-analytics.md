---
title: "Pomodoro Timer PWA with Focus Analytics"
category: productivity
tags: [pomodoro, focus, time-management, pwa, analytics]
model: any
use_case: "Spec a pomodoro app that ties sessions to tasks and produces weekly focus analytics."
---

# Pomodoro Timer PWA with Focus Analytics

## Role
You are a front-end engineer who has shipped multiple focus apps. You know that the hard part of pomodoro apps is not the timer - it is habit adherence and meaningful analytics.

## Objective
Spec a pomodoro timer that connects sessions to tasks, tracks streaks, surfaces weekly focus analytics, and ships as an installable PWA.

## Inputs needed
- Default interval lengths (work / short break / long break / cycles before long break)
- Task-integration source (local-only, Todoist API, Linear, etc.)
- Offline requirement (must / nice)
- Notification posture (web push opt-in, sound, visual only)
- Target platforms

## Output format
1. Feature list split into MVP and v2
2. UI spec: timer screen, task picker, history, analytics dashboard, settings
3. Animation spec for the circular progress indicator (frame budget, reduced-motion fallback)
4. Data model: Session, Task, Interruption, DayStat, WeekStat
5. Analytics surfaces: streak, longest focus day, interruption rate, task-to-session ratio
6. Notification strategy: tabs-hidden, PWA installed, system-do-not-disturb
7. Keyboard shortcuts (start, pause, reset, skip, open-task-picker)
8. Focus-mode behavior: block tab-switching detection? show overlay? grey-out other UI?
9. Telemetry events (local, opt-in to sync)
10. Acceptance checklist (12 items)

## Constraints
- No account required for MVP.
- Must work offline end-to-end.
- Interruption must be counted and surfaced in analytics - not swept under the rug.
- Do not default to alarming sounds; make the bell configurable and calm.

## Example (optional)
Input: 25/5/15 default, local-only tasks, mobile + desktop PWA, web push opt-in.
Output: 11 MVP features, 5-entity model, 4 analytics surfaces, 9 shortcuts.
