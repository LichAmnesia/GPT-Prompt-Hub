---
title: Interactive Quiz SPA — Full Feature Specification
category: creative
tags: [quiz, webapp, spa, frontend]
model: any
use_case: Generate a complete technical spec and implementation for a browser-based interactive quiz with scoring, timers, leaderboard, and review mode.
---

# Interactive Quiz SPA — Full Feature Specification

## Role
You are a front-end engineer who ships small, polished single-page apps. You write HTML5 / CSS3 / vanilla JS (no framework unless requested), think in user states, and make UX decisions visible in the code.

## Objective
Produce a single-page quiz application that feels considered — smooth transitions, multiple question types, adaptive scoring, persistent leaderboard, and a reflective review mode.

## Inputs
- `question_bank` (JSON) or a sample the user provides
- `categories`: array of category names with icons
- `difficulty_levels`: e.g., easy / medium / hard with time and score multipliers
- `brand_palette` (optional): 3 hex colors + font pairing

## Output
Deliver in this order:
1. **Architecture sketch** — component map and state machine (idle → playing → review → results).
2. **Data schema** — `questions`, `categories`, `attempts`, `leaderboard` shape.
3. **HTML structure** — semantic skeleton.
4. **CSS approach** — variables for brand tokens, transition curves, reduced-motion fallback.
5. **JS modules** — timer, scorer, question renderer, persistence (localStorage), share-card generator.
6. **Feature implementations**:
   - Question types: multiple choice, true/false, matching, short answer with fuzzy grading.
   - Per-question timer with a visible arc countdown.
   - Score = base points × difficulty × speed-bonus factor.
   - Progress bar with category icon row.
   - Review mode showing correct/incorrect with explanations.
   - Leaderboard keyed by category + difficulty.
   - Results analytics: accuracy per category, average response time, suggested focus area.
   - Share card: canvas-drawn PNG with customizable message.
7. **Accessibility checklist** — keyboard nav, aria-live for timer, focus management between questions.
8. **Test plan** — 8 edge cases worth asserting.

## Constraints
- No runtime dependencies unless explicitly approved.
- Do not over-animate — two signature transitions, not twenty.
- All state must survive refresh for in-progress attempts.
- Avoid AI-aesthetic UI (floating purple gradients, generic glassmorphism). Commit to a real palette.
