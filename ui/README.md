# ui/ — the Depth Engine product surface

**Nothing is built here yet, on purpose.** The shell decision has not converged. Building before it does would be the mistake this whole run exists to avoid.

> AI-written documentation (Claude Code), run `20260828-123823-depth-engine-product-ui`.

## Current state

| | |
|---|---|
| **Leading hypothesis** | Option A — CLI-served local web app: `depth-engine ui` opens localhost |
| **Confidence** | Not established. Cross-family check returned 1 inconclusive + 2 overturned, nothing clean |
| **Blocking** | S6 (who opens the UI, and when) has had zero research and could promote Option E, a TUI |
| **Decision record** | [`research/05-shell-decision.md`](../research/05-shell-decision.md) |

## What is settled

**The data model.** Whatever shell wins, it renders the same four things, because the engine already writes them:

| Source | UI region |
|---|---|
| `REGISTER.md` | Coverage bar — **the hero**. A closed list, so the denominator is real |
| `LEDGER.md` | Timeline / audit feed |
| `STATE.md` | "Where am I" header |
| `INDEX.md` | Navigation |

**The UI reads two sources, not one.** This was the run's most expensive correction (`L-0021`). The Markdown alone cannot answer staleness, model routing, or cost — those signals are not in it. The second source is OpenTelemetry:

```
run directory (Markdown)  ──┐
                            ├──►  UI
OTel stream (model, cost) ──┘
```

**Hard rule, from `L-0023`:** the coverage bar **counts register rows itself**. It never reads a summary line — including the one written at the top of `REGISTER.md`, which was wrong in all four of its numbers when a script checked it.

**Security is not deferred.** A localhost server that reads source code is an attack surface. Jupyter ships token auth by default for this reason. Loopback-only binding, random session token, path confinement, CSP, and origin checks are v1 requirements.

## Build order (once the shell is decided)

| # | Step | Unblocks |
|---|---|---|
| 0 | Telemetry + a local collector writing to file | F4, F7-tracking |
| 1 | Renderer over the four Markdown tiers + security baseline | Orientation; the hero screenshot |
| 2 | Fold in the telemetry stream — model panel, cost meter | F4, F7 |
| 3 | Per-agent heartbeat timestamp (small engine change) | F3 |
| 4 | Diff view — needs git access; resolve against the isolation rule | F5 |
| 5 | `humanizer` pass on rendered output, with a raw toggle | F8 |

## Design constraints carried from the run

- **One persistent control** (the thoroughness dial, M7) and **one persistent action** (start/stop a run). Everything else is a view of state. This is not restraint — the engine genuinely has one knob.
- **The PM panel is the default view** (M1), not the raw engine feed. The raw feed is a tab you can open.
- **Every persistent control must trace to a documented failure or mechanism.** One that doesn't is a defect, not a feature.

## Before writing any code here

Run the design pipeline that is already installed (see [`research/01-tooling-audit.md`](../research/01-tooling-audit.md) §6):

```bash
npx skills add uizze/uizze
npx skills add anthropics/skills
```

Then `design-consultation` → `anti-ui-slop` (writes `.uizze/design-contract.md`, freeze it) → `design-shotgun` → `dataviz` → `design-html` → `design-review` → `humanizer`.
