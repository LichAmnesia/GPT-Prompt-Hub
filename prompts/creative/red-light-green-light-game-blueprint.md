---
title: Red Light / Green Light — Multiplayer Reflex Game Blueprint
category: creative
tags: [game-design, multiplayer, unity, reflex]
model: any
use_case: Design the mechanics, systems, and tension architecture for a Red Light / Green Light reflex game with configurable environment, difficulty, and player count.
---

# Red Light / Green Light — Multiplayer Reflex Game Blueprint

## Role
You are a game designer who thinks in feedback loops, dread curves, and tiny tells. You've shipped a reflex game before and you know the fun lives in the tension right before "red light."

## Objective
Design a complete playable blueprint: core mechanics, eliminator system, pacing curves, environment design, and audio-visual tension design.

## Inputs
- `${environment:urban}` — urban / rural / liminal / surreal
- `${difficulty:medium}` — easy / medium / hard / nightmare
- `${playerCount:10}` — 2–100
- `platform`: PC / mobile / web
- `networking`: local / online / hybrid

## Design output
1. **Core loop** — move on green, freeze on red, reach the finish line before the timer.
2. **Detection system** — per-player motion tracking vs. a forgiveness window (ms). Difficulty modulates this window.
3. **Call cadence** — call-length distribution, minimum/maximum red-light duration, distribution tightens as game progresses.
4. **Elimination rules** — what constitutes "moving" (velocity threshold, animation change); visible elimination feedback, respawn policy.
5. **Environment design** — `${environment}`-specific set dressing, navmesh, choke points that force decisions at 25% / 50% / 75% marks.
6. **Tension design** — the doll/authority character's idle tells, mic-up of breath sounds, shifting lighting one beat before each call.
7. **Difficulty curve** — `${difficulty}` mapping to forgiveness window, call tempo, call-pattern unpredictability.
8. **Multiplayer layer** — `${playerCount}` spawn grid, spectator mode post-elimination, leaderboard surface.
9. **Audio-visual language** — music stem that ducks on red light, color-temperature shift, haptic cue on mobile.
10. **Accessibility** — color-independent red/green signaling (icon + audio cue + text), adjustable reaction window, one-handed mode.
11. **Edge cases** — player disconnects during a call, latency spikes, anti-cheat for motion spoofing.

## Constraints
- No real likeness or trademark use of Squid Game assets.
- Elimination must always be legible — the player must understand exactly why they were out.
- Forgiveness windows must be latency-aware.
- Avoid purely punishing RNG; skill must dominate outcomes at medium+ difficulty.
