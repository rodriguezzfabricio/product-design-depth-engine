# The shell decision — evidence so far

**Decision run.** Central question: *what shell should the Depth Engine UI ship in for v1, given external developers as the buyer?*
**Leading hypothesis (operator):** Option A — CLI-served local web app, `depth-engine ui` → localhost.
**Status:** NOT converged. 3 of 9 sub-questions answered. E8 has not run.
Sub-question map: [`decision_subquestions.md`](../depth-engine/runs/20260828-123823-depth-engine-product-ui/artifacts/decision_subquestions.md)

---

## What the cross-family pass returned

Three claims went to Codex with instructions to overturn. **One inconclusive, two overturned.** None survived clean. Full verdict in Ledger `L-0020`/`L-0021`.

### S1 + S7 — "localhost has precedent, and local-only is a feature" → **INCONCLUSIVE**

My precedent list was **Storybook, Jupyter, Vite, `next dev`, Prisma Studio**. Codex's objection:

> "The precedents are category errors. Storybook, Vite, and `next dev` are free development infrastructure, not standalone commercial workflow products. Prisma pairs local Studio with a hosted collaborative Console; local-only was not sufficient for team use."

That lands. Every product I named is either free infrastructure or has a hosted companion. **They do not evidence that a paid, standalone, local-only workflow product succeeds.** The one genuine counterexample came from Codex, not me: **TablePlus** — a commercial local database client with perpetual licensing.

Two further objections worth recording:

- **Remote development breaks the core assumption.** SSH sessions, containers, Codespaces, and devboxes mean the run directory is frequently *not* on the machine running the browser. VS Code requires explicit port forwarding to reach a localhost service. A meaningful share of your target users do not develop on the laptop in front of them.
- **Localhost is not secure.** Jupyter enables token authentication by default because a local server reachable from a browser is an attack surface. A server that reads source code needs: loopback-only binding, a random session token, path confinement, CSP, and origin checks. **v1 requirements, not later hardening.**

**Verdict:** local privacy is a credible feature. It is **not** established that this is the right shell. S1 and S7 stay open, and the precedent argument must be rebuilt around *commercial* local tools.

### S3 — "commercial + external breaks local-only" → **OVERTURNED (good news)**

I claimed the shell forces open-core, license-key, or a hosted tier, and that the choice had to be made now. Wrong on both halves:

> "The shell does not force those three business models, and it does not preclude telemetry. Storybook and Next.js collect optional anonymous telemetry despite running locally. Entitlement can occur at package download, CLI launch, update delivery, or premium-command execution."

**Revised:** local-first does not corner you commercially. Entitlement has at least four insertion points that are not account auth. Codex's actual guidance is narrower and better:

> "Decide distribution and entitlement boundaries now. Do not prematurely design account auth for a product that may never need identity. Retrofitting hosted collaboration is substantial; adding opt-in telemetry or CLI license validation is not."

So S8's one-way door is **hosted collaboration**, not telemetry and not licensing. That is the only thing that must be decided early.

### S5 — "a read-only renderer resolves five failures" → **OVERTURNED**

The most consequential correction of the run. The Markdown files do not carry the signals:

| Failure | Required signal | In the Markdown? |
|---|---|---|
| F3 staleness | heartbeat / process events | No |
| F4 actual model | runtime dispatch metadata | No |
| F7 cost | telemetry events | No |
| F5 diffs | git / worktree access, likely outside the isolated run dir | No |
| F8 readability | semantic transformation, not rendering | No |

> "Polling, file watching, parsing partial writes, clock-based liveness, and derived status **are** state management. A read-only renderer can improve readability and display REGISTER progress; it cannot honestly claim to resolve all five failures."

Also: a CLI-served browser app **already has a backend** — the CLI's own HTTP/file server. "No backend" was never true.

**Revised S5 answer:** a pure renderer delivers orientation (coverage bar, readable ledger, state header, navigation). Every failure fix needs a signal source that does not exist yet.

## The unlock — and it was already on your list

The missing F4 and F7 signals are **already being emitted and merely uncollected**. From the prior report's Tier-1 build item #2:

> "Turn on telemetry. `CLAUDE_CODE_ENABLE_TELEMETRY=1`, point the exporter somewhere. **Effort: minutes.**"
>
> Emits `claude_code.api_request` with `model`, `input_tokens`, `output_tokens`, `cache_read_tokens`, `cost_usd`, `request_id`; and `claude_code.token.usage` / `claude_code.cost.usage` with `model`, `agent.name`, `skill.name`, `effort`, `speed`.

`model` per request is F4. `cost_usd` and tokens per `agent.name` are F7's tracking half. **The UI's hardest data problem is a config flag you have not set.**

That leaves **F3 (staleness)** as the only one needing new engine work: a timestamp written per active agent, so elapsed time is computable. Small, and it is the honest price of the fix.

## Revised build sequence

| # | Step | Effort | Unblocks |
|---|---|---|---|
| 0 | `CLAUDE_CODE_ENABLE_TELEMETRY=1`, exporter to a local file | minutes | F4, F7-tracking |
| 1 | Renderer over the 4 Markdown tiers — coverage bar, ledger, state, index | days | orientation; the hero screenshot |
| 2 | Fold in the telemetry stream — model panel, cost meter | days | F4, F7-tracking |
| 3 | Heartbeat: engine writes a per-agent timestamp | small engine change | F3 |
| 4 | Diff view — needs git access, resolve against the isolation rule | design work | F5 |
| 5 | `humanizer` pass on rendered output, raw toggle | already installed | F8 |

Security is not a step — loopback binding, session token, path confinement, CSP, and origin checks belong in step 1.

## S6 — "who opens the UI, and when?" → **the question was framed wrong**

I framed S6 as *terminal vs. browser while watching a run*. Research killed the premise: **for long-running agent work, the developer does not watch. They leave.**

What the products actually do:

| Product | What happens while it runs | How the developer comes back |
|---|---|---|
| **Cursor Background Agents** | Runs remotely, writes to a branch | Opens a **PR with a summary**, then notifies by **email + desktop notification + Slack** |
| **GitHub Actions** | Runs on CI | `gh run watch` streams in the terminal until settled; web UI for review |
| **Agent-watch tooling generally** | Returns a watch ID immediately, streams to a bounded widget | Reports final status back when the run settles |

And the documented caution, which matters for your F3 instinct: *monitors should remain selective, since every output line interrupts.* A firehose is not observability.

### What this does to the design

**The primary job is not "watch a run." It is a four-beat loop:**

1. **Start** — one action.
2. **Leave confidently** — know it is running and know it will fetch you.
3. **Get pulled back at the right moment** — a gate, a death, or a terminal.
4. **Land somewhere that answers "what happened, what changed, what needs me"** — and decide in under a minute.

**This partly rescues Option A.** The "a browser tab fragments attention" objection weakens badly, because you are not meant to be staring at it. You are pulled to it. A surface you visit on notification is not a competing window; it is a destination.

**But it surfaces a requirement no source in this run had named: the engine has no notification primitive.** Not in the Markdown, not in the telemetry. That is a gap in the engine, not in the UI.

### F3 was misdiagnosed — by me, and arguably in the original failure log

F3 reads: *"subagents kept dying and the engine never noticed. The operator sat waiting, then checked by hand."*

I mapped that to a heartbeat indicator. **A heartbeat display only helps someone who is looking at it** — and the whole point is that he had left. F3's real fix is a **notification**, not a dashboard row.

That is a sharper and cheaper fix than the UI work it was queued behind. It also means the engine's **hard gates are the natural notification triggers** — the E1 confirm gate, the E2/E5 sign-offs, the E11 review, plus agent death and terminal. Those are precisely the moments the operator must be fetched.

### Revised S6 verdict

- The shell matters **less** than the notification channel. Both a browser and a TUI can be notified into.
- **Option E (TUI) is not promoted** on attention grounds — the attention objection largely dissolves.
- New blocking work, ahead of any shell build: **decide the notification channel** (OS notification, terminal bell, email, Slack) and **add the primitive to the engine.**
- Cursor's review surface is a **PR**, not a dashboard. Worth taking seriously: the Depth Engine's terminals — scaffold, decision, refusal — may want to land as a document or PR the developer already knows how to review, with the dashboard reserved for a run in flight.

## Still open

**S2** isolation rule vs. a viewer process · **S4** team review and work-from-anywhere · **S7** is local-only decisive for this buyer · **S9** cost per option · **S10** argue an option other than A seriously.

**S11 (new, from S6):** what is the notification channel, and where does the primitive live in the engine?

## Ceiling

- Codex's citations (Prisma, VS Code Remote SSH, Jupyter security, Storybook, Next.js CLI, TablePlus) are **unopened by this run**. Accepted as argument, not verified. Same defect flagged in `02` §8, now recurring — it is a Register row, not a footnote.
- No option other than A has been argued for seriously. Saturation condition 3 is unmet.
- 6 of 9 sub-questions unanswered. **Do not treat this as a decision.**
