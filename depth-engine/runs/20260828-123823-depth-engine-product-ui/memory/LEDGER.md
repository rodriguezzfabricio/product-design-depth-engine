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

L-0023
Date: 2026-08-28
Type: correction
**Self-caught integrity error in this run's own Register.** The hand-written summary header read "25 rows · 8 covered · 5 in-progress · 12 open". A mechanical tally (`grep -c` on the status cells) returned **27 rows · 11 covered · 5 in-progress · 11 open** — wrong in all four numbers. Corrected in `REGISTER.md` and `README.md`. Found by a script, not by review. Two consequences recorded: (1) this is the prior report §6 argument in miniature — mechanical checks are the only reproducible tier, and they should own any number a human would otherwise type; (2) **direct UI requirement** — a rendered coverage bar must count Register rows itself and must never read a summary line, including the one in the file it is rendering. L-B invariant (i) re-run after the fix using the record-parsing awk (not the line-anchored grep that produced a false alarm in the prior run): ledger records = 22, index rows = 22, HOLDS. Invariant (iii) additive-only: `git diff --diff-filter=DR` from root commit to HEAD returns empty, HOLDS.

L-0024
Date: 2026-08-28
Type: decision
**Q4 RESOLVED by the operator.** The earlier answer ("totally diff and new repo and make it private") referred to THIS work, not to relocating the canonical engine. Operator clarified: *"I need a new repo for it. Like a whole depth engine + product design with depth engine + ui. All this needs to go in a repo."* No second repo was created — `product-design-depth-engine` was made today, is private, and already held the design work; creating another would fragment it. Instead the existing repo was consolidated into the product monorepo the operator described: `engine/` (the Depth Engine source), `ui/` (the surface, not yet built), `research/` (decision records), `depth-engine/runs/` (CLI-managed run workspace, untouched so resume keeps working). Engine brought in with `git subtree add --prefix=engine … --squash` rather than a submodule, so a plain clone on any machine gets every file with no `--recursive` footgun — which is the operator's stated "work from any computer" requirement. Pinned at upstream `3b48cb4`, v0.1.0, working tree verified clean before the pull. Drift risk recorded in the README with the `git subtree pull` sync command; unmanaged divergence between a vendored copy and its upstream is the X-006 failure from the prior report. The `[unknown]` blocking flag on Q4 is cleared.

L-0025
Date: 2026-08-28
Type: correction
**"Effort: minutes" for the telemetry unlock was WRONG, and this run repeated it without checking.** L-0021 and `research/05` relayed the prior report's Tier-1 item #2 ("Turn on telemetry … effort: minutes") as the fix for F4/F7. The operator ran `export CLAUDE_CODE_ENABLE_TELEMETRY=1` and asked whether that was correct. Checked against the harness documentation (code.claude.com/docs/en/monitoring-usage): **the flag alone collects nothing.** At least one exporter is required — `OTEL_METRICS_EXPORTER` / `OTEL_LOGS_EXPORTER`, valid values `console` | `otlp` | `prometheus` | `none`. Verbatim from the docs: *"There is no built-in file exporter — you must pipe output or use `otlp` exporter with a local collector."* So the two honest options are console (pollutes the terminal on every session) or OTLP into a local collector (real infrastructure). Turning the flag on is minutes; getting data into a place the UI can read is not. Verified on this machine: the variable is unset, and is absent from `~/.zshrc`, `~/.zprofile`, and `~/.claude/settings.json` — so a shell `export` neither persists nor reaches an already-running session. Correct persistent home is the `env` block of `~/.claude/settings.json`. **This is the prior report's §8 lesson recurring for the fifth time — read the harness docs before relaying a mechanism — and this run committed it by relaying a claim instead of checking it.** Confirmed emitted attributes worth designing against: `model`, `query_source` (main | subagent | auxiliary), `agent.name`, `skill.name`, `effort`, `speed`, plus `claude_code.api_request` carrying cost, tokens, model and duration.

L-0026
Date: 2026-08-28
Type: finding
**S6 ANSWERED, and the premise was wrong.** I framed S6 as "terminal vs browser while watching a run." Research killed the framing: for long-running agent work the developer does not watch, they leave. Cursor Background Agents run remotely, write to a branch, open a **PR with a summary**, and notify by email + desktop notification + Slack. GitHub Actions offers `gh run watch` streaming in-terminal until settled, plus a web UI for review. General agent-watch tooling returns a watch ID immediately and reports final status when the run settles, with the documented caution that monitors must stay selective because every output line interrupts. CONSEQUENCES: (1) the primary job is a four-beat loop — start, leave confidently, get pulled back at a gate/death/terminal, land somewhere that answers what happened / what changed / what needs me; (2) the "browser tab fragments attention" objection against Option A largely dissolves, because the surface is a destination visited on notification, not a competing window — **Option E (TUI) is NOT promoted on attention grounds**; (3) the shell matters less than the notification channel, since both a browser and a TUI can be notified into.

L-0027
Date: 2026-08-28
Type: correction
**F3 was misdiagnosed, by this run and arguably in the original failure log.** F3 reads "subagents kept dying and the engine never noticed; the operator sat waiting, then checked by hand." L-0013 and `research/02` mapped it to a heartbeat indicator in the UI. **A heartbeat display only helps someone who is looking at it** — and the defining fact of F3 is that the operator had left. F3's real fix is a **notification**, not a dashboard row. This is cheaper than the UI work it was queued behind and does not depend on the shell decision at all. The engine's **hard gates are the natural notification triggers**: the E1 confirm gate, E2/E5 sign-offs, the E11 review, plus agent death and terminal state. **Gap named that no source in this run had surfaced: the engine has no notification primitive** — not in the Markdown tiers, not in the OTel stream. That is an engine gap, not a UI gap. New sub-question S11 opened: what is the notification channel, and where does the primitive live? Also worth carrying: Cursor's review surface is a PR, not a dashboard — the engine's three terminals may want to land as a document the developer already knows how to review, with a dashboard reserved for runs in flight.

L-0028
Date: 2026-08-28
Type: finding
**Operator premise checked and FALSE, verified at primary grade.** Operator stated: "it's like cursor you don't see the underlying prompts, same thing with claude code harness we don't ever see it." GitHub API, 2026-08-28: `x1xhlol/system-prompts-and-models-of-ai-tools` has **143,196 stars**, 28 contributors, updated 2026-08-11, and its top-level directories include `Cursor Prompts`, `Anthropic` (Claude Code), `Devin AI`, `Lovable`, `Replit`, `Warp.dev`, `Windsurf`, `VSCode Agent` — including JSON tool schemas, not just prompt text. Second corroborating repo `asgeirtj/system_prompts_leaks` covers Anthropic (Opus 5, Fable 5, Claude Code), OpenAI Codex, Google, xAI. What Cursor and Anthropic achieve is NOT SHOWING you — a presentation choice — not protection. Also verified: `NousResearch/hermes-agent`, **237,588 stars**, MIT, pushed 2026-08-28 — a legitimate BYO-agent target as the operator assumed.

L-0029
Date: 2026-08-28
Type: correction
**L-A verdict: INCONCLUSIVE — my over-correction was caught.** I claimed method secrecy is simply unavailable to this product. Codex: "it conflates perfect secrecy with economically useful secrecy. Public prompt extraction proves determined customers can reverse-engineer a system; it does not prove that obscuring prompts has zero value. Friction, incomplete extraction, update lag, licensing, and trade-secret remedies can still deter commodity competitors." Counter-examples I had ignored: **Stripe Radar** (customers submit transactions and receive scores; Stripe publishes only "a preview of some signals," never the operative model) and **Renaissance Technologies** (decades of proprietary strategies as the stated moat). Surviving narrower claim, and it is the finding: **secrecy is impossible under TODAY'S ARCHITECTURE**, because `depth-engine init` writes every stage, law and protocol file to the customer's disk. "Impossible forever" is overstated; "impossible while `init` ships the method" survives. CONSEQUENCE: the operator's IP concern is legitimate and is **not a UI problem** — it is a distribution/orchestration-boundary problem upstream of every display decision. Separately **OVERTURNED**: my open-core suggestion. Codex: open-core "gives noncustomers immediate cloning material, eliminates extraction effort, enables forks, and weakens trade-secret claims"; execution, evidence, distribution, cadence AND a proprietary method can jointly form a moat — I framed a false either/or.
Decided at: ~215k context — provisional until reproduced cold (L-C).

L-0030
Date: 2026-08-28
Type: correction
**L-A verdict: OVERTURNED — and the counter-argument IS the design.** I claimed R-A (connect your own agent) and R-B (don't expose the method) are mutually exclusive. Codex: "L-A requires a different **model family**, not a customer-supplied second agent or visibility into the entire harness… R-A and R-B become mutually exclusive **only if every connected agent must receive the complete method. That assumption is not in R-A.**" RESOLUTION: the boundary is not hosted-vs-local, it is **orchestration vs execution**. The orchestrator (stage sequencing, gates, laws, adjudication, convergence logic) stays proprietary and unshipped; connected agents receive **one stage-scoped task contract at a time** and never see the pipeline. An agent told "research these five failure modes and return findings with citations" learns nothing about E0–E11 or the laws. **The sequencing is the IP; the individual task rarely is.** Precedent that customer code need not move: **GitLab's BYOM architecture keeps source code and inference traffic inside the customer's own AWS boundary while GitLab supplies orchestration and governance** — "our orchestration, your machine, your models," which preserves the local-first privacy positioning. COST, stated honestly: this is a real re-architecture, because today the engine IS the Markdown and the agent reads all of it. Moving to contracts makes the orchestrator software that runs rather than documents that are read — which is the same "make it a harness" conclusion the prior report reached in §9, arrived at from a different direction.
Decided at: ~215k context — provisional until reproduced cold (L-C).

L-0031
Date: 2026-08-28
Type: decision
**Connect-your-own-agent VALIDATED, with one caution, and it must be built as a guarantee rather than a settings page.** For: (1) it is a precondition, not a feature — L-A mandates a different model family for every load-bearing verdict, and PDF gate G1 ("until codex is in, every verdict is same-family") is that requirement failing in practice; (2) it is checkable and unfakeable — "authored by Claude, challenged by Codex" is a verifiable property of a run; (3) broad precedent in developer tools — Cline, Continue, Aider, VS Code BYOK. CAUTION from the cross-check: **Sourcegraph offered BYOK/BYOLLM then discontinued Cody Free and Pro in favour of a more opinionated agentic product** — this does not prove BYO caused failure, but it disproves that provider choice by itself creates product value. Therefore: **model choice is not the differentiator; the cross-family guarantee is.** UI form: a single persistent strip showing `Author · Challenger · ✓ cross-family` or `⚠ same-family — verdicts unverified`. Not a dropdown of providers. Adding an agent is a consequence of clicking the warning, not a settings excursion. This satisfies the operator's "no random buttons" constraint while making the sold promise visibly true or false.

L-0032
Date: 2026-08-28
Type: decision
**Display model REPLACED. `research/02-what-to-display.md` §3 is superseded.** That section mapped engine internals one-to-one onto UI regions (E0–E11 → pipeline rail, LEDGER → feed, etc.), which would leak the pipeline by construction. New rule: **show the customer's work, never the engine's machinery** — which serves the IP boundary AND Nielsen #2 (match the real world) and #8 (minimalism) simultaneously, since a paying developer does not want to learn "E5 aspect decomposition." Translation layer: stages E0–E11 → plain phases (Understanding → Researching → Stress-testing → Deciding); L-A → "challenged by a second model" + survived/challenged badge; REGISTER rows → "your questions, 17 of 23 answered"; LEDGER → "what we found" with evidence links; E8 verdict → the coverage bar (counting rows itself per L-0023); refusal → "we recommend not proceeding — here's why". Stage prompts, law text and gate logic are **never rendered** — not in a debug view, not behind a toggle. WHAT MUST STILL BE SHOWN OR THERE IS NO PRODUCT: the evidence. The value proposition is "this survived attack," and proving it requires showing what was attacked and what survived. The result is the customer's; the method is the vendor's — a lab report shows results and a methods summary, not the reagent formula. Diffs (F5): executor-side, so the diff is customer data and carries **no IP tension** — purely a permissions question, still blocked on S2. Cursor's answer worth copying: the review surface is a PR, not a bespoke diff viewer.

L-0033
Date: 2026-08-28
Type: decision
**Operator answers, second gate.** (1) IP boundary = **design the seam now, build it later** — keep shipping local Markdown, but write every stage as a self-contained task contract from today so orchestration can move server-side without a rewrite. Reversible door; no engine re-architecture before a paying customer demands it. (2) Ambition = **real venture, shipping to paying users.** (3) Buyer = **not known yet.** (4) Notifications = **all operating systems**, not macOS only. Consequence recorded: the shell decision is **no longer blocked on S12**, because orchestration stays local for now and the seam preserves the option to move it. It is now blocked on the buyer question instead.

L-0034
Date: 2026-08-28
Type: finding
**Highest-value open item is now non-technical, and no further design reduces it.** "Real venture, shipping to paying users" combined with "don't know who's paying" is a live tension: solo-developer, small-team, and enterprise buyers fork nearly every downstream decision (local-first correctness, whether team review is waste, whether the append-only ledger is a compliance asset, whether SSO and procurement are unavoidable). Prisma is the cited precedent that local-only stops being sufficient at team scale. Recommended next step is operator-executed, not engine-executed: talk to 5–10 developers already running Claude Code or Codex on real work, ask what they do today when an agent burns an hour and returns something untrusted, and test whether "it survived an attack by a second model" is worth paying for versus re-running and eyeballing. **Zero people other than the operator have been asked anything about this product.** For a venture this is the largest risk in the register and it is not reducible by research the engine can perform.

L-0035
Date: 2026-08-28
Type: decision
**Seam specification written** (`research/07-the-seam.md` §2). One rule: every stage must be expressible as a self-contained task contract revealing nothing about the pipeline. Contract fields: `task_id`, `role` (researcher | challenger | builder | verifier), `objective` (one plain sentence), `inputs` (data only, never method), `deliverable` (exact return shape so grading is mechanical), `acceptance` (stated up front), `constraints` (`max_turns` as a hard cap the executor cannot raise, allowed tools), `forbidden` (asking what step this is, requesting other tasks or the surrounding process). **Deliberately absent: stage numbers, law identifiers, neighbouring steps, convergence criteria, gate logic.** Litmus test, both halves required: hand one contract to a stranger's agent — if they can do the job it is self-contained; if they can reconstruct the pipeline it leaks. **Seam enforced as a CI lint, not a promise** — a grep for stage/law identifiers and pipeline vocabulary that fails the build, because the operator's own record shows prose rules decay and code rules hold. Warning carried from the prior report §10: tune the pattern against real contracts first, since a check that raises false alarms gets switched off, and a switched-off check is fail-open.

L-0036
Date: 2026-08-28
Type: finding
**Cross-platform notification: reject the obvious dependency, write ~30 lines instead.** `node-notifier` verified 2026-08-28 via npm and GitHub APIs: MIT, v10.0.1, **5,538,879 downloads last week**, 5,845 stars, **last pushed 2024-06-24 (over two years), 128 open issues** — heavily used, effectively unmaintained. Two reasons to decline it: the engine's README advertises "No dependencies to install — the CLI is pure Node (≥18)", so adding a package to the core loop breaks a property currently being sold; and a two-year-stale dependency in a core feature is inherited supply-chain risk for a venture with paying users. Native mechanisms present by default on each platform: macOS `osascript -e 'display notification'`; Linux `notify-send` (libnotify); Windows 10+ PowerShell toast via `Windows.UI.Notifications`. Detect with Node's built-in `process.platform`, shell out, **fail silently** so a notification never kills a run, and fall back to a terminal bell `\x07` for headless/SSH. **Fire on exactly four events** — gate needs a decision, agent died or went stale past deadline, run reached a terminal, spend crossed an operator-set threshold — because agent-monitoring research is explicit that monitors must stay selective since every output line interrupts. Not on stage transitions, not on findings; an ignored notification equals no notification, which is F3 again. **This is the cheapest real win in the project: it fixes F3, costs hours, needs no UI, and depends on none of the open decisions. Build it first.**

L-0037
Date: 2026-08-28
Type: null-result
**LAW L-A UNSATISFIED — the cross-family checker died on quota mid-verdict.** `codex exec` returned: "ERROR: You've hit your usage limit… try again at 1:19 PM." The claims it was attacking (market-need premise, rigor-product base rate, desk-research-cannot-establish-demand) therefore have **NO adversarial pass**. Recorded as unsatisfied per START.md §6 — never record an unrun check as passed. This is the prior report's **X-003** reproducing exactly: rate-limit errors never trigger fallback model chains, subagent requests fail terminally, and nothing resumes by itself. It is also **F3 and F7 happening to this run**: an agent died and the only reason it was noticed is that the output was read by hand. The engine has no quota-death detection and no resume path — both already on the operator's Tier-2 build list as item 7, still unbuilt.

L-0038
Date: 2026-08-28
Type: finding
**E2/E3 were SKIPPED, and that is the defect the operator caught.** The engine's order is E0 intake → E1 interview → **E2 become the domain expert** → **E3 mine the world's scar tissue** → E4 seams → E5 decompose. This run went E0 → E1 → straight to design decisions and an E5 sub-question map. Every conclusion in `research/02` through `research/07` was reached with no domain-expertise pass and no failure research underneath it. The operator's request to "research if there's a need" is the protocol asserting itself against a run that cut corners, not a change of plan. Correction to his framing, recorded: he supplied the conclusion in advance — "There is [a need], no one has had a solution for it before" — which is a flattering, load-bearing claim handed to the researcher with the answer attached, the setup L-A exists to prevent. Also recorded: "no one has solved it" has two externally identical explanations, a new category or a graveyard, distinguishable only by searching for failed attempts.

L-0039
Date: 2026-08-28
Type: finding
**E3 first pass — the category's corpses and what killed them.** Academic sources, not vendor blogs: **"significantly less than 1% of developers use formal verification"** — the most rigorous technique the field has produced, it works, almost nobody uses it; stated reason is that the additional effort needs an obvious short-term benefit and must pay for itself each week. Second: developers use free static-analysis tools even where executives would fund paid ones, because the expectations attached to a costly tool land on the developer who requested it. Third, the mechanism of death once adopted: *"false positives, and the way in which the warnings are presented, are barriers to use… many tools generate thousands of warnings, making it difficult to extract meaningful insights."* **Direct read-across to the operator's own failure log: F8 (unreadable output) and F1 (no stopping point) are not annoyances — they are the exact two symptoms that killed the previous generation of rigor tools.** A tool producing more findings than a human will read gets ignored, and an ignored check equals no check. The Depth Engine is slow by design, which is the same tax formal verification failed to justify; that is the corpse most similar to it.

L-0040
Date: 2026-08-28
Type: correction
**My own intended argument was destroyed by the evidence before it was ever made.** I was going to argue that rigor/correctness products have a poor commercial record while speed/output products win. FALSE, and not close: **Snyk $325.0M revenue, $1.247B raised over 16 rounds**, selling security scanning; **SonarSource/SonarQube** since 2007, with **~85% of its rules code-quality and only ~15% security**; Datadog the broadest commercial observability platform; Sentry developer-first debugging, strong in small and mid-size teams. Formal verification failed while Snyk built a $325M business three feet away from it. Recorded as a correction rather than quietly dropped, because the run nearly shipped a false base-rate claim to the operator.
Decided at: ~272k context — provisional until reproduced cold (L-C). NO cross-family pass (L-0037).

L-0041
Date: 2026-08-28
Type: finding
**The pattern separating the winners from the corpse, and it points at the buyer (S15).** **Rigor sells to whoever eats the cost of failure; it does not sell to whoever pays the cost of the rigor.** Formal verification asks the individual developer to absorb large immediate effort for a diffuse benefit landing elsewhere — payer and sufferer are different entities. Snyk sells to an org that eats a breach, Sonar to an org that eats years of technical debt, Datadog to a team that eats a 3am outage — payer and sufferer are the same entity. Corroborating purchasing research: *individual developers discover tools, team leads evaluate them, platform engineering or procurement makes the final decision* (bottom-up adoption, top-down budget), and **only 5% of individual developers treat cost-cutting as a priority when choosing a tool, while productivity ranks highly as a motivator to buy.** The Depth Engine is explicitly NOT a productivity tool — it is slow by design — so the motivation that makes individual developers buy is the one it does not have. What it does have (append-only ledger of what was challenged and what survived, plus a documented refusal) is a **risk artifact**, and risk is bought by whoever the risk lands on. **WORKING HYPOTHESIS for S15, to be tested with humans not with more reading: the individual developer is the ADOPTER, not the PAYER.** Reframes the interviews — do not ask developers whether they would pay; ask who gets blamed when an AI-assisted decision turns out wrong, then go talk to that person. UNCHALLENGED and clean, which under L-A earns more scrutiny, not less.

L-0042
Date: 2026-08-28
Type: null-result
**No direct competitor sweep has been run, so "no one has had a solution" remains the operator's assertion and not a finding.** This pass established the CATEGORY BASE RATE only. Named candidates still unchecked at source: LangSmith and Braintrust evaluation platforms, promptfoo, DeepEval, Guardrails, AI code-review tools, and any agent-verification or AI-decision-audit product. The operator's own PDF target **T10** already ordered this sweep — "many tools solve pieces of what the engine wants to solve, including problems the operators haven't identified yet" — and named the starting index `ai-boost/awesome-harness-engineering`. **It was never run, and gate G4 asking the operator to rule on its scale was never answered.** Built-in web search returned SEO listicles again this pass, the third recurrence of standing rule **R3** this run; Scrapling `StealthyFetcher` v0.4.15 sits unused in the run venv and is the documented fix.

L-0043
Date: 2026-08-28
Type: correction
**L-A SATISFIED on re-run (operator restored codex credits). ALL THREE CLAIMS OVERTURNED. The operator's founding premise is FALSIFIED.** Codex: "The founder's 'no solution before' premise is already falsified, so it is not the deepest remaining uncertainty. The harder risks are differentiation, measurable quality improvement, workflow tolerance, and payment." Six competitors named; **I independently verified every one** rather than accepting citations unopened (the defect this run had already committed three times, register row R5): **`github/spec-kit` 132,004 stars, pushed 2026-08-28** (intent → spec → plan → tasks, agent-independent, checklists, cross-artifact analysis — spec-driven development is a FIRST-PARTY GitHub feature); **`nexus-substrate/nexus-agents` 18 stars, pushed 2026-08-28**, self-described as "Governance substrate for your AI coding agents — adversarial review, drift-detected rules, immutable audit, closed-loop telemetry" (nearly the operator's pitch verbatim, being built right now, independently); plus **Sigil** runsigil.com (markdown spec → hidden verification scenarios → allow/review/block, signed append-only ledger), **Findry** findry.ai (requirement-to-production governance, policy gates, hash-chained evidence ledger), **Kiro** kiro.dev, **Augment Intent** (coordinator → implementer → verifier, adversarial roles, human gates) — all four returned HTTP 200. WHAT SURVIVES: "I found no verified product matching every Depth Engine stage — especially failure-history mining plus mandatory cross-family attack — but that makes its differentiation **a particular workflow bundle, not a new category.**" Consequence: the operator is a distinct bundle in a category that already contains GitHub, not a one-of-one. Survivable (Linear beat Jira on craft) but a completely different strategic posture. **E3 failure-history mining and mandatory cross-family attack are the two genuinely uncommon stages — those are the product.**

L-0044
Date: 2026-08-28
Type: correction
**Both my base-rate claim AND my correction to it were wrong.** L-0040 already retracted "rigor products don't sell." Codex went further and killed L-0039's framing of formal verification as the nearest corpse: formal methods support real businesses — **Runtime Verification** (100+ clients, **$30K–$50K monthly engagements**), **Certora** (seven years, $100B+ protected assets), **AdaCore/SPARK**. Formal verification is **high-value, low-volume**, a different business shape rather than a failed one. Further correctness-market figures: **Sonar raised $412M at a $4.7B valuation**; **Tricentis took a $1.33B investment at a $4.5B valuation**; **Synopsys sold its application-security/static-analysis division for up to $2.1B**. Codex's sharper framing: "The sharper threat is not 'rigor never sells.' It is that **individual developers may not personally bear enough failure cost; enterprises, security teams, and regulated sectors usually do.**" **This CONFIRMS L-0041 rather than overturning it — the payer-is-not-the-adopter hypothesis is the only conclusion in this entire run to survive a genuine adversarial attack.** Treat it as the most load-bearing finding the operator owns. NOTE: the six financial figures carry primary-source URLs that I did NOT open; I verified the six competitor products, not the financials.

L-0045
Date: 2026-08-28
Type: correction
**My "go do 5–10 interviews" advice was too weak, OVERTURNED.** Codex: "Interviews are neither necessary nor sufficient to establish willingness to pay: **they measure statements, not purchases.** Paid pilots, preorders, retention, workflow telemetry, and abandonment under real latency provide stronger evidence." **"Abandonment under real latency" is the specific risk**, because the Depth Engine is slow by design and nobody discovers whether they tolerate that by being asked about it. Corrected sequence: (1) competitor/graveyard research — partly done, T10 sweep still outstanding; (2) a **minimal testable workflow** — the smallest thing that runs end to end and produces one real ledger on someone else's real problem; (3) a **paid behavioural test** — pilot or preorder, money changing hands. Interviews run alongside as diagnosis, not validation. Surviving fragment of my claim, narrow: desk research alone cannot validate demand for the Depth Engine specifically. **Next milestone is therefore NOT a UI — it is one real ledger from one real external problem, in front of one person willing to pay.**
