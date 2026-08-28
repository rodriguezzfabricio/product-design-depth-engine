# State (Tier 2) — resume snapshot

> The single mutable "where am I" file. Overwrite in place at each compaction/resume (L-B). Keep it lean — the full record lives in the Ledger; this file POINTS at detail, it does not duplicate it.

### Current stage & task
**E1 complete (confirm gate cleared). E5 complete. In E7 — answering the decision sub-questions.**
Four of nine sub-questions have evidence; the decision is **NOT converged**. E8 has not been run and must not run until S2 and S6 have evidence.

### Project-type
**`decision`** — CONFIRMED at the E1 confirm gate. E8 applies **decision-saturation**. A CONVERGED verdict routes to **E11 directly**; E9 and E10 are skipped.

### Key conclusions & decisions in force
- **Shell hypothesis is NOT confirmed.** Operator prefers Option A (CLI-served local web app). Cross-family pass returned 1 inconclusive + 2 overturned; nothing survived clean (L-0020, L-0021).
- **A read-only Markdown renderer fixes none of the five observability failures** — the Markdown lacks heartbeat, dispatch metadata, telemetry, and git access (L-0021). It does deliver orientation: coverage bar, readable ledger, state header, navigation.
- **The unlock is `CLAUDE_CODE_ENABLE_TELEMETRY=1`** — already item #2 on the prior report's Tier-1 list, "effort: minutes". Supplies `model` per request (F4) and `cost_usd`/tokens per `agent.name` (F7). Only F3 then needs new engine work: a per-agent heartbeat timestamp.
- **The only genuine one-way door is hosted collaboration.** Telemetry and licensing can be added later cheaply; account auth should not be built pre-emptively (L-0020).
- **Localhost security is a v1 requirement**, not later hardening: loopback-only binding, random session token, path confinement, CSP, origin checks. Jupyter's default token auth is the precedent.
- `REGISTER.md` as the hero UI object survives — still **unchallenged**, which under L-A means it is owed scrutiny, not trust (L-0014).
- Rank tools by reading them, never by registry install counts (L-0006).

### Open threads & next actions
1. **S6 — who opens the UI, and when?** Zero research. The developer is already watching a terminal while the agent walks the engine. This is the sharpest live objection to Option A and could promote Option E (a TUI). Designated primary-grade for saturation.
2. **S2 — does the isolation rule in `START.md` forbid a viewer process reading the run directory?** Unanswered; potentially makes Option A illegal as specified.
3. **Argue an option other than A seriously.** Saturation condition 3 is unmet. As written, this run would converge on the operator's preference without a real alternative — the exact shape of a flattering result under L-A.
4. Open Codex's citations — Prisma Studio/Console, VS Code Remote SSH, Jupyter security, Storybook/Next.js telemetry, TablePlus. Accepted as argument, never verified. Second recurrence of this defect.
5. Re-run the market pass with Scrapling `StealthyFetcher` to upgrade or kill the six quarantined figures (L-0010).
6. L-C cold re-verify: L-0011, L-0012, L-0013, L-0020, L-0021 were all decided at 110k–150k context.
7. Carry-forward engine change: a mandatory "inventory existing capability" step before any tooling recommendation (L-0007, 4th recurrence).

### Resume mode
**CONTINUE** — next unambiguous action is S6: research whether a browser surface helps or fragments attention for a developer already supervising an agent in a terminal, then S2. Do not run E8 before both have evidence.

### Ledger status
Highest ID in Ledger: **L-0025** · Index rows: **25** · invariant (i) holds.

### Blocked items
- **Q4 repo identity** — operator answered *"totally diff and new repo and make it private"*, which names no repository. `[unknown]`. Blocks any E2 research treating engine source as authoritative, and blocks any action that would create or move repositories. Does not block the shell decision.
