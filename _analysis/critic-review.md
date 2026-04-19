# Critic Review — 222 Rewritten Prompts

## Verdict
**FAIL** · confidence 0.82

Rewrite is clean on the basics (metadata, attribution, verbatim copy) but misses the popular-skill rubric at scale. Specifically: directives #1 (named anchor), #3 (deterministic artifact), #4 (auditor framing), #5 (TRIGGER/SKIP block) are under-applied in 6 of 10 categories. The hub looks like "structured ChatGPT prompts" not "2026 agent skills" — exactly the gap the rewrite was meant to close.

Tier-5 categories (engineering, research) that should be strongest are split: research averages 61% directive compliance (best in class), but engineering averages only 33% — the highest-demand category is one of the weakest.

## Scores (0-10 per failure mode)

| # | Mode | Score | Sample | Key findings |
|---|------|-------|--------|--------------|
| 1 | Verbatim copy risk | **9** | 12 random + signature-phrase scan on all 222 | Only 2 signature-phrase carryovers found (`do not write explanations` in `engineering/sql-terminal-simulator.md:38` and `business/behavioral-interview-simulator-star-method.md`). Shingle overlap on detected source-pairs 0–6.9%. Rewrite is substantial. |
| 2 | Pattern miss | **4** | All 222 scored on 5 directives | Aggregate directive compliance avg 41%. `trigger_block` hit only 33/222 (15%). `auditor_framing` hit only 79/222 (35%). Engineering category hits 4% on trigger, 16% on auditor — core rewrite goal missed. Only 1 file of 222 (`research/defect-risk-auditor-for-code-and-agents.md`) hits all 5 directives. |
| 3 | AI-slop phrases | **9** | Full-repo grep on 8 banned phrases | 5 raw hits, 4 are false positives (phrases quoted INSIDE guardrails telling model NOT to use them). Only 1 real usage: `business/budget-travel-route-planner-multimodal.md:15` uses "leveraging layovers" unironically. Clean overall. |
| 4 | Structural inconsistency | **7** | All 222 section-header scan | 16/222 (7.2%) miss a required section. Worst: `business` (8 misses) and `career` (6). Most common gap: `Inputs` (12 files) and `Output` (9). Several are intentionally section-less image-generation briefs (`holiday-portrait-edit`, `rainy-window-cinematic-portrait`) which is a rewrite-shape decision, not a bug, but still violates the stated SPEC. |
| 5 | Broken metadata | **10** | YAML parse on all 222 | 0 YAML errors. 0 category mismatches. 0 missing required keys. Metadata pipeline is solid. |
| 6 | Attribution leak | **10** | Grep for 6 attribution patterns | 0 hits on `awesome-chatgpt-prompts`, `prompts.chat`, `PlexPt`, `dair-ai`, source URLs. The one `contributor` match (`writing/codebase-wiki-generator.md:15`) is legit product copy ("new contributor can read in 20 minutes"), not credit. |

## Must-fix list (blockers before ship)

1. **Pattern miss is the primary FAIL.** Directive #5 (TRIGGER/SKIP / when-to-use / when-NOT-to-use header) appears in only 15% of files. This is the single biggest driver of `find-skills`-style routing and was explicitly in the rewrite brief. Fix: add a standardized `## When to Use` / `## Skip When` block to every prompt, or add it as a frontmatter key (`triggers:` + `skip_when:`).

2. **Engineering category is off-brand for the rubric.** 33% directive compliance in the category that maps to cluster #1 (Frontend/React best practices, 73 of top-200 skills). Rewrite kept too many "I am a Linux terminal simulator" roleplay prompts (`terminal-simulator-for-shell-learning.md`, `javascript-console-simulator.md`, `python-interpreter-simulator.md`, `dax-terminal-simulator.md`, `sql-terminal-simulator.md`, `chemistry-reaction-vessel-simulator.md`) — these are low-install shapes per the popular-patterns analysis. Either promote them to auditor framing ("simulate + also critique the commands the user types") or move them to a `legacy/roleplay` subfolder.

3. **16 files missing required sections** per the rewrite SPEC. Locations:
   - `career/legacy-ats-scanner-simulator.md` missing Inputs, Output
   - `career/strategic-resume-customizer-with-de-risking-audit.md` missing Objective, Inputs, Output (uses Phase 1/2/3/4 structure instead — good content but violates SPEC)
   - `business/ai-strategy-consultant-10-prompt-playbook.md` missing Inputs, Output
   - `business/code-snippet-manager-spec-builder.md` missing Inputs, Output
   - `business/product-manager-advisor-strategy-roadmap.md` missing Inputs, Output
   - `business/product-manager-prd-writer-kpi-driven.md` missing Inputs, Output
   - `business/holiday-portrait-edit-warm-festive.md` missing Inputs, Constraints
   - `business/rainy-window-cinematic-portrait-prompt.md` missing Inputs, Constraints
   - plus 8 more with single-section gaps
   Decide: either enforce the SPEC's required-section list, or update the SPEC to allow "Phase"-style and "image-brief"-style variants. Pick one.

4. **Marketing-seo deterministic artifact miss: 72% of files (18/25) lack a concrete artifact spec** (table, JSON, Mermaid, diff). The category that should dominate on rubric #3 (`azure-resource-visualizer`-style) has the second-worst artifact coverage. Example: `marketing-seo/seo-article-outline-builder.md`, `marketing-seo/linkedin-outreach-generator.md`, `marketing-seo/social-media-manager-operating-system.md`.

5. **Slug collision:** `productivity/professional-email-composer.md` and `writing/professional-email-composer.md` share the same slug with different content (~2KB vs ~2.5KB). Will break any URL generation that assumes slug-unique. Rename one (e.g., `writing/professional-email-composer-tone-locale.md`).

## Should-fix list (nice-to-have)

- Engineering and creative drop below 35% named-anchor compliance. Add a named framework/method to the title (not just "Senior Code Reviewer" but "Senior Code Reviewer — SOLID+OWASP Rubric v2026").
- `business/budget-travel-route-planner-multimodal.md:15` uses "leveraging" — replace with "using" or "stacking".
- Marketing-seo and productivity get 100% numbered-checklist coverage but the checklists are rarely scored. Convert numbered "1-5 steps" into numbered "1-10 rubric items with 0/1/2 scoring".
- Only 7 files in `health-life`. Either retire the category or commit to filling it to 15-25 to match the rest. Half-built categories look abandoned.
- Engineering has multiple roleplay/simulator prompts (6+) that don't fit 2026 agent-skill demand. Consolidate into one `engineering/terminal-simulator-collection.md` and repurpose the slots for code-review/harden/validate prompts.

## Best-of examples (3 strongest)

1. **`research/defect-risk-auditor-for-code-and-agents.md`** — the only file hitting all 5 directives. Named rubric ("six defect categories"), numbered checklist, deterministic artifact (explicit `TODO_defect-risk-audit.md` file spec with diff block), auditor framing in the title, severity taxonomy. This is the template every other prompt should match.

2. **`research/thesis-literature-gap-auditor.md`** — proper auditor framing ("doctoral-level reviewer whose job is to stop students"), tiered source table, triangulation rule (3-signal gap-claim requirement), explicit limitations section, unknown-handling clause. This is what "research" as a 2026 skill category should look like.

3. **`career/strategic-resume-customizer-with-de-risking-audit.md`** — despite failing the section SPEC, substantively the most specific prompt in `career/`. Multi-phase structure, explicit banned-verbs list, word-count budgets, before/revised format discipline, measurable success bar (≥85%). Keep the content, just add the SPEC sections.

## Worst-of examples (3 weakest)

1. **`engineering/terminal-simulator-for-shell-learning.md`** — roleplay prompt that hits 0/5 directives. No named framework, no rubric, no artifact shape beyond "fenced code block", no auditor framing, no trigger block. Additionally contains `"as an AI"` inside a guardrail quote — which is fine but the surrounding shape is exactly the pre-2026 "I want you to act as" template the rewrite was supposed to replace.

2. **`engineering/senior-frontend-react-scaffolder.md`** — 0/5 directives hit in the category that should map most directly to `vercel-react-best-practices` (rank #2 all-time installs, 256K). Should have named anchor ("React 19 + Next 15 + RSC patterns"), numbered rule checklist, concrete deliverable (file tree + diff), and audit framing. Doesn't.

3. **`business/rainy-window-cinematic-portrait-prompt.md`** — image-gen brief with no Inputs section, no Constraints section, no framework anchor. Pretty copy, wrong shape for an agent-skill hub. Either accept a separate `image-briefs/` subcategory shape-spec or rewrite.

## Rewrite verdict per category (1-10)

| Category | Score | Notes |
|----------|-------|-------|
| research | 7 | Best category. Strong auditor framing (48%), high numbered-checklist (72%), 88% artifact coverage. Trigger blocks weak (28%). |
| productivity | 6 | 100% numbered-checklist, 52% auditor, but only 36% artifact and 8% trigger. Feels like clean prompts, not agent skills. |
| career | 6 | Solid individual prompts, weak shape variance (phase-based instead of SPEC-compliant). 13% trigger coverage. |
| business | 5 | 41% avg compliance. 8 SPEC-breaking files. Image-briefs and multi-module playbooks force the SPEC. |
| marketing-seo | 5 | 100% numbered-checklist but only 24% artifact — rubric violated. Category where `seo-audit`/`content-strategy`-style artifact discipline should be the default. |
| health-life | 5 | Only 7 files. Too thin to rank. What's there is competent. |
| learning | 4 | 84% artifact (unusually high) but 20% numbered-checklist and 12% trigger. Fine prose prompts, not skill-shaped. |
| writing | 4 | 56% numbered-checklist, 16% audit, 8% trigger. "Writing" should lean into audit-framing (review my draft) per directive #4 and doesn't. |
| engineering | 3 | **Worst Tier-5 category.** 33% avg. 15+ prompts missing 3+ directives. Roleplay-heavy. Directly contradicts cluster-1 popularity analysis. |
| creative | 3 | 31% avg. 16% audit, 20% named-anchor. Creative-writing prompts are hardest to skill-ify — but that's exactly the recommendation: pivot them to "critique / score my creative draft" framing or drop the category per popular-patterns Tier-3 guidance. |

## Evidence log

- Scan script results: metadata 0 errors on 222 files; attribution 0 leaks; signature-phrase carryover 2 hits; section-SPEC 16 misses; rubric-compliance matrix in body above.
- Source CSV used: `/Users/lich/ws/oss/prompt/prompts.chat/prompts.csv` (98616 lines, CC0).
- Pattern rubric: `/Users/lich/ws/oss/GPT-Prompt-Hub/_analysis/popular-patterns.md` directives 1–5.

