# E5 — Decision sub-question map

**Run:** `20260828-123823-depth-engine-product-ui` · project-type `decision`
**Central decision:** *What shell should the Depth Engine UI ship in for v1, given external developers as the buyer?*
**Leading hypothesis (operator, Q1):** a CLI-served local web app — `depth-engine ui` opens localhost and reads the run directory directly.

> Under L-A the leading hypothesis is the thing to attack, not defend. Every sub-question below is phrased so that a *no* is possible. E8 declares decision-saturation when each row is answered and no open row could flip the decision.

---

## The sub-questions

| # | Sub-question | Why it can flip the decision | Status |
|---|---|---|---|
| **S1** | Does a CLI-served localhost UI have adoption precedent at scale in developer products? | If no mature product ships this way, the pattern is unproven and the risk is unpriced. | open |
| **S2** | Can a local web app read the run directory without violating the isolation rule in `START.md`? | The rule forbids a run reading outside its own directory. If the *viewer* is caught by that rule, the architecture is illegal as specified. | open |
| **S3** | Does "external developers, commercial" break local-only? | No auth, no server, no telemetry means no natural gating point and no usage data. This is the sharpest threat to the hypothesis. | open |
| **S4** | Does local-only foreclose the M1 PM panel, team review, or working from any computer? | The operator explicitly wants to work from any computer. If the shell blocks that, it fails a stated goal. | open |
| **S5** | Can a **read-only** renderer resolve the five observability failures (F3, F4, F5, F7-tracking, F8), or is a live event stream required? | Read-only with no write path is dramatically cheaper. If F3's heartbeat needs live events, v1 scope grows. | open |
| **S6** | **Who opens the UI, and when?** The engine is walked by an agent inside a terminal (Claude Code / Codex). Does a second surface in a browser help, or fragment attention? | The strongest structural objection to the hypothesis. If the developer is already watching a terminal, a browser tab may be a context switch rather than a fix. | open |
| **S7** | Is "your code and research never leave your machine" a real differentiator for this buyer? | If yes, local-only flips from constraint to positioning. If it is merely neutral, S3's commercial cost is unpaid for. | open |
| **S8** | What is the migration path if v1 later needs to be hosted? | Retrofitting auth and multi-tenancy into a local-first architecture is expensive. A one-way door must be identified before it is walked through. | open |
| **S9** | What does each shell cost to build to a demoable state? | Cost is the tiebreaker if S1–S8 do not separate the options. | open |

## Options under evaluation

| Option | Shape |
|---|---|
| **A** | CLI-served local web app (`depth-engine ui` → localhost) — **the hypothesis** |
| **B** | Desktop app (Tauri / Electron) |
| **C** | Hosted web app + local agent daemon |
| **D** | Extension inside Cursor / VS Code |
| **E** | Terminal UI (TUI) — *added by the engine, not offered at the gate.* If S6 resolves against a browser, the honest alternative is not another GUI but a richer terminal surface where the developer already is. |

Option E is the engine's own addition. E5 exists to catch aspects nobody framed; offering only the four options the operator was shown would reproduce the frame rather than test it.

## Saturation criterion (what E8 will check)

The decision is saturated when:

1. Every row S1–S9 is answered with cited evidence, **or** explicitly marked as not-decision-changing with a reason.
2. **S3 and S6 are answered at primary grade**, not by inference — they are the two rows most capable of overturning the hypothesis.
3. At least one option other than A has been argued for seriously enough that a reader could disagree with the conclusion.
4. A cross-family overturn attempt on the final recommendation has been run and survived, or its objections have been incorporated.
5. The one-way doors in S8 are named explicitly.

If the evidence converges but does **not** support building a UI shell now, E8 issues **REFUSAL** and E11 delivers the smaller-scoped intervention the evidence does support. That remains a valid terminal.

## Ceiling

This map is the artifact E8 judges against, so a sub-question nobody framed stays invisible through convergence — the failure mode E5's own honest ceiling names. S6 and Option E were added because the operator's four offered options shared an assumption (that the answer is a GUI). There may be further shared assumptions not yet surfaced.
