# The IP boundary, BYO-agents, and what the UI can honestly show

**Answers:** *how do we display the engine without leaking how it works* · *is connect-your-own-agent good or bad* · *can we show code changes*.
Run `20260828-123823-depth-engine-product-ui`. **This document supersedes the display model in `02-what-to-display.md` §3.**

---

## 0. Short version

- **Your premise is factually wrong.** Cursor's and Claude Code's prompts *are* public — a 143,196-star repo publishes them. §1.
- **Your conclusion is still defensible.** I over-corrected. Cross-family check: *"it conflates perfect secrecy with economically useful secrecy."* §2.
- **The real problem is not the UI. It is `init`.** Today the engine copies all 22 method files onto the customer's disk. Secrecy is impossible **under today's architecture** — that is an architecture bug, not a display bug. §2.
- **BYO-agent and method protection are NOT mutually exclusive.** I claimed they were; that was overturned. The resolution: connected agents receive **stage-scoped task contracts**, never the whole pipeline. §3.
- **Connect-your-own-agent: good idea, with one caution.** §4.

---

## 1. The premise, checked

> *"it's like cursor you don't see the underlying prompts, same thing with claude code harness we don't ever see it."*

Verified against GitHub's API, 2026-08-28:

| Repo | Stars | Contains |
|---|---|---|
| `x1xhlol/system-prompts-and-models-of-ai-tools` | **143,196** | `Cursor Prompts/`, `Anthropic/` (Claude Code), Devin AI, v0, Lovable, Windsurf, Replit, Warp.dev, +20 more — **including JSON tool schemas** |
| `asgeirtj/system_prompts_leaks` | — | Anthropic (Opus 5, Fable 5, Claude Code), OpenAI Codex, Google, xAI |

People see them. They are on GitHub, updated through 2026, with 28 contributors. What Cursor and Anthropic achieve is **not showing you** — a presentation choice — not protection.

**This does not make your instinct wrong.** It makes the *reasoning* wrong, which matters because you were about to design around a mechanism that does not exist.

## 2. What survived the attack — the distinction that matters

I claimed secrecy was simply unavailable. Cross-family verdict: **INCONCLUSIVE**, and the objection is good:

> "It conflates perfect secrecy with economically useful secrecy. Public prompt extraction proves determined customers can reverse-engineer a system; it does not prove that obscuring prompts has zero value. **Friction, incomplete extraction, update lag, licensing, and trade-secret remedies can still deter commodity competitors.**"

And on whether hidden methods can be real businesses — two counter-examples I had ignored:

- **Stripe Radar.** Customers submit transactions and get scores; Stripe publishes only *"a preview of some signals,"* never the operative model. A hidden method supporting a large commercial product.
- **Renaissance Technologies.** Attributes its position to decades of proprietary strategies. An enduring hidden-method business.

**So the corrected claim is narrower and sharper:**

> Secrecy is impossible **under today's architecture**, because `depth-engine init` writes every stage, law, and protocol file onto the customer's disk. "Impossible forever" is overstated. **"Impossible while `init` ships the method" survives.**

**This is the finding.** Your IP concern is legitimate, and it is not a UI problem at all — it is a **distribution and orchestration-boundary problem** sitting upstream of every display decision. No amount of UI design fixes a `cat` command.

Also from the same verdict, against my open-core suggestion (**OVERTURNED**): open-core *"gives noncustomers immediate cloning material, eliminates extraction effort, enables forks, and weakens trade-secret claims."* Execution, evidence, distribution, cadence **and** a proprietary method can jointly form a moat. It is not either/or, and I framed it as one.

## 3. The resolution I missed

I claimed R-A (connect your own agent) and R-B (don't expose the method) were mutually exclusive. **OVERTURNED**, and the counter is the design:

> "L-A requires a different **model family**, not a customer-supplied second agent or visibility into the entire harness… R-A and R-B become mutually exclusive **only if every connected agent must receive the complete method. That assumption is not in R-A.**"

That is the unlock. The boundary is not *hosted vs local* — it is **orchestration vs execution**.

```
┌──────────────────────────────────────────┐
│  ORCHESTRATOR  — yours, never shipped    │
│  stage sequencing · gates · laws ·       │
│  adjudication · convergence logic        │
└───────────────────┬──────────────────────┘
                    │  emits ONE stage-scoped task contract at a time
                    ▼
┌──────────────────────────────────────────┐
│  EXECUTOR — the customer's own agent     │
│  Claude Code · Codex · Hermes            │
│  sees: this task. not: the pipeline      │
└──────────────────────────────────────────┘
```

An agent receiving *"research these five failure modes and return findings with citations"* learns nothing about E0–E11, the five laws, the gate structure, or how convergence is judged. **The sequencing is the IP. The individual task rarely is.**

And the customer's code need not move: **GitLab's BYOM architecture keeps source code and inference traffic inside the customer's own AWS boundary while GitLab supplies orchestration and governance.** That is the precedent for "our orchestration, your machine, your models" — and it preserves your local-first privacy positioning.

**Cost, stated honestly:** this is a real re-architecture. Today the engine *is* the Markdown, and the agent reads all of it. Moving to contracts means the orchestrator becomes software that runs, not documents that are read. That is the same "make it a harness" conclusion your prior report reached in §9 — arrived at from a completely different direction, which is mild evidence it is right.

## 4. Connect-your-own-agent: validated, with one caution

**Good idea.** Three reasons:

1. **It is not a feature, it is a precondition.** Law L-A mandates a different model family for every load-bearing verdict. Gate G1 in your PDF — *"until codex is in, every verdict in this run is same-family"* — is that requirement failing in practice. Multi-agent support is the method working as specified.
2. **It is checkable, and competitors cannot fake it.** "Authored by Claude, challenged by Codex" is a verifiable property of a run.
3. **The precedent is broad**: Cline, Continue, Aider, and VS Code's own BYOK all ship provider choice for developer tools, where the API-key onboarding tax is acceptable.

**The caution, from the same verdict:** *Sourcegraph offered BYOK/BYOLLM and then discontinued Cody Free and Pro in favour of a more opinionated agentic product.* That does not prove BYO caused the failure — but it disproves the idea that provider choice by itself creates product value. **Model choice is not a differentiator. The cross-family guarantee is.**

### So design it as a guarantee, not a settings page

This is the difference between on-brand and a violation of your "no random buttons" rule:

```
  Author      Claude Code          Challenger   Codex          ✓ cross-family
  Author      Claude Code          Challenger   Claude Code    ⚠ same-family — verdicts unverified
```

One persistent strip. Not a dropdown of eleven providers. It shows whether **the promise you sell is currently true**, and it turns your PDF's G1 gate from a footnote into a visible product state. Adding an agent is a consequence of clicking the warning, not a settings excursion.

## 5. What to display, restated

**The display rule is no longer "show the ledger." It is: show the customer's work, never the engine's machinery.** This serves secrecy *and* Nielsen #2 (match the real world) and #8 (minimalism) at the same time. A paying developer does not want to learn "E5 aspect decomposition."

| Internal (never rendered) | What the customer sees |
|---|---|
| Stages E0–E11 | Plain phases: **Understanding → Researching → Stress-testing → Deciding** |
| Law L-A cross-family check | **"Challenged by a second model"** + `survived` / `challenged` badge |
| `REGISTER.md` rows | **"Your questions"** — 17 of 23 answered |
| `LEDGER.md` entries | **"What we found"** — claim, evidence, link |
| E8 convergence verdict | **Coverage bar** — and it counts rows itself (`L-0023`) |
| Refusal terminal | **"We recommend not proceeding — here's why"** |
| Stage prompts, law text, gate logic | **Never rendered.** Not in a debug view, not behind a toggle |

**What you must still show, or you have no product:** the *evidence*. The value proposition is "this survived attack." Proving it requires showing what was attacked and what survived — the finding, the source, the verdict. **The result is the customer's. The method is yours.** A lab report shows results and a methods summary, not the reagent formula.

This supersedes `02-what-to-display.md` §3, which mapped engine internals directly onto UI regions and would have leaked the pipeline by construction.

## 6. Code changes / diffs

Wanted (F5), and still blocked on the same thing as before:

- Diffs need **git or worktree access**, which is likely *outside* the isolated run directory that `START.md` confines a run to. That is open sub-question **S2**, still unanswered.
- Under §3's architecture the diff is *executor-side* — the customer's agent edits the customer's files on the customer's machine. So the diff is customer data, never engine internals. **No IP tension here at all.** It is purely a permissions question.
- Cursor's answer is worth copying: the review surface is a **PR**, not a bespoke diff viewer. Developers already know how to review a PR, and it costs you nothing to build.

## 7. What this does to the shell decision

The orchestration boundary is now **upstream** of the shell choice, and it partially destabilises Q1:

- A pure local web app with the method on disk **cannot** satisfy R-B.
- An orchestrator-hosted / executor-local split **can**, and GitLab shows code need not leave the customer's boundary.
- That is closer to "hosted control plane + local execution" than to the pure local-first shell chosen at the E1 gate.

**S12 opened:** where does the orchestration boundary sit, and does R-B survive contact with its cost? Until that is answered, the shell decision cannot converge — it now depends on it.

## 8. Honest ceiling

- Codex's citations — Stripe Radar, Renaissance, GitLab/AWS BYOM, Sourcegraph's Cody changes — are **unopened by this run**. Third recurrence of accepting citations as argument. It is Register row `R5`.
- The repo star counts and file listings in §1 **were** verified directly against GitHub's API.
- §3's contract architecture is Codex's sketch plus my elaboration. **No implementation exists and none was probed.** Whether stage-scoped contracts actually preserve engine quality is untested and is the obvious thing to prove with a thin slice.
- Nothing here is legal advice. "Trade-secret remedies" came from the cross-check; whether your `UNLICENSED` posture plus existing disclosures supports that is a question for a lawyer, not an agent.
- No customer has been asked whether they would connect their own agent, or whether they care that the method is hidden.
