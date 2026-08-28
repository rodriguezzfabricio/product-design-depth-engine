# Ledger (Tier 1) — append-only

> The immutable record of this run. Append one entry per action / finding / decision / null-result. Never edit or delete a prior entry (L-B). Entry format:
>
> ```
> L-NNNN
> Date: YYYY-MM-DD
> Type: action | finding | decision | null-result | correction
> <content that lets a fresh context reconstruct what happened and why>
> ```
>
> Load-bearing entries also carry a `Decided at: ~Xk context` line; a high-context decision is provisional until reproduced cold (L-C).

---

L-0001
Date: 2026-08-28
Type: action
E0 intake. Seed captured verbatim to `artifacts/seed.md` with 11 numbered asks (A1–A11) extracted for coverage tracking. Attachment `Depth Engine Meta-Run.pdf` preserved as `artifacts/source_meta_run.pdf` + extracted text. Prior in-repo report `research/2026-08-26-harness-upgrade/REPORT.md` preserved as `artifacts/source_prior_report.md`. Run root is a NEW git repo `product-design-depth-engine`, created this session and pushed to `rodriguezzfabricio/product-design-depth-engine` (private) per ask A11.

L-0002
Date: 2026-08-28
Type: finding
The PDF is NOT a feature specification. Operator hedged ("Not sure if it describe features in the pdf"). Actual content: a lossless meta-run seed dated 2026-08-26 — 8 observed failures (F1–F8), 7 operator-proposed mechanisms (M1–M7), 6 standing rules (R1–R6), 10 external targets (T1–T10), a 10-row claims ledger, a 12-row decode log, and 4 gates blocked on the operator (G1–G4). Implication for this run: UI requirements must be DERIVED from F1–F8 and M1–M7, not read off a feature list. Extraction required a venv + pypdf; poppler is absent on this machine.

L-0003
Date: 2026-08-28
Type: finding
Repo recon (ask A1), source `~/.depth-engine/repo`. The engine is a methodology, not a running program: 12 stage files (E0–E11), 5 law files (L-A–L-E), 5 protocol files, 4 memory templates, and a ~4-file Node CLI (`src/cli.js`, `init.js`, `start.js`, `files.js`) whose only job is to copy assets and create a per-run directory. Nothing executes during a session; nothing can block. Run state = 4 Markdown files: LEDGER (append-only), STATE (resume snapshot), INDEX (TOC), REGISTER (coverage register, drives E8 convergence). This is the schema any UI must render.

L-0004
Date: 2026-08-28
Type: finding
**Gate G1 from the PDF is CLEARED.** The PDF recorded codex as "Verified still logged out on 2026-08-26," which made every verdict in that run same-family. On 2026-08-28 `codex exec --skip-git-repo-check` returned the requested sentinel. Cross-family L-A checks are available for this run. Note: codex requires `--skip-git-repo-check` or a trusted directory; a bare invocation fails with "Not inside a trusted directory."

L-0005
Date: 2026-08-28
Type: finding
The operator's suggested command `npx skills add https://uizze.com/` DOES NOT WORK. `git ls-remote https://uizze.com/` → "fatal: repository 'https://uizze.com/' not found". `npx skills add` clones a git remote; uizze.com is a marketing site (200 in a browser, but /skills.json, /.well-known/skills.json, /api/skills all 404). Correct command: `npx skills add uizze/uizze`. The skill itself is real, MIT-licensed, and substantively good — design contract written to disk, 9 required states, a finish gate. Operator's instinct validated; his address was wrong.

L-0006
Date: 2026-08-28
Type: finding
Registry install counts are not credible as adoption. `skills.sh` reports 532,461 installs for `uizze.com/anti-ui-slop`; the backing repo `uizze/uizze` has **12 stars**, created 2026-07-15. Third instance of this pattern in the operator's own records (PDF C4: Scrapling "74k" → ~33k; PDF C6: ECC "16k" → 117k+). Standing rule adopted for this project: rank tools by reading them, never by a registry number.

L-0007
Date: 2026-08-28
Type: finding
The operator already has 8 relevant design skills installed and unused: `design-consultation`, `design-html`, `design-review` (explicitly targets "AI slop patterns"), `design-shotgun`, `plan-design-review` (all gstack), plus `artifact-design`, `dataviz`, and `humanizer`. `humanizer` is M4/F8 already on disk. This is the fourth occurrence of the correction logged three times in the prior report §8 ("things D1 plans to build that already exist"). Per that report, a lesson relearned per batch is a missing protocol step, not an insight — candidate engine change: a mandatory "inventory existing capability" step before any tooling recommendation.

L-0008
Date: 2026-08-28
Type: finding
Design-canon URLs verified reachable (HTTP 200, 2026-08-28, curl with browser UA): nngroup ten-heuristics, marketingexamples.com, lawsofux.com, refactoringui.com, linear.app/method, basecamp.com/shapeup, vitsoe good-design, asktog principles, docs.cursor.com/background-agent, anthropic claude-code-best-practices. Nielsen page read in full: 10 heuristics, author Jakob Nielsen, last updated 2024-01-30. Heuristics #1 (visibility of system status), #6 (recognition not recall), #8 (aesthetic and minimalist) map directly onto F3, the paste-to-another-chat ritual, and the "no random buttons" constraint respectively.

L-0009
Date: 2026-08-28
Type: finding
Linear growth mechanism, primary-grade (Sequoia spotlight + Figma interview + linear.app/method). Founded Jan 2019, profitable Jul 2021, no waitlist or launch campaign; found by Sequoia via Twitter. Growth driver: internal "revolts" — ICs refusing management-mandated tools, including a full memo from Sequoia's own teams. Design principles: "there's one really good way of doing things"; flexible software creates chaos at scale; deliberate product debt accepted in settings to strengthen the core; dark gray sans-serif on black, "inspired by coding environments engineers prefer." Relevance: the operator's A8 constraint (no random buttons/dropdowns, minimal friction) is the documented growth mechanism of the most design-respected tool in the category, not a stylistic preference.

L-0010
Date: 2026-08-28
Type: null-result
Could NOT verify any AI-company growth figure at primary grade. Built-in web search returned 9 results for the growth query, ~7 SEO listicles, several vendor-published and self-ranking (e.g. lovable.dev guides ranking Lovable first). Quarantined as UNVERIFIED in `research/03-market-and-business.md` §4: Lovable $100M ARR/8mo; Lovable $200M ARR/$6.6B; Replit $10M→$100M/9mo; $15B/yr dev spend; 84% adoption; Bolt 28min/Lovable 35min/Replit 45min. This is standing rule R3 earning itself again — Scrapling StealthyFetcher (v0.4.15, in the run venv) is the documented upgrade path and was NOT used this pass. Recorded as an honest negative, not smoothed over.

L-0011
Date: 2026-08-28
Type: correction
**L-A cross-family verdict: OVERTURNED.** Claim 1 was: "the Depth Engine should not be designed like Cursor — Cursor is an editor, this is a long-running run, so the precedents are CI/CD views and trace viewers, not an IDE." Codex overturned it: Cursor Background Agents are asynchronous runs users launch, leave, monitor, redirect and review, with status/diffs/PR handoff on web and mobile; GitHub Copilot's coding agent turns an issue into an autonomous run reviewed as a PR. Codex: "Making RUN the data model is sensible; concluding 'therefore not Cursor-like' is not… Separating run supervision from the editor could create a costly context switch exactly when users must inspect, edit, test, and accept the result." Surviving fragment: RUN is still the correct primary object. Revised position: run-first WITHOUT giving up code/diff inspection; study Cursor Background Agents as nearest precedent. The operator's original "like Cursor" instinct was closer to correct than the engine's correction to it.
Decided at: ~110k context — provisional until reproduced cold (L-C).

L-0012
Date: 2026-08-28
Type: correction
**L-A cross-family verdict: OVERTURNED.** Claim 2 was: "F1–F8 are enforcement failures not presentation failures, so a UI would be a skin over the same problems and the enforcement layer must be built first." Codex: a sound warning wrapped around a false absolute. A GUI directly improves F5 (structured file-level diffs), F4 (display requested vs actually selected model), F7-tracking (live token/cost accounting), F3 (elapsed-time, last-event, heartbeat). Counterexample cited: LangSmith's trace UI delivers observability — latency, errors, token consumption, cost — without becoming the execution runtime, and before/independently of binding workflow controls. Codex: "'enforcement layer first' is an unnecessary sequencing constraint. Instrumentation plus a thin run UI could validate which controls users actually need." Surviving narrow claim: a UI cannot GUARANTEE stopping, liveness, routing, or budget caps. Consequence: build the UI first, as instrumentation. Both cited doc URLs (docs.cursor.com, docs.langchain.com) are UNOPENED by this run — flagged for verification.
Decided at: ~110k context — provisional until reproduced cold (L-C).

L-0013
Date: 2026-08-28
Type: decision
Following L-0011/L-0012, F1–F8 are split into two halves and the split is the product plan. OBSERVABILITY HALF (a UI fixes these, ship now): F3 heartbeat/last-event, F4 requested-vs-actual model panel, F5 file-level diffs, F7 cost meter (tracking only), F8 humanized copy with raw toggle. ENFORCEMENT HALF (a UI cannot fix these, needs code that runs): F1 stopping point, F2 adaptive thoroughness, F7 blocking budget cap. Five of eight are surface-fixable = a real first release. Guard recorded: the cost meter must not imply a cap that does not exist — that would be a fail-open gate wearing a fail-closed label, the exact defect the prior report logged as X-004.

L-0014
Date: 2026-08-28
Type: finding
Answer to the operator's "I don't know what to display": the data model already exists and he authored it. One-to-one mapping — REGISTER.md → coverage bar with a closed denominator; LEDGER.md → timeline/audit feed; STATE.md → persistent "where am I" header; INDEX.md → navigation/search; stages E0–E11 → pipeline rail with gates rendered as gates; L-A verdicts → survived/challenged/inconclusive badges; three terminals → outcome card. The REGISTER is the hero object: prior report §5.1 established that convergence must be coverage over a closed list because the softmax has no null entry, and a closed list with per-row status is exactly a progress bar that can honestly reach 100%. Competitors show spinners because they cannot name a denominator. UNCHALLENGED by cross-family check — under L-A its cleanness warrants MORE scrutiny, not less.

L-0015
Date: 2026-08-28
Type: action
E1 MOVE 1–2 complete; four research artifacts written to `research/` (01 tooling audit, 02 what-to-display, 03 market-and-business, 04 design-canon). Intent Brief DRAFTED to `artifacts/intent_brief.md` with provenance tags on every line. Proposed project-type: `decision` first (shell), then a separate `build` run (surfaces) — the seed contains both and E8 cannot select a convergence mode for a merged project. MOVE 3: four irreducible questions put to the operator (Q1 shell, Q2 first user, Q3 decision-vs-build sequencing, Q4 canonical repo identity — seed says `endegenaassefa/depth-engine`, operator's own START.md says `rodriguezzfabricio/depth-engine`; X-009 gate applies). **E1 Step 6 confirm gate is OPEN. E2 must not load until the operator answers.**

L-0016
Date: 2026-08-28
Type: decision
**E1 Step 6 confirm gate CLEARED.** Operator answers: Q1 shell = **local web app served by the CLI** (`depth-engine ui` → localhost, reads run dir directly, no Electron/infra/auth). Q2 first user = **external developers, as a product** (not internal-only). Q3 sequencing = **decision run on the shell first**, then a separate build run. Q4 canonical repo = *"Totally diff and new repo and make it private"* — does not name a repo; unresolved, see L-0018. Project-type is now CONFIRMED `decision`, so E8 applies decision-saturation and a CONVERGED verdict routes to E11 directly, skipping E9 and E10. Accepted engine-inferred lines upgraded to `[engine-inferred — operator-confirmed]`, NOT to `[operator-stated]`.

L-0017
Date: 2026-08-28
Type: finding
Q1 and Q3 read together are not contradictory but they change the decision run's job. The operator named a preferred shell AND asked for the decision to be run properly. Therefore Option A (CLI-served local web app) is treated as the **leading hypothesis the run must attempt to overturn**, not as a settled answer. This is L-A applied to the operator's own preference: a convenient answer earns more scrutiny, not less. The E5 sub-questions are deliberately phrased so a `no` is reachable.

L-0018
Date: 2026-08-28
Type: null-result
Q4 remains UNRESOLVED after the confirm gate. The operator's answer states an intent ("totally diff and new repo and make it private") but names no repository. Two readings survive: (1) the canonical depth-engine should move to a new private repo that does not yet exist — an action, not a fact; (2) the answer was aimed at this design repo, already created private. Under X-009 from the prior report ("verifying an artifact is not verifying it is the artifact you asked for"), recorded as `[unknown]` rather than guessed. Does NOT block the shell decision, which turns on architecture already read from the local clone. DOES block any E2 research treating engine source as authoritative, and blocks any action that would create or move repositories.

L-0019
Date: 2026-08-28
Type: action
E5 decision sub-question map written to `artifacts/decision_subquestions.md`: 9 sub-questions (S1–S9) against 5 options (A–E). S3 (does commercial + external break local-only, given no auth/gating/telemetry) and S6 (who opens the UI and when, given the engine is walked by an agent in a terminal the developer is already watching) are designated the two rows most capable of overturning the hypothesis and must be answered at primary grade for saturation. **Option E (a richer terminal UI) was added by the engine, not offered at the gate** — the operator's four options shared the assumption that the answer is a GUI, and E5 exists to catch aspects nobody framed. Saturation criterion recorded with 5 conditions including a mandatory cross-family overturn on the final recommendation.

L-0020
Date: 2026-08-28
Type: correction
**L-A cross-family verdict on the shell hypothesis: 1 INCONCLUSIVE, 2 OVERTURNED. Nothing survived clean.** (a) S1/S7 "localhost has precedent at scale + local-only is a feature" → **INCONCLUSIVE**. Codex: "The precedents are category errors. Storybook, Vite, and `next dev` are free development infrastructure, not standalone commercial workflow products. Prisma pairs local Studio with a hosted collaborative Console; local-only was not sufficient for team use." Two further objections: remote development (SSH, containers, Codespaces, devboxes) frequently puts the run directory on a different machine from the browser, and VS Code needs explicit port forwarding to reach localhost services; and localhost is NOT secure — Jupyter ships token auth by default, so loopback-only binding, random session token, path confinement, CSP, and origin checks are v1 requirements for a server that reads source code. Only genuine commercial-local precedent came from Codex, not from this run: **TablePlus** (perpetual license, local DB client). (b) S3 "commercial+external forces open-core/license-key/hosted tier, decide now" → **OVERTURNED**. The shell forces no business model and does not preclude telemetry (Storybook and Next.js collect opt-in anonymous telemetry while running locally); entitlement can sit at package download, CLI launch, update delivery, or premium-command execution. Narrower surviving guidance: decide distribution and entitlement boundaries now, but do not prematurely design account auth. The genuine one-way door is **hosted collaboration**, not telemetry and not licensing.
Decided at: ~150k context — provisional until reproduced cold (L-C).

L-0021
Date: 2026-08-28
Type: correction
**L-A verdict: OVERTURNED — the most consequential correction of this run.** Claim: "a read-only renderer of the 4 Markdown tiers, with no write path and no backend, already resolves five of eight failures (F3/F4/F5/F7-tracking/F8)." Codex established the Markdown does not carry the required signals: staleness needs heartbeat/process events; "actual model" needs runtime dispatch metadata; token cost needs telemetry events; diffs need git/worktree access likely OUTSIDE the isolated run directory; humanized output needs semantic transformation, not rendering. Also: "A CLI-served browser app already has a backend: the CLI's HTTP/file server" — the no-backend framing was false. And: "Polling, file watching, parsing partial writes, clock-based liveness, and derived status ARE state management." What survives: a renderer honestly delivers REGISTER coverage progress, LEDGER readability, STATE orientation, INDEX navigation — four regions of orientation, not five failure fixes. This **directly invalidates L-0013's implied scope**; a correction block was written into `research/02-what-to-display.md` §2 rather than the claim being silently edited. UNLOCK, already on the operator's own Tier-1 list from the prior report (item #2, "effort: minutes"): `CLAUDE_CODE_ENABLE_TELEMETRY=1` emits `claude_code.api_request` with `model` and `cost_usd`, and `claude_code.token.usage` with `agent.name` — exactly the missing F4 and F7 signals. Only F3 then needs new engine work: a per-agent heartbeat timestamp. Revised 6-step build sequence recorded in `research/05-shell-decision.md`.
Decided at: ~150k context — provisional until reproduced cold (L-C).

L-0022
Date: 2026-08-28
Type: action
`research/05-shell-decision.md` written: S1/S3/S5/S7 answered from the cross-family pass, revised 6-step build sequence (step 0 = turn on telemetry), security requirements folded into step 1 rather than deferred. Decision is **NOT converged** — 6 of 9 sub-questions remain open, including **S6** (who opens the UI and when, given the developer is already watching a terminal) which has had zero research and is a designated primary-grade saturation requirement capable of promoting Option E (TUI). Saturation condition 3 is also unmet: no option other than A has been seriously argued. E8 has NOT been run and must not be run until S6 and S2 have evidence.
