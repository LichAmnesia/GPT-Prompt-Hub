# Plagiarism scan — v2 independent

Script: `/tmp/plag_scan.py`
Output JSON: `/tmp/scan_out.json`
Method: 5-gram containment overlap (hub file ∩ source) + longest common substring (60+ char) against all 1662 rows of `prompts.csv`.
Scanned: 222 rewritten files (legacy excluded).

## Top-20 overlap scores

| Rank | Hub file | Overlap % | LCS chars | Matched source |
|---|---|---|---|---|
| 1 | career/strategic-resume-customizer-with-de-risking-audit.md | 14.43 | 64 | Resume Customization Prompt – STRATEGIC INTEGRITY (Scott M.) |
| 2 | engineering/dax-terminal-simulator.md | 13.82 | 77 | DAX Terminal |
| 3 | career/job-posting-archival-snapshot-engine.md | 12.63 | 74 | Job Posting Snapshot & Preservation Engine (Scott M.) |
| 4 | research/lightweight-functional-analyst-mode.md | 10.38 | 101 | Small Functional Analyst mode |
| 5 | writing/taglish-narrative-explainer.md | 10.34 | 88 | Taglish Technical Storytelling Editor |
| 6 | research/senior-functional-analyst-phased.md | 9.74 | 80 | Functional Analyst |
| 7 | marketing-seo/q1-systematic-review-article-design.md | 8.74 | 114 | Diseño de Artículo de Revisión Sistemática… |
| 8 | career/legacy-ats-scanner-simulator.md | 7.89 | 89 | ATS Resume Scanner Simulator (Scott M.) |
| 9 | research/career-competency-excavation-interview.md | 7.85 | 208 | Career Intelligence Analyst |
| 10 | business/rainy-window-cinematic-portrait-prompt.md | 6.16 | 0 | Through the Glass: One Eye in Focus |
| 11 | marketing-seo/seo-fundamentals-2026.md | 5.91 | 99 | seo-fundamentals |
| 12 | writing/multi-audience-codebase-onboarding-doc.md | 5.00 | 69 | Multi-Audience Application Discovery… |
| 13 | creative/meat-egg-category-expert-qa.md | 4.91 | 140 | Professional Buyer Q&A Creator |
| 14 | business/holiday-portrait-edit-warm-festive.md | 4.85 | 0 | Cozy Christmas Smile |
| 15 | writing/project-aware-prompt-architect.md | 4.57 | 89 | Prompt Writer for Specific Project |
| 16 | career/universal-job-fit-evaluator.md | 4.56 | 129 | Universal Job Fit Evaluation Prompt |
| 17 | career/real-time-job-scout-scanner.md | 4.53 | 0 | Customizable Job Scanner |
| 18 | marketing-seo/ad-powershell-disabled-users-script.md | 4.27 | 0 | PowerShell Script for Managing Disabled AD Users |
| 19 | writing/codebase-wiki-generator.md | 4.24 | 0 | Codebase WIKI Documentation Skill |
| 20 | research/bibtex-normalizer.md | 3.99 | 83 | Academic Research Writer |

## Interpretation

- **Pure verbatim copy**: ZERO files. No file contains a continuous >200-char verbatim block.
- **Technical-vocabulary overlap (acceptable)**: DAX (rank 2), Functional Analyst (4,6), SEO (11). Overlap is dominated by domain vocabulary (table names, UML2/Gherkin/BPMN, E-E-A-T, Core Web Vitals). Legitimate.
- **Structural / branded-IP clones (PROBLEM)**: Rank 1, 3, 8 all trace to "Scott M." in `prompts.csv`. They:
  - Preserve proprietary section names ("De-Risking Audit", "Real Problem", "Risk Profile", "Language Mirror", "99% Trap", "Sinker", "God-Mode Writing Rules", "Insider Cover Letter", "Multi-Persona Audit", "Scanner Sinker", "Synonym Trap", "AI Stealth").
  - Preserve exact scoring weight systems, 4-phase ordering, and signature rules ("1:1 Metric Rule", "Before Test", "Active Kill-Switch", "Eye-Tracking").
  - Paraphrase the surface text but clone the IP architecture.
  - Anyone familiar with Scott M.'s posted prompts will recognize them. Attribution stripped.
