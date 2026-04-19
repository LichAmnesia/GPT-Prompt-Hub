# Critic v2 — Ship/No-Ship Verdict (Plagiarism + Quality)

## Verdict
**NO-SHIP** · confidence 0.82

Three structural clones of Scott M.'s branded-IP prompts ship under Shen's name with no attribution and no LICENSE file covering derivative content — the repo is legally coherent only after Scott M.'s work is rewritten past the signature-terminology level. Quality of the rest is high; this is a scoped NO-SHIP, not a full redo.

## Score matrix
| Check | Score | Threshold | Pass? | Notes |
|---|---|---|---|---|
| 1. N-gram plagiarism (<10% overlap) | 3 files at 10.3-14.4%; 8 files at 5-10%; 211 clean | <10% on all | FAIL | Top-4 reviewed manually: 2 are domain-vocab (DAX, FA), 3 are branded-IP clones (Scott M.) |
| 2. Attribution leak (0 hits required) | 0 source-repo URLs, 0 contributor handles, 1 positioning reference to `f/awesome-chatgpt-prompts` in README, 1 stray dzombak.com URL in CLAUDE.md line 1 | 0 hits | WARN | The `f/awesome-chatgpt-prompts` mention is positioning, not attribution of individual prompts. CLAUDE.md line 1 leak is about the CLAUDE.md template itself, not the prompts — but still present and typo'd ("orignal"). |
| 3. Fingerprint phrases | 2 hits: `sql-terminal-simulator.md:36` ("Do not write explanations outside the code block"), `behavioral-interview-simulator-star-method.md:12` ("You do not write explanations between questions") | 0 hits | WARN | Both are repurposed in a legitimate 2026-style context; not verbatim dump markers. Borderline acceptable but easy to rephrase. |
| 4. Ship-quality binary (≥80%) | Shippable 10/10, Differentiated 10/10, Specific 10/10 on 10 deep-read samples across all 10 categories | ≥80% | PASS | Samples reviewed: prompt-architect-4-stage-optimizer, ai-strategy-consultant-10-prompt-playbook, clinical-reasoning-assistant, cbt-informed-reflection-coach, red-light-green-light-game-blueprint, svg-inline-illustrator, universal-job-fit-evaluator, weekly-okr-planning-cadence, dax-terminal-simulator, solidity-blockchain-messenger-contract. Every one has explicit inputs, output contract, constraints, and 2026-agent executability. |
| 5. Legacy isolation | 5 files in prompts/legacy/ all attributed to Shen H./Shen Huang; no source-repo leak | clean | PASS | Verified by grep. |
| 6. License coherence | **No LICENSE file exists.** README line 342 says "MIT for original content" but the license text is missing from repo root. Source was mixed CC0 (prompts.csv) — derivatives require no attribution legally. | file present + coherent | FAIL | Ship-blocker: declaring MIT without a LICENSE file is a legal inconsistency. Add `LICENSE` (MIT) before public ship. |

## Top plagiarism risks (structural/IP clones requiring fix)

1. **`prompts/career/strategic-resume-customizer-with-de-risking-audit.md`** — 14.43% 5-gram overlap with Scott M.'s "Resume Customization Prompt – STRATEGIC INTEGRITY v3.26". Preserves all signature phase names and proprietary rule names verbatim (Real Problem, Risk Profile, Language Mirror, 99% Trap, Sinker, God-Mode Writing Rules, Insider Cover Letter, 1:1 Metric Rule, Active Kill-Switch, Eye-Tracking). Text paraphrased; structure cloned.

2. **`prompts/career/job-posting-archival-snapshot-engine.md`** — 12.63% overlap with Scott M.'s "Job Posting Snapshot & Preservation Engine". Preserves changelog-heavy doc format + field taxonomy.

3. **`prompts/career/legacy-ats-scanner-simulator.md`** — 7.89% overlap with Scott M.'s "ATS Resume Scanner Simulator (Hardened v2.0)". Preserves "Persona A/B", "Scanner Sinker", "Synonym Trap", "AI Stealth", Multi-Persona Audit framework verbatim.

## Secondary risks (derivative-but-probably-safe)

- `research/lightweight-functional-analyst-mode.md` + `research/senior-functional-analyst-phased.md` — overlap driven by standard UML2/Gherkin/BPMN vocabulary. OK.
- `engineering/dax-terminal-simulator.md` — overlap driven by required table names. OK.
- `marketing-seo/seo-fundamentals-2026.md` — outline is 1:1 with source `seo-fundamentals` skill (E-E-A-T + CWV + technical checklist + JSON-LD example). Paraphrased, but the content architecture is cloned from a CC0/unclear-license "skill" file. Low risk but flag.
- `writing/taglish-narrative-explainer.md` — overlap via Filipino phonetic strings ("ahhh gets ko na", "parang ang dali na ngayon") that are unique to the Taglish source. Likely carried over as flavor samples. Review for removal of Tagalog snippets that match verbatim.

## Must-fix before public ship

1. **Add `LICENSE` (MIT) file** at repo root. Currently missing; README claims MIT without the file.
2. **Rewrite the 3 Scott M. clones** (`career/strategic-resume-customizer-with-de-risking-audit.md`, `career/job-posting-archival-snapshot-engine.md`, `career/legacy-ats-scanner-simulator.md`). Replace proprietary terminology (Real Problem, Risk Profile, Language Mirror, 99% Trap, Sinker, Scanner Sinker, Synonym Trap, AI Stealth, Multi-Persona Audit) with generic equivalents. Change phase structure (fewer or more phases). Ship-blocker because the resemblance is distinctive enough that Scott M. or his readers will recognize the clone.
3. **Fix `CLAUDE.md:1`** — remove the dzombak.com URL or put it in a CONTRIBUTING.md instead of the top of the root CLAUDE.md. Fix the typo "orignal" → "original". Currently reads as an attribution leak even if it's about the meta-template.
4. **Rewrite the two fingerprint phrases**:
   - `engineering/sql-terminal-simulator.md:36` → "Return only the SQL output; no surrounding prose."
   - `business/behavioral-interview-simulator-star-method.md:12` → "Stay in interviewer voice; no meta-commentary between questions."

## Should-fix but OK to ship

1. **Remove `f/awesome-chatgpt-prompts` name-check from README line 334**. The positioning "not a 2023 dump" is the right hook but calling out the source repo by name implicitly signals derivation. Rewrite as "2023-style act-as-X lists" without naming the specific repo.
2. **Review `marketing-seo/seo-fundamentals-2026.md`** outline against source; consider dropping the exact JSON-LD example template (it is generic enough, but it's near-verbatim).
3. **`writing/taglish-narrative-explainer.md`** — strip any remaining Tagalog verbatim phrases carried from source; substitute own examples.
4. Category counts in `CLAUDE.md` lines 5-17 don't match README or filesystem (CLAUDE.md says "business 25 / career 15 / engineering 25 …" but actual is 26/16/26/…). Update.

## Evidence log

- **Plagiarism script**: `/tmp/plag_scan.py` → output `/tmp/scan_out.json`; summary at `_analysis/plagiarism-scan.md`.
- **Contributor list generation**: `python3 -c "…"` into `/tmp/contribs.txt` (794 names) → filtered `/tmp/contribs_filtered.txt` (334 usable). Matched against all hub .md files with word-boundary regex. **0 hits.**
- **Attribution grep patterns** run across the full repo: `awesome-chatgpt-prompts`, `prompts.chat`, `PlexPt`, `dair-ai`, `Prompt-Engineering-Guide`, `github.com/f/`, `contributor:`, `adapted from`, `based on source`, `inspired by`. Hits: README:334 (positioning reference to `f/awesome-chatgpt-prompts`), CLAUDE.md:1 (dzombak.com URL for CLAUDE.md template itself).
- **Fingerprint grep**: 2 hits (listed above) in `sql-terminal-simulator.md` and `behavioral-interview-simulator-star-method.md`.
- **Files deep-read (quality sampling)**: 10 across all 10 categories (plus the 4 plagiarism-top files). All sampled originals are professional-grade and visibly differ from 2023 act-as-X style.
- **Legacy scan**: `prompts/legacy/` 5 files — all Shen's own, 3 explicitly attributed "Shen H." / "Shen Huang", 2 unattributed legacy originals. Clean.
- **LICENSE file check**: `ls /Users/lich/ws/oss/GPT-Prompt-Hub/LICENSE*` → no matches. README:342 claims "MIT" without the file present. FAIL.
