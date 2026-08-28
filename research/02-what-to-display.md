# What to display in the UI

**Answers seed asks A6 (what to display), A7 (web vs app), A9 (new PDF features), A10 (does the task make sense).**
Run `20260828-123823-depth-engine-product-ui`, stage E1 MOVE-2 → feeds E5.
**Status:** two load-bearing claims were **overturned** by cross-family check. This document states the revised position, and §1 shows the overturn rather than hiding it.

---

## 1. Two things I got wrong, corrected before you build on them

Under Law L-A, I sent my two central claims to Codex (a different model family) with instructions to overturn them. Both came back **OVERTURNED**. The corrections are load-bearing, so they go first.

### Overturn 1 — "don't build it like Cursor" was wrong

**What I claimed:** Cursor is an editor; the Depth Engine is a long-running run; therefore Cursor is the wrong model and the precedents are CI/CD views and trace viewers.

**What Codex answered:** the category boundary is false. Cursor **Background Agents** are asynchronous runs users launch, leave, monitor, redirect, and review, with status, diffs, and PR handoff exposed on web and mobile. GitHub Copilot's coding agent turns an issue into an autonomous run reviewed as a pull request. *Cursor itself is the counterexample.*

> "Making RUN the data model is sensible; concluding 'therefore not Cursor-like' is not. Depth Engine eventually emits scaffolds and code, and F5 demands diff inspection. Separating run supervision from the editor could create a costly context switch exactly when users must inspect, edit, test, and accept the result."

**Revised position.** Your "kind of like Cursor" instinct was closer to right than my correction was. The RUN is still the right primary object — that part survived. But run supervision and code inspection must not be split, because your own F5 (diff visibility) lives exactly at the seam. **Study Cursor Background Agents as the nearest precedent, not as the wrong analogy.**

### Overturn 2 — "the UI can't fix your failures" was too absolute

**What I claimed:** F1–F8 are enforcement failures, not presentation failures, so a UI would be a skin over the same problems and the enforcement layer must come first.

**What Codex answered:** a sound warning wrapped around a false absolute. A GUI *directly* improves:

| Failure | What the UI alone fixes |
|---|---|
| **F3** stale/dying subagents | elapsed-time, last-event, heartbeat indicators |
| **F4** invisible model routing | display **requested vs. actually selected** model |
| **F5** diff visibility | structured file-level diffs |
| **F7** token burn | live token and cost accounting (the *tracking* half) |

> "LangSmith is the concrete counterexample: its trace UI records each agent step and exposes latency, errors, token consumption, and cost without needing to become the agent's execution runtime… 'enforcement layer first' is an unnecessary sequencing constraint. Instrumentation plus a thin run UI could validate which controls users actually need before building a heavyweight orchestrator."

**Revised position, and this is the answer to A10.** Your task makes sense. Build the UI first — but build it as **instrumentation**, and know precisely which half of your pain it treats.

## 2. The two halves — the sharpest thing in this document

Your eight failures split cleanly, and the split *is* the product plan.

| | **Observability half — a UI fixes this** | **Enforcement half — a UI cannot fix this** |
|---|---|---|
| | F3 stale agents → heartbeat | F1 no stopping point |
| | F4 invisible routing → model panel | F2 thoroughness not adaptive |
| | F5 diff blindness → diff view | F7 *cap* — blocking spend needs a hook |
| | F7 *tracking* → cost meter | |
| | F8 AI language → humanized copy | |
| **Fix medium** | pixels | code that runs: hooks, `maxTurns`, blocking checks |
| **Ship** | **now** | after — informed by what the UI reveals |

Five of eight are surface-fixable. That is a real first release.

The narrow claim that survived Codex: **a UI cannot guarantee stopping, liveness, routing, or budget caps.** Display a number ≠ enforce a limit. So do not let the cost meter imply a cap that does not exist — that would be a fail-open gate wearing a fail-closed label, the exact defect X-004 in your prior report.

> ### ⚠ CORRECTION — the table above is half wrong. Read this before building from it.
>
> A second cross-family pass (2026-08-28, Ledger `L-0021`) **overturned** the implied claim that a read-only renderer of the Markdown files delivers those five fixes. Codex's objection is concrete and correct: **the Markdown does not contain the required signals.**
>
> | Failure | Signal the UI needs | Is it in the Markdown today? |
> |---|---|---|
> | F3 staleness | heartbeat / process events | **No** |
> | F4 actual model | runtime dispatch metadata | **No** |
> | F7 token cost | telemetry events | **No** |
> | F5 diffs | git / worktree access — likely *outside* the isolated run directory | **No** |
> | F8 readability | semantic transformation, not rendering | **No** |
>
> What a pure renderer *can* honestly deliver: **REGISTER coverage progress, LEDGER readability, STATE orientation, INDEX navigation.** That is still worth building — but it is four regions of orientation, not five failure fixes.
>
> **The unlock is already in your own Tier-1 list.** The prior report's build item #2 is *"Turn on telemetry. `CLAUDE_CODE_ENABLE_TELEMETRY=1`, point the exporter somewhere. Effort: minutes."* That emits `claude_code.api_request` with `model`, `input_tokens`, `output_tokens`, `cost_usd`, and `claude_code.token.usage` with `agent.name` and `effort`. **Those are exactly the F4 and F7 signals the Markdown lacks** — and per §8 of that report, they are already being emitted and merely uncollected.
>
> **Revised sequence:** (1) turn on telemetry — minutes; (2) build the renderer over Markdown *plus* the telemetry stream; (3) F3 needs one more thing neither source has — a heartbeat, which means the engine must write a timestamp per active agent. That is a small engine change, and it is the honest price of the staleness fix.
>
> Also from that pass: **a CLI-served localhost server that reads source code is an attack surface.** Jupyter ships token auth by default for exactly this reason. Loopback-only binding, a random session token, path confinement, CSP, and origin checks are v1 requirements, not hardening for later.

## 3. What to display — you already designed it

You said "I don't know what to display." **You do.** The data model is already written, and it is the four memory files the engine creates on every run. They map one-to-one onto four UI regions:

| Engine file | What it is | UI region | Why it earns the space |
|---|---|---|---|
| **`REGISTER.md`** | coverage register — one row per tracked item, with status | **The progress bar with a real denominator** | The single most important object. See §4. |
| **`LEDGER.md`** | append-only record of every action, finding, decision, null-result | **Timeline / audit feed** | Your L-E law made visible; every claim links to evidence |
| **`STATE.md`** | resume snapshot — current stage, open threads, blocked items | **Persistent header: "where am I"** | Answers Nielsen heuristic #1 in one glance |
| **`INDEX.md`** | table of contents over the ledger | **Navigation / search** | Makes the ledger queryable instead of scrollable |

Plus the pipeline itself:

| Engine structure | UI region |
|---|---|
| Stages **E0 → E11** with hard gates | **Pipeline rail** — GitHub Actions-style, gates rendered as gates |
| Law **L-A** cross-family checks | **Verdict badges**: `survived` / `challenged` / `inconclusive` |
| Three terminals | **Outcome card** — scaffold, decision, or refusal, all three as first-class results |

**Nothing here is invented.** Every region renders a file the engine already writes. That is why this is a design problem you can actually finish: the schema exists, and it was designed by the person who has to live with it.

## 4. The Register is the whole product

If you take one thing: **the coverage register is your primary UI object, and it is the visual fix for F1.**

Your own prior report, §5.1, established the mechanism: a model's softmax is a normalized distribution over ~250,000 tokens with no null entry, so asking "any more questions?" has no false branch — the gate's *no* wire was never connected. The fix it prescribed was structural: enumerate the aspects, **close the list**, converge when every item is covered.

A closed list with per-row status is *exactly* a progress bar that can reach 100%.

```
Coverage   ███████████████░░░░░  17/23 covered · 4 open · 2 challenged
```

That bar is only honest because the denominator is closed. Every other agent product shows a spinner, because a spinner is what you display when you cannot name the denominator. **You can name it.** That is the one screenshot that sells this product, and no competitor can copy it without first solving the stopping problem.

Design consequence: the register row is your atomic component. Item · type · status · evidence link · challenge verdict. Get that one component right and most of the UI falls out of it.

## 5. The PDF's new features, mapped to UI (A9)

The PDF is not a feature spec — it is a failure-and-mechanism seed. Its mechanisms M1–M7 still imply concrete surfaces:

| From PDF | UI surface |
|---|---|
| **M1** PM with isolated judgment; operator talks to the PM | **The PM panel is the default view.** Plain-language "where the project stands, where it's going, what to look into." The raw engine feed is a second tab you *can* open, not the thing you land on. This is the biggest structural implication in the PDF. |
| **M2** Staleness watchdog | Heartbeat dot + "last event 4m ago" per agent; a dead agent turns red without you asking |
| **M3** Routing applied + visible model panel | **Model panel**: agent · task · requested model · actual model. Show the mismatch. Anti-patterns as warnings — Haiku on architecture, Fable on doc-reading |
| **M4** Lossless humanization | Every string passes `humanizer`. A "show raw" toggle keeps it lossless — humanized by default, verbatim on demand |
| **M5** Senior SWE discipline (DRY/TDD/CI) | Test status inline on the build-probe (E9) card |
| **M6** Automatic MR documentation | Doc-diff preview on the outcome card |
| **M7** "Good enough" gate + thoroughness dial | **The one control that earns a place in the chrome.** A mode dial: `get-it-done` ↔ `full research`. You said no random buttons — this is not random, it is F2's fix and the only setting the operator genuinely owns |
| **G1** codex login gate | **Cleared this run.** Codex answered; the overturns in §1 are real cross-family verdicts, not simulated |

**Design rule this implies:** the UI has exactly **one** persistent control (the thoroughness dial) and **one** persistent action (start/stop a run). Everything else is a view of state. That satisfies your A8 constraint — "no random buttons, drop down menu" — not by restraint, but because the engine genuinely has one knob.

## 6. Web app or desktop app (A7) — the honest answer

I am **not** resolving this here, because it depends on one fact only you have. It is the first question in the E1 interview.

The trade is concrete:

| | Web app | Desktop / local |
|---|---|---|
| Runs live where the files are | ✗ needs an agent/daemon on the dev machine | ✓ reads `depth-engine/runs/` directly |
| Zero-install demo, shareable link | ✓ | ✗ |
| Team/collaborative review | ✓ | ✗ |
| Matches Cursor's actual shape | Cursor is desktop **plus** web for background agents | — |

**Structural fact that constrains it:** the engine's state is Markdown files on a developer's laptop, inside their git repo, and the isolation rule in `START.md` forbids a run reading anything outside its own directory. A pure web app cannot see those files without you shipping a local agent. That is not a blocker — it is a scope item you would be choosing.

Cursor's own answer was **both**: desktop for the work, web/mobile for supervising background runs. Given the overturn in §1, that is the precedent to weigh.

## 7. What "does my task make sense" actually resolves to

Yes — with three corrections:

1. **"Like Cursor" is right, for a reason you didn't state.** Not because it is an editor, but because Cursor Background Agents already solved run-supervision UX for a mainstream audience. Copy that shape, not the autocomplete.
2. **Your task is two projects, and you bundled them.** "Web app or app?" is a **decision**. "What do I display?" is a **build**. Per E1, an ambiguous project is a decision project first and a build project second. Decide the shell, then build the surfaces — otherwise you will design twice.
3. **You are not designing a product no one has ever seen.** You said that three times, and it is the belief making this feel impossible. The *engine* is novel. The *interface* is a supervised-run view, and there are at least five mature precedents (Cursor Background Agents, GitHub Actions, LangSmith, Copilot coding agent, Linear's issue view). What is genuinely new is one thing — **a coverage denominator that closes** — and that is the thing to make the hero of the design.

## 8. Honest ceiling

- §1's overturns are Codex's reasoning, checked once. Codex cited Cursor and LangSmith documentation URLs; I have **not** independently opened those docs. Verify before treating the Cursor Background Agents comparison as settled.
- No user research. Zero developers other than you have been asked what they would want to see. Everything here is derived from your failure log and from precedent, not from observed use.
- §3's file→region mapping is mine and has **not** been cross-checked. It is clean, which under L-A means it deserves more scrutiny, not less.
- The register-as-hero argument in §4 rests on your prior report's §5.1 mechanism, which that report itself labels "a strong hypothesis… not an established result."
- Business/market figures are deliberately **absent** from this document. What I could retrieve came from SEO listicles that fail your R3 standard. See `03-market-and-business.md` for what survived and what did not.
