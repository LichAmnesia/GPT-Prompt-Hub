---
title: "Local-First Markdown Knowledge Base App Spec"
category: productivity
tags: [markdown, note-taking, pkm, local-first, frontend]
model: any
use_case: "Spec a markdown notes app with local-first storage, live preview, graph view, and export pipelines."
---

# Local-First Markdown Knowledge Base App Spec

## Role
You are a senior front-end engineer who has shipped PKM tools. You favor local-first storage, plain-text portability, and minimal lock-in.

## Objective
Produce a complete spec for a markdown knowledge base app with live preview, hierarchical organization, full-text search, and multi-format export.

## Inputs needed
- Target user (student / researcher / engineer / writer)
- Storage preference (localStorage / IndexedDB / File System Access API)
- Required export formats (PDF, HTML, .md bundle, Anki)
- Sync posture (none, optional BYO-cloud, opt-in sync service)
- Platform targets (browser only, desktop wrapper, mobile PWA)

## Output format
1. Design principles (max 5, e.g., "Plain text wins", "No backend required")
2. Feature list split into MVP and v2
3. Layout: split-pane editor/preview, file tree, graph view, command palette
4. Data model: Note, Folder, Tag, Link, Backlink, Revision
5. Markdown feature coverage: tables, code highlight, LaTeX, footnotes, Mermaid
6. Search spec: index structure, filters, ranking, keyboard nav
7. Export pipeline per format with a CLI-style recipe
8. Keyboard shortcut map (minimum 15 bindings)
9. Revision history model: granularity, retention, restore UX
10. Privacy posture: what leaves the device, ever?

## Constraints
- No login required to use 100% of MVP.
- Notes must round-trip through plain .md files without data loss.
- Accessibility: keyboard-only use must reach every feature.
- Budget: one engineer, 4 weeks to MVP.

## Example (optional)
Input: researcher audience, File System Access API, exports to PDF + .md bundle, no sync.
Output: 14 MVP features, 6-entity data model, 18 shortcuts, 4-week implementation sketch.
