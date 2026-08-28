# product-design-depth-engine

Product and UI design for the **Depth Engine** — research, decisions, and the design record.

> Written by an AI coding agent (Claude Code) during depth-engine run `20260828-123823-depth-engine-product-ui`, 2026-08-28. Per the operator's CLAUDE.md rule, AI-written documentation says so.

---

## Status

**Confirm gate cleared. Project-type `decision`. In E7 — answering the shell sub-questions. NOT converged.**

Operator decisions: shell = **local web app served by the CLI** · first user = **external developers, as a product** · sequencing = **decision run first**.

Coverage: **11 covered · 5 in-progress · 11 open**, out of a closed list of 27 → [`REGISTER.md`](depth-engine/runs/20260828-123823-depth-engine-product-ui/memory/REGISTER.md)

## Start here

| Read | For |
|---|---|
| [`research/05-shell-decision.md`](research/05-shell-decision.md) | **Newest.** Where the shell decision actually stands, and the 3 claims that did not survive |
| [`research/02-what-to-display.md`](research/02-what-to-display.md) | **The main answer.** What goes in the UI — includes a ⚠ correction block in §2 |
| [`research/01-tooling-audit.md`](research/01-tooling-audit.md) | Which skills to install, which you already have, and the one command that doesn't work |
| [`research/03-market-and-business.md`](research/03-market-and-business.md) | How developer tools actually grew, and which numbers are unverified |
| [`research/04-design-canon.md`](research/04-design-canon.md) | Nine verified resources, and the four to read first |
| [`artifacts/intent_brief.md`](depth-engine/runs/20260828-123823-depth-engine-product-ui/artifacts/intent_brief.md) | The four open questions blocking the run |

## The three findings that matter

1. **You already designed the UI's data model.** The engine writes four memory files on every run. They map one-to-one onto four UI regions, and `REGISTER.md` — a closed list with per-row status — is a progress bar that can honestly reach 100%. Every competitor shows a spinner, because a spinner is what you display when you cannot name the denominator.

2. **Your eight failures split in half, and the split is the release plan.** Five (F3, F4, F5, F7-tracking, F8) are fixable with pixels. Three (F1, F2, F7-cap) need code that runs. Ship the first five.

3. **The engine argued against the operator twice and lost both times.** Under Law L-A, this run's two central claims were sent to Codex — a different model family — with instructions to overturn them. Both were overturned, with concrete counter-evidence. The corrections are recorded in [`research/02`](research/02-what-to-display.md) §1 and in the Ledger as `L-0011` and `L-0012`, not quietly edited out.

## Layout

This is the product monorepo: the engine, the design work, and the UI in one place.

```
engine/                       the Depth Engine source (git subtree, upstream: rodriguezzfabricio/depth-engine)
ui/                           the product surface — not built yet, see ui/README.md
research/                     research and decision records (01–05)
depth-engine/                 CLI-managed run workspace — do not hand-edit
└── runs/<run-id>/
    ├── artifacts/            seed.md, intent_brief.md, decision_subquestions.md, sources
    └── memory/               LEDGER · STATE · INDEX · REGISTER
```

`memory/` is the run's append-only record. `LEDGER.md` is the audit trail — every finding, null-result, and correction with its evidence. `STATE.md` is where to resume.

### On `engine/`

Vendored with `git subtree`, not a submodule — the files are simply present, so a plain `git clone` on any machine gets everything with no `--recursive` footgun. Pinned at upstream `3b48cb4` (v0.1.0).

**This copy is not the canonical engine.** Upstream is `rodriguezzfabricio/depth-engine`. To sync:

```bash
git subtree pull --prefix=engine https://github.com/rodriguezzfabricio/depth-engine.git main --squash
```

Version drift between a vendored copy and its upstream is exactly the failure logged as X-006 in the prior report. If this repo becomes the real home of the engine, retire the upstream deliberately rather than letting the two diverge quietly.

## Resuming

```bash
/depth-engine-start resume 20260828-123823-depth-engine-product-ui
```

Reads `STATE.md`, runs the L-B integrity checks, finds the first open Register row, continues there. Resume mode is **WAIT** — it stops at the E1 confirm gate rather than advancing on its own.

## Honest ceiling

A clean walk proves the process ran. It does not prove the output is right.

Specifically, as of this run: no user research exists — no developer other than the operator has been asked anything. Two Codex-cited sources were accepted on citation alone and never opened. Six market figures are quarantined as unverified. Three decisions were made at ~110k context and are provisional until reproduced cold. All of this is tracked as open rows in the Register rather than left implicit.
