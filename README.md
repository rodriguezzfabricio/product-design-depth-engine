# product-design-depth-engine

Product and UI design for the **Depth Engine** — research, decisions, and the design record.

> Written by an AI coding agent (Claude Code) during depth-engine run `20260828-123823-depth-engine-product-ui`, 2026-08-28. Per the operator's CLAUDE.md rule, AI-written documentation says so.

---

## Status

**⛔ Founding premise falsified. Sent back to E2/E3. Design work is on hold.**

"No one has had a solution for this" is checkably false — `github/spec-kit` has **132,004 stars**, and `nexus-substrate/nexus-agents` already ships **six of the seven v2 mechanisms**, with a hash-chained audit trail stronger than the Markdown ledger. See [`research/09`](research/09-the-gold.md).

**The wedge that survives: repo-specific recurrence prevention** — the one mechanism that accumulates proprietary per-customer data instead of copyable orchestration. The next milestone is not a UI; it is one real ledger on one real external repo showing one prevented recurrence.

Operator decisions: shell = **local web app served by the CLI** · first user = **external developers, as a product** · sequencing = **decision run first**.

Coverage: **19 covered · 10 in-progress · 17 open**, out of a closed list of 46 → [`REGISTER.md`](depth-engine/runs/20260828-123823-depth-engine-product-ui/memory/REGISTER.md)

## Start here

| Read | For |
|---|---|
| [`research/09-the-gold.md`](research/09-the-gold.md) | **Newest.** v2 mapped against the closest competitor, and the one item worth building a company around |
| [`research/08-does-anyone-need-this.md`](research/08-does-anyone-need-this.md) | **Newest.** Whether the category sells at all, what killed the last generation of rigor tools, and who the payer probably is. **No cross-family check ran** |
| [`research/07-the-seam.md`](research/07-the-seam.md) | **Newest.** The task-contract seam, the CI lint that enforces it, cross-platform notifications, and the buyer gap |
| [`research/06-ip-boundary-and-agents.md`](research/06-ip-boundary-and-agents.md) | The IP boundary, connect-your-own-agent, and what the UI can honestly show. Supersedes `02` §3 |
| [`research/05-shell-decision.md`](research/05-shell-decision.md) | Where the shell decision stands, and the claims that did not survive |
| [`research/02-what-to-display.md`](research/02-what-to-display.md) | **The main answer.** What goes in the UI — includes a ⚠ correction block in §2 |
| [`research/01-tooling-audit.md`](research/01-tooling-audit.md) | Which skills to install, which you already have, and the one command that doesn't work |
| [`research/03-market-and-business.md`](research/03-market-and-business.md) | How developer tools actually grew, and which numbers are unverified |
| [`research/04-design-canon.md`](research/04-design-canon.md) | Nine verified resources, and the four to read first |
| [`ui/README.md`](ui/README.md) | What is settled about the surface, and why nothing is built yet |
| [`artifacts/intent_brief.md`](depth-engine/runs/20260828-123823-depth-engine-product-ui/artifacts/intent_brief.md) | Confirmed intent; Q1–Q4 answered |

## The four findings that matter

1. **You already designed the UI's data model.** The engine writes four memory files on every run. They map one-to-one onto four UI regions, and `REGISTER.md` — a closed list with per-row status — is a progress bar that can honestly reach 100%. Every competitor shows a spinner, because a spinner is what you display when you cannot name the denominator.

2. **The UI reads two sources, not one.** The Markdown cannot answer staleness, model routing, or cost — those signals are not in it. The second source is OpenTelemetry. This was the run's most expensive correction (`L-0021`), and it replaced an earlier claim here that five of the eight failures were fixable with pixels alone. They are not.

3. **Developers do not watch long runs — they leave.** So the product is a four-beat loop: start, leave, get pulled back at a gate or a death, land somewhere that answers *what needs me*. Which means **F3 needs a notification, not a heartbeat display** — a dashboard row only helps someone who is already looking. The engine has no notification primitive today (`L-0026`, `L-0027`).

4. **The engine argued against the operator three times and lost every time.** Under Law L-A, this run's central claims were sent to Codex — a different model family — with instructions to overturn them. Five verdicts so far: four overturned, one inconclusive, none clean. Every correction moved *toward* the operator's original instinct. They are recorded in [`research/02`](research/02-what-to-display.md) §1, [`research/05`](research/05-shell-decision.md), and the Ledger — not quietly edited out.

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

Reads `STATE.md`, runs the L-B integrity checks, finds the first open Register row, continues there. Resume mode is **CONTINUE**, pointed at **S11** — decide the notification channel and where the primitive lives in the engine. It blocks any shell build.

## Honest ceiling

A clean walk proves the process ran. It does not prove the output is right.

Specifically, as of this run: **the shell decision has not converged** — 11 Register rows are open, including S2 (does the isolation rule even permit a viewer process) and S10 (no option other than the operator's preference has been seriously argued, which is the shape L-A says to distrust). No user research exists; no developer other than the operator has been asked anything. Codex's cited sources were accepted on citation alone and never opened — twice. Six market figures are quarantined as unverified. Five decisions were made at 110k–180k context and are provisional until reproduced cold. All of it is tracked as open rows rather than left implicit.
