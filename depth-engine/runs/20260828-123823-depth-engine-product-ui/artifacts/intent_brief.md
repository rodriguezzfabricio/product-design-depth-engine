# Intent Brief — CONFIRMED

**Run:** `20260828-123823-depth-engine-product-ui`
**Stage:** E1 · **Step 6 confirm gate CLEARED 2026-08-28**
**Status:** the operator answered Q1–Q4. Accepted `[engine-inferred]` lines are upgraded to `[engine-inferred — operator-confirmed]` per E1 Step 6; they are **not** reclassified as `[operator-stated]`. E2 may load.

## Operator answers (E1 MOVE 3 → confirm gate)

| # | Question | Answer |
|---|---|---|
| **Q1** | Which shell | **Local web app served by the CLI** — `depth-engine ui` opens localhost, reads the run directory directly. No Electron, no hosted infra, no auth. |
| **Q2** | First user | **External developers, as a product.** Not internal-only. |
| **Q3** | Sequencing | **Decision run on the shell first**, then a separate build run for the surfaces. |
| **Q4** | Canonical depth-engine repo | *"Totally diff and new repo and make it private"* — **ambiguous, see `[unknown]` in §4.** Not blocking the shell decision; blocking E2 research that reads engine source. |

**Consequence of Q1 + Q3 read together:** the operator has named a preferred shell *and* asked for the decision to be run properly. These are not in conflict. Q1 becomes the **leading hypothesis the decision run must try to overturn**, not a settled answer. Under L-A, a convenient answer earns more scrutiny, not less — so the E5 sub-questions are framed to attack it.

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
- **RESOLVED at the confirm gate:** shipping to external developers **is** the target. The product is commercial and external, so nothing may assume the user wrote the engine. `[operator-stated]`
- **Still unresolved:** which depth-engine repository is canonical. The operator answered *"totally diff and new repo and make it private"*, which does not identify an existing repo. This run's engine recon was performed against the local clone `~/.depth-engine/repo`. `[unknown — flag for E2]`

## 5. Project-type

**CONFIRMED: `decision` first, then a separate `build` run.** `[engine-inferred — operator-confirmed]`

E8 therefore applies **decision-saturation** convergence to this run: it converges when the shell decision is answerable and remaining open sub-questions would not change it. E5 produces `decision_subquestions.md`, not an aspect map. A CONVERGED verdict routes to **E11 directly** — E9 and E10 are skipped for a decision-mode run.

E1 Step 5 states: *"When the seed is ambiguous about project-type — for instance, the operator says 'I want to build X' but the real question is whether X is worth building — surface the distinction explicitly. An ambiguous project may be a decision project first and a build project second."*

The seed contains both. "I don't know [whether] to use a web app or app" is a decision with an E8 saturation test. "I don't know what to display" is a build with an E8 aspect-coverage test. Running them as one project means E8 cannot pick a convergence mode — a structural failure, not a preference.

---

## Residual open item after the gate

**Q4 is not resolved.** The operator answered *"totally diff and new repo and make it private"*, which states an intent but does not name a repository. Two readings survive:

1. The canonical depth-engine should be moved to a new private repo that does not exist yet — an action to take, not a fact to record.
2. The answer was directed at *this* design repo, which was already created private as `rodriguezzfabricio/product-design-depth-engine`.

Under **X-009** from the prior report — *"verifying an artifact is not verifying it is the artifact you asked for"* — this stays `[unknown]` rather than being guessed. It does **not** block the shell decision, which depends on the engine's architecture (already read from the local clone) rather than on which remote hosts it. It **does** block any E2 research that reads engine source as authoritative.

## Ceiling on this brief

A confirmed Intent Brief is not proof of completeness (E1 §Honest ceiling). Confirmation means you agree with what is written — not that everything load-bearing has been written. Gaps in the candidate-question generation propagate silently through the confirm gate. E2 and E3 are the earliest catch-points.
