# Coverage Register (Tier 3b) — exhaustiveness guarantee

> One row per tracked item (question / task / risk / aspect / sub-question). Status drives convergence (E8). Append rows and update their status; never delete a row (L-B). On resume, the first `open` or `in-progress` row is where you continue.

**Closed list: 25 rows · 8 covered · 5 in-progress · 12 open.** The denominator is closed — that is what makes this countable, and it is the same property that makes the UI's coverage bar honest (see L-0014).

> Rows S1–S9 are the decision sub-questions E8 judges saturation against (project-type `decision`, confirmed at the E1 gate). The run is **not converged**.

| Item | Type | Status | Evidence (Ledger ID) | Notes |
|------|------|--------|----------------------|-------|
| A1 · View the engine's guts | task | **covered** | L-0003 | 22 Markdown files + thin Node CLI; 4 memory tiers identified as the renderable schema |
| A2 · Market research, developer apps, AI era | research | **in-progress** | L-0009, L-0010 | Linear covered at primary grade; AI-native companies NOT verified — 6 figures quarantined |
| A3 · How the AI apps blew up + how they look | research | **in-progress** | L-0009 | Growth mechanism + visual grammar written; no AI-native primary source obtained |
| A4 · More design/UX research beyond mentor's links | research | **covered** | L-0008 | 9 resources, all URLs verified 200; Nielsen read in full and mapped onto F1–F8 |
| A5 · Best tools/skills for non-slop design | research | **covered** | L-0005, L-0006, L-0007 | uizze command corrected; 8 skills already installed; ranked stack recommended |
| A6 · Decide what to display in the UI | decision | **covered** | L-0013, L-0014 | 4 memory tiers → 4 UI regions; REGISTER is the hero object |
| A7 · Web app vs app | decision | **open** | — | **Blocked on operator Q1.** Structural constraint recorded: engine state is local Markdown; a pure web app needs a local agent |
| A8 · Intentional UI: color psychology, no friction, no random buttons | constraint | **covered** | L-0009 | Operationalized as: every persistent control traces to a documented failure. One dial + one action |
| A9 · Integrate the PDF's new features (M1–M7) | scope | **covered** | L-0002 | All 7 mechanisms mapped to surfaces; M1 (PM panel) is the default view, M7 (dial) the only setting |
| A10 · "Does my task make sense?" | question | **covered** | L-0011, L-0012 | Yes, with 3 corrections. Both of the engine's own objections were overturned in the operator's favour |
| A11 · Create the GitHub repo | action | **covered** | L-0001 | `rodriguezzfabricio/product-design-depth-engine`, private, pushed |
| R1 · Verify Codex's two cited sources | risk | **open** | L-0011, L-0012 | `docs.cursor.com/background-agent` and LangSmith docs accepted on citation alone, never opened |
| R2 · Competitive teardown of actual screens | task | **open** | — | Cursor Background Agents, LangSmith, GitHub Actions — named as the cheap next pass |
| R3 · Cold re-verify the three ~110k-context decisions | risk | **open** | L-0011, L-0012, L-0013 | L-C: high-context decisions are provisional until reproduced in a fresh window |
| R4 · L-0014 is unchallenged and clean | risk | **in-progress** | L-0014 | Under L-A, a clean flattering result earns MORE scrutiny. No overturn attempt has been run on it yet |
| A7 · Shell decided (supersedes the `open` row above) | decision | **in-progress** | L-0016, L-0020 | Operator prefers Option A; cross-family returned 1 inconclusive + 2 overturned. Not settled |
| S1 · Precedent for a CLI-served localhost UI at scale | sub-question | **in-progress** | L-0020 | Precedents were category errors — free infra, not commercial products. Only real one: TablePlus |
| S2 · Does the isolation rule permit a viewer process? | sub-question | **open** | — | Could make Option A illegal as specified. Unanswered |
| S3 · Does commercial + external break local-only? | sub-question | **covered** | L-0020 | No. Shell forces no business model; entitlement has 4 non-auth insertion points |
| S4 · Team review + work-from-any-computer | sub-question | **open** | — | Operator stated the goal; Prisma needed a hosted Console for team use |
| S5 · Can a read-only renderer fix the five failures? | sub-question | **covered** | L-0021 | **No.** Markdown lacks every required signal. Telemetry flag + heartbeat are the fix |
| S6 · Who opens the UI, and when? | sub-question | **open** | — | **Sharpest live objection.** Zero research. Could promote Option E (TUI). Primary-grade required |
| S7 · Is local-only a real differentiator for this buyer? | sub-question | **open** | L-0020 | "Credible feature", but not established as decisive. Remote dev undercuts the premise |
| S8 · Migration path if v1 later needs hosting | sub-question | **covered** | L-0020 | One-way door is **hosted collaboration** only. Telemetry and licensing are cheap to retrofit |
| S9 · Build cost per option | sub-question | **open** | — | Tiebreaker if S1–S8 do not separate the options |
| S10 · Argue an option other than A seriously | sub-question | **open** | — | Saturation condition 3. Unmet — as written this run would converge on the operator's preference unopposed |
| R5 · Codex citations accepted but never opened | risk | **open** | L-0020, L-0021 | Prisma, VS Code Remote SSH, Jupyter security, Storybook/Next telemetry, TablePlus. 2nd recurrence |
