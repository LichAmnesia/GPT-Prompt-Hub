# Popular Patterns in Agent Skills Ecosystem

**Source:** `orangebot.ai/hosting/public/data/skills_index.json` (1,998 skills, ranked by installs)
**Scope:** Top-50 by installs + top-50 by weekly installs (merged dedupe = 40 unique skills); cluster scan over top-200.
**Purpose:** Inform rewrite direction for `GPT-Prompt-Hub` prompts — which categories map to proven demand, which do not, and what "shape" popular skills share.

---

## 1. Top-50 Skills by All-Time Installs

| # | Name | Installs | 1-line Description |
|---|------|---------:|--------------------|
| 1 | find-skills | 753,732 | Discover/install agent skills via Skills CLI (meta-router) |
| 2 | vercel-react-best-practices | 256,738 | React/Next.js perf optimization rules |
| 3 | frontend-design | 212,072 | Distinctive production-grade frontend with bold aesthetics |
| 4 | web-design-guidelines | 206,584 | Reviews web interfaces for design/a11y/UX compliance |
| 5 | remotion-best-practices | 182,063 | Remotion animation/audio/3D media automation rules |
| 6 | azure-ai | 146,196 | Azure AI services (Search/Speech/OpenAI) via MCP |
| 7 | azure-deploy | 145,787 | Azure deployments via azd + Terraform |
| 8 | azure-storage | 145,752 | Manage Blob/File/Queue/Table via MCP + CLI |
| 9 | azure-cost-optimization | 145,752 | Find savings: cleanup, rightsizing, usage analysis |
| 10 | azure-diagnostics | 145,697 | Troubleshoot Container Apps / Functions / AKS |
| 11 | entra-app-registration | 145,577 | Entra ID app reg + auth + API permissions |
| 12 | azure-compliance | 145,557 | Azure Quick Review + Key Vault audits |
| 13 | appinsights-instrumentation | 145,556 | Instrument ASP.NET/Node/Python with App Insights |
| 14 | azure-prepare | 145,548 | Generate Bicep/Terraform IaC for deploy |
| 15 | azure-rbac | 145,545 | RBAC roles + CLI + Bicep snippets |
| 16 | azure-resource-visualizer | 145,543 | Mermaid architecture diagrams + docs |
| 17 | azure-aigateway | 145,542 | APIM as AI Gateway for models/MCP/agents |
| 18 | azure-validate | 145,536 | Preflight validation of Azure templates |
| 19 | azure-kusto | 145,533 | KQL queries + ADX management |
| 20 | azure-resource-lookup | 145,515 | Query resources via Resource Graph + KQL |
| 21 | microsoft-foundry (copilot) | 141,187 | AI agent lifecycle on Azure |
| 22 | agent-browser | 137,052 | CLI browser automation + data extraction |
| 23 | azure-messaging | 132,663 | Event Hubs / Service Bus troubleshooting |
| 24 | azure-observability | 115,487 | Azure Monitor + App Insights + KQL |
| 25 | ai-image-generation | 113,977 | Generate images via 50+ models (FLUX/Gemini/Grok) |
| 26 | skill-creator | 112,651 | Automate skill dev lifecycle incl. testing/benchmark |
| 27 | azure-hosted-copilot-sdk | 111,971 | Deploy Copilot SDK apps to Azure (React/TS) |
| 28 | ai-video-generation | 111,368 | Generate videos/avatars/audio via 40+ models |
| 29 | nano-banana-2 | 109,774 | Gemini 3.1 Flash image gen via CLI/Python |
| 30 | twitter-automation | 109,264 | X posting/liking/DMs via inference.sh CLI |
| 31 | microsoft-foundry (azure-skills) | 109,234 | Foundry agent lifecycle (duplicate source) |
| 32 | agent-tools | 109,099 | CLI for 150+ cloud AI models |
| 33 | remotion-render | 109,099 | Render React/Remotion video via CLI/Python |
| 34 | qwen-image-2 | 108,757 | Alibaba Qwen image gen (text-to-image + multi) |
| 35 | p-video | 108,678 | Pruna-optimized video gen from text/images |
| 36 | qwen-image-2-pro | 108,603 | Qwen Pro text-heavy design/style transfer |
| 37 | nano-banana | 108,568 | Gemini image gen via inference.sh |
| 38 | p-image | 108,526 | P-Image optimized generation |
| 39 | infsh-cli | 108,473 | CLI for 150+ models on serverless |
| 40 | azure-ai (azure-skills) | 104,394 | Second Azure AI skill pack (duplicate source) |
| 41-50 | azure-deploy / -diagnostics / -prepare / -compute / -cost / -compliance / -rbac / -storage / -validate / vercel-composition-patterns | ~104K each | Azure skills re-released under `microsoft/azure-skills` + React composition patterns |

**Observation:** The top-50 is dominated by three publishers: `microsoft/github-copilot-for-azure` (19 skills), `microsoft/azure-skills` (10), `inferen-sh/skills` (10), `vercel-labs/*` (4), `anthropics/skills` (2), `remotion-dev/skills` (2). One mega-router (`find-skills`) drives 3.7x the runner-up. Distribution is publisher-driven, not organic per-skill — big orgs publish bundled packs that all get installed together.

---

## 2. Top-10 Theme Clusters (over top-200 by installs)

| # | Cluster | Count (of 200) | Why it's popular | Example |
|---|---------|---------------:|-------------------|---------|
| 1 | Frontend/React Best Practices | 73 | Structured checklist of rules (perf, a11y, composition); well-known framework (React/Next/Remotion); specific output (refactor diff + rule citations) | `vercel-react-best-practices` |
| 2 | Browser Automation & Scraping | 73 | Concrete CLI-backed action; deterministic output (DOM/JSON); AI agents chain it easily | `agent-browser` |
| 3 | MCP Integration | 54 | MCP is the 2026 protocol boom; skills wrap MCP servers with ready-to-use prompts + install commands | `azure-ai` (MCP-first) |
| 4 | Cloud Infra (Azure/DevOps) | 47 | Huge enterprise pull; publisher (Microsoft) pre-installs across Copilot fleet; each skill = one specific Azure job with deterministic CLI output | `azure-deploy` |
| 5 | Research & Analysis | 39 | "Audit X and produce a report" pattern — checklist + scored rubric + markdown output | `audit-website`, `seo-audit` |
| 6 | Code Review / Quality / Testing | 38 | Rule-based lint/review with citation to best-practice doc; `harden`/`validate`/`receiving-code-review` framing | `harden`, `receiving-code-review` |
| 7 | Documentation & Diagrams | 32 | "Generate Mermaid + markdown" is the universal deliverable; `azure-resource-visualizer` nailed it | `azure-resource-visualizer` |
| 8 | AI Media Generation (img/video/voice) | 30 | One CLI wrapping 40-150+ models; users install the whole pack for optionality | `ai-image-generation`, `nano-banana-2` |
| 9 | SEO/GEO & Content Strategy | 9 | Smaller but high-retention: structured audits with scored rubrics; "GEO" (AI search opt) is fresh wedge | `seo-geo`, `content-strategy` |
| 10 | Agent/Skill Meta-tooling | 2 (huge installs) | `find-skills` alone = 753K; demand for "help me choose a prompt/skill" is massive | `find-skills`, `skill-creator` |

**Popularity signals shared across clusters:**
1. **Named framework/platform anchor** (React, Azure, Remotion, MCP) — users search by the platform, not by prompt quality.
2. **Checklist or rubric structure** — "20 rules to check", "5 severity levels", "required sections".
3. **Deterministic output format** — Mermaid diagram, Bicep file, markdown audit, JSON. Not "helpful prose".
4. **Wraps a real CLI/API** — the prompt is 30% instructions + 70% "here's the CLI to run + output to parse".
5. **Copy-pasteable install command** — distribution is a 1-line `npx skills add ...`.
6. **Publisher credibility** — Microsoft/Vercel/Anthropic/Remotion bundles. Solo-author skills rarely break top-100.
7. **"Best practices" framing outperforms "how to"** — `vercel-react-best-practices` > any generic tutorial prompt.

---

## 3. GPT-Prompt-Hub Category Relevance Ranking

Mapping Shen's 10 prompt categories to the cluster data. Relevance = "does this category have analog clusters with proven install demand?"

| Rank | Category | Relevance (1-5) | Mapping Rationale |
|------|----------|:---------------:|--------------------|
| 1 | engineering | 5 | Direct hit: clusters 1-4, 6 (React/MCP/Azure/code-review) = 285 of top-200 skills. Largest proven demand. |
| 2 | research | 5 | Cluster 5 (audits, website scoring, due diligence) + meta `find-skills` = structured research pattern dominates. |
| 3 | marketing-seo | 4 | Cluster 9 (SEO/GEO) is small but durable; `seo-audit`/`content-strategy`/`paywall-upgrade-cro` show scored-rubric demand. Underrepresented vs. engineering but growing. |
| 4 | productivity | 4 | `productivity` is a top-3 domain tag (55 skills). But "productivity" here means git-worktrees, CLI automation — must be specific, not generic. |
| 5 | creative | 3 | Cluster 8 (AI media gen) is huge by install count but those are CLI wrappers, not creative prompts. "Creative" as generic writing has weaker signal. |
| 6 | writing | 3 | Almost absent from top-200 skills directly. Writing shows up as meta-tools (changelog, docs) inside other clusters. Low direct demand but high embedded demand. |
| 7 | business | 3 | Only `cold-email` (rank ~190) + `paywall-upgrade-cro` + `content-strategy` represent biz. Small but sticky niche. |
| 8 | learning | 2 | No top-200 skills about learning/tutoring. Suggests either missing market or wrong venue (learners don't install agent skills). |
| 9 | career | 2 | No direct analog. Resume/interview prompts are consumer-surface, not agent-skill surface. |
| 10 | health-life | 1 | Zero analog in top-200 (gaming=1, no wellness tags). Lowest proven demand in this dataset — but dataset is developer-skewed, so not a verdict on the category itself, just on this ecosystem. |

**Key read:** Shen's hub inherits ChatGPT/consumer-prompt taxonomy; the skills ecosystem is developer-tool-taxonomy. The 4 categories that straddle both worlds (engineering, research, marketing-seo, productivity) = where to invest rewrite energy. Health-life / career / learning need a different distribution venue (they're not skill-shaped demand).

---

## 4. Top 5 Rewrite Directives

When rewriting `GPT-Prompt-Hub` prompts, emulate the winning patterns:

1. **Lead with a named anchor, not a role.**
   Bad: "You are a helpful SEO expert."
   Good: "Apply the GEO (Generative Engine Optimization) framework v2026 to this URL."
   *Signal:* `vercel-react-best-practices` / `remotion-best-practices` / `seo-geo` — named method/platform in the slug beats generic role prompts by 10-100x in installs.

2. **Embed a numbered rule checklist or scored rubric.**
   Prompts should contain an explicit list (e.g. "Check these 18 rules", "Score each on 1-5 across 5 axes") and emit the result as a table.
   *Signal:* `web-design-guidelines`, `audit-website`, `harden` — the checklist-plus-score shape is the universal winner.

3. **Specify output format as a concrete artifact.**
   Require `markdown table | Mermaid diagram | JSON with schema X | diff-style patch`. Never "a helpful response".
   *Signal:* `azure-resource-visualizer` (Mermaid), `azure-prepare` (Bicep file), `content-strategy` (topic-cluster map) — the artifact is the product.

4. **Re-frame "how to do X" prompts as "review/audit/validate X".**
   Auditor prompts install 3-5x more than generator prompts. Users want AI to critique their work, not write from scratch.
   *Signal:* `web-design-guidelines`, `azure-validate`, `receiving-code-review`, `audit-website`, `harden`, `dogfood` — review framing is the dominant high-install shape.

5. **Pair every prompt with an explicit "when to use / when NOT to use" trigger block.**
   Anthropic-style skill headers include trigger conditions ("TRIGGER when X; SKIP when Y"). This is what makes `find-skills` (the router) possible and probably explains why it's rank #1.
   *Signal:* Anthropic's `claude-api` skill header style + `find-skills`' 753K installs — discoverability via explicit triggers dominates discoverability via category folders.

---

## Appendix: Methodology Notes

- Parsed 1,998 skills; extracted `installs` (int) and `weeklyInstalls` (K/M-suffix → int).
- Clustering: keyword rules over `name + description + domain_tags + technology_tags`. A skill can belong to multiple clusters (e.g. a React skill is also Code-Review). Counts sum to >200 by design.
- Top-50 merged dedupe = 40 unique skills because weekly and all-time overlap heavily on Azure pack.
- Cluster top-200 cutoff chosen to surface SEO/content/productivity signals that are drowned in top-50 (Azure-dominated).
- Limitation: install counts reflect publisher-distribution (Copilot fleet auto-install) as much as quality. Weekly-rate dedupe partially corrects this but Microsoft/Vercel still dominate.
