# Intent Brief — DRAFT (not yet operator-confirmed)

**Run:** `20260828-123823-depth-engine-product-ui`
**Stage:** E1 · Step 5 drafted · **Step 6 confirm gate NOT cleared**
**Status:** every `[engine-inferred]` line below is INTERPRETIVE under L-E until the operator answers. This file is a draft; per E1 it may not be treated as `intent_brief.md` proper until an explicit YES.

---

## 1. Mission

- Design the product surface — the UI and its shell — for the Depth Engine, so that operating a run stops requiring the CLI plus a manual paste-into-a-fresh-chat ritual. `[operator-stated]`
- The surface must be intentional throughout: reasoned color, minimal friction, no arbitrary controls, immediate legible value. `[operator-stated]`
- It must cover the mechanisms in the 2026-08-26 meta-run (M1–M7), not only the shipped v1 stage/law model. `[operator-stated]`
- **Reframed:** the work splits into a *decision* (what shell — web, desktop, or both) and a *build* (what the surfaces show). These have different convergence tests and should not be run as one project. `[engine-inferred]`

## 2. Operator-edge

- Fabricio is the engine's operator and co-author: the eight failures (F1–F8) are lived, reproduced across three harnesses, not surveyed. Designing from a first-hand failure log is a real edge over designing from personas. `[operator-stated]`
- Access to a Disney product-design mentor, already supplying canon-grade starting sources. `[operator-stated]`
- The engine's data model is already authored and stable — four memory tiers plus a 12-stage pipeline. The UI has a real schema to render rather than one to invent. `[engine-inferred]`
- Self-described as not yet a senior engineer, and explicitly wants the engine to establish the quality bar rather than assert one. Recorded as a stated constraint on how findings must be justified, not as a limitation. `[operator-stated]`

## 3. Success criteria

- The operator can start a run, leave, return, and understand its state without opening a Markdown file or pasting output into another chat. `[engine-inferred]`
- Each of F3, F4, F5, F7-tracking, and F8 has a named surface that addresses it — the five the cross-family check confirmed a UI can fix. `[engine-inferred]`
- Every persistent control in the UI traces to a documented failure or mechanism. A control with no such trace is a defect. `[engine-inferred]` — direct operationalization of `[operator-stated]` "no random buttons, drop down menu"
- A single frame communicates the product's value without narration. Candidate: coverage bar with a closed denominator. `[engine-inferred]`
- Design decisions cite a source or a run finding. `[operator-stated]` — the seed's demand for psychology and intentionality, plus standing rules R2/R6

## 4. Explicit non-goals

- Not building the enforcement layer (binding caps, blocking hooks, stale-agent reaper) in this run — it is the separate, larger half of F1/F2/F7. `[engine-inferred]`
- Not modifying engine behavior: no stage, law, or protocol file is edited by this run. `[engine-inferred]`
- Not a full brand identity — logo, marketing site, naming. `[engine-inferred]`
- Not competing with Cursor as a code editor; the overlap that matters is supervised background runs. `[engine-inferred]`
- **Unresolved:** whether shipping a commercial product to external developers is in scope for *this* run or a later one. `[unknown — flag for E2/E3]`

## 5. Project-type

**Proposed: `decision` first, then a separate `build` run.** `[engine-inferred]`

E1 Step 5 states: *"When the seed is ambiguous about project-type — for instance, the operator says 'I want to build X' but the real question is whether X is worth building — surface the distinction explicitly. An ambiguous project may be a decision project first and a build project second."*

The seed contains both. "I don't know [whether] to use a web app or app" is a decision with an E8 saturation test. "I don't know what to display" is a build with an E8 aspect-coverage test. Running them as one project means E8 cannot pick a convergence mode — a structural failure, not a preference.

---

## Open questions for the operator (E1 MOVE 3)

Only what research could not resolve. Everything else was self-answered and recorded in the Ledger.

| # | Question | Why it is irreducible |
|---|---|---|
| **Q1** | **Which shell** — web app, desktop app, both (Cursor's answer), or an extension inside an existing editor? | Depends on your distribution intent, not on research. Structural constraint: engine state is Markdown inside a developer's local git repo, and `START.md`'s isolation rule forbids reading outside the run directory — so a pure web app requires shipping a local agent. That is a scope choice only you can make. |
| **Q2** | **Who is the first user** — you and your team, or external developers? | Changes nearly every downstream decision: onboarding, defaults, whether the four memory files can be exposed raw. An internal tool can assume the operator wrote the engine. A product cannot. |
| **Q3** | **Decision run first, or build now?** | Sets E8's convergence mode (§5). If you want the shell resolved with a saturation argument, that is a decision run. If you have already decided the shell, say which and this becomes a build run today. |
| **Q4** | **Which depth-engine repo is canonical?** | Your seed gives `endegenaassefa/depth-engine`; your own `START.md` records the remote as `rodriguezzfabricio/depth-engine`. I used the local clone at `~/.depth-engine/repo`. Your prior report's **X-009** established the exact gate this triggers: *"Verifying an artifact is not verifying it is the artifact you asked for."* Confirming before more research is spent. |

## Ceiling on this brief

A confirmed Intent Brief is not proof of completeness (E1 §Honest ceiling). Confirmation means you agree with what is written — not that everything load-bearing has been written. Gaps in the candidate-question generation propagate silently through the confirm gate. E2 and E3 are the earliest catch-points.
