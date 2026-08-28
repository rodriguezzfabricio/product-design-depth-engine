# State (Tier 2) — resume snapshot

> The single mutable "where am I" file. Overwrite in place at each compaction/resume (L-B). Keep it lean — the full record lives in the Ledger; this file POINTS at detail, it does not duplicate it.

### Current stage & task
**E1 — Operator interview.** MOVE 1 (candidate questions) and MOVE 2 (self-answer by research) complete. MOVE 3 delivered: four irreducible questions put to the operator. **Step 6 confirm gate is OPEN and blocking.** E2 must not load until the operator confirms or corrects `artifacts/intent_brief.md`.

### Project-type
**PROPOSED, not confirmed:** `decision` first (which shell), then a separate `build` run (which surfaces). The seed contains both and E8 cannot select a convergence mode for a merged project. Awaiting operator answer to Q3.

### Key conclusions & decisions in force
- The 4 memory tiers map 1:1 onto 4 UI regions; `REGISTER.md` is the hero object — the only honest progress bar in the category because its denominator closes (L-0014).
- F1–F8 split into an observability half (F3/F4/F5/F7-tracking/F8 — a UI fixes these) and an enforcement half (F1/F2/F7-cap — it cannot). Ship the observability UI first (L-0013).
- Two of this run's own central claims were OVERTURNED by cross-family check (L-0011, L-0012). Both corrections moved the design toward the operator's original instinct, not away from it.
- Rank tools by reading them, never by registry install counts (L-0006).
- No AI-company growth number is verified. Six are quarantined as UNVERIFIED (L-0010).

### Open threads & next actions
1. **BLOCKING — operator answers Q1–Q4** (`artifacts/intent_brief.md` §Open questions). Nothing downstream is valid until then.
2. Open the two Codex-cited sources not yet read: `docs.cursor.com/background-agent` and LangSmith tracing/cost docs. Both are load-bearing for L-0011/L-0012 and were accepted on Codex's citation alone.
3. Competitive teardown — actually look at Cursor Background Agents, LangSmith, GitHub Actions run views. Named in `research/03` §6 as the obvious cheap next pass.
4. Re-run the market pass with Scrapling `StealthyFetcher` (v0.4.15, in the run venv) to upgrade or kill the six quarantined figures (L-0010).
5. L-C cold re-verify of L-0011/L-0012/L-0013 — all decided at ~110k context, provisional until reproduced in a fresh window.
6. Candidate engine change to carry forward: a mandatory "inventory existing capability" step before any tooling recommendation (L-0007, 4th recurrence).

### Resume mode
**WAIT** — stopped at a real gate (E1 Step 6 confirm gate). Do not advance to E2 on resume; re-read this file and the Intent Brief, then check whether the operator has answered Q1–Q4.

### Ledger status
Highest ID in Ledger: **L-0015** · Index rows: **15** · invariant (i) holds.

### Blocked items
- E2 (domain expert) — blocked on the E1 confirm gate.
- Q4 repo-identity ambiguity — seed says `endegenaassefa/depth-engine`; operator's own `START.md` records `rodriguezzfabricio/depth-engine`. Research proceeded against the local clone `~/.depth-engine/repo`. Prior report's X-009 gate applies: verifying an artifact is not verifying it is the requested artifact.
