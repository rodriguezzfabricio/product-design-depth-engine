# product-design-depth-engine

Product and UI design for the **Depth Engine** — research, decisions, and the design record.

> Written by an AI coding agent (Claude Code) during depth-engine run `20260828-123823-depth-engine-product-ui`, 2026-08-28. Per the operator's CLAUDE.md rule, AI-written documentation says so.

---

## Status

**E1 — Operator interview. Confirm gate OPEN.**
Research is done; the Intent Brief is drafted and awaiting the operator's answers to four questions. E2 does not load until then.

Coverage: **7 covered · 4 in-progress · 4 open**, out of a closed list of 15 → [`REGISTER.md`](depth-engine/runs/20260828-123823-depth-engine-product-ui/memory/REGISTER.md)

## Start here

| Read | For |
|---|---|
| [`research/02-what-to-display.md`](research/02-what-to-display.md) | **The main answer.** What goes in the UI, why, and the two claims that got overturned |
| [`research/01-tooling-audit.md`](research/01-tooling-audit.md) | Which skills to install, which you already have, and the one command that doesn't work |
| [`research/03-market-and-business.md`](research/03-market-and-business.md) | How developer tools actually grew, and which numbers are unverified |
| [`research/04-design-canon.md`](research/04-design-canon.md) | Nine verified resources, and the four to read first |
| [`artifacts/intent_brief.md`](depth-engine/runs/20260828-123823-depth-engine-product-ui/artifacts/intent_brief.md) | The four open questions blocking the run |

## The three findings that matter

1. **You already designed the UI's data model.** The engine writes four memory files on every run. They map one-to-one onto four UI regions, and `REGISTER.md` — a closed list with per-row status — is a progress bar that can honestly reach 100%. Every competitor shows a spinner, because a spinner is what you display when you cannot name the denominator.

2. **Your eight failures split in half, and the split is the release plan.** Five (F3, F4, F5, F7-tracking, F8) are fixable with pixels. Three (F1, F2, F7-cap) need code that runs. Ship the first five.

3. **The engine argued against the operator twice and lost both times.** Under Law L-A, this run's two central claims were sent to Codex — a different model family — with instructions to overturn them. Both were overturned, with concrete counter-evidence. The corrections are recorded in [`research/02`](research/02-what-to-display.md) §1 and in the Ledger as `L-0011` and `L-0012`, not quietly edited out.

## Layout

```
research/                     the four research artifacts
depth-engine/runs/<run-id>/
├── artifacts/                seed.md, intent_brief.md, preserved sources
└── memory/                   LEDGER · STATE · INDEX · REGISTER
```

`memory/` is the run's append-only record. `LEDGER.md` is the audit trail — every finding, null-result, and correction with its evidence. `STATE.md` is where to resume.

## Resuming

```bash
/depth-engine-start resume 20260828-123823-depth-engine-product-ui
```

Reads `STATE.md`, runs the L-B integrity checks, finds the first open Register row, continues there. Resume mode is **WAIT** — it stops at the E1 confirm gate rather than advancing on its own.

## Honest ceiling

A clean walk proves the process ran. It does not prove the output is right.

Specifically, as of this run: no user research exists — no developer other than the operator has been asked anything. Two Codex-cited sources were accepted on citation alone and never opened. Six market figures are quarantined as unverified. Three decisions were made at ~110k context and are provisional until reproduced cold. All of this is tracked as open rows in the Register rather than left implicit.
