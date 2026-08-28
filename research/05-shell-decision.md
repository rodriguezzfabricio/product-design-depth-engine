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

## Still open

**S2** isolation rule vs. a viewer process · **S4** team review and work-from-anywhere · **S6** who opens the UI and when, given the developer is already watching a terminal — *still the sharpest unanswered objection, and the one that could promote Option E (a TUI)* · **S9** cost per option.

S6 has had no research at all. It is designated a primary-grade saturation requirement, and it is unanswered.

## Ceiling

- Codex's citations (Prisma, VS Code Remote SSH, Jupyter security, Storybook, Next.js CLI, TablePlus) are **unopened by this run**. Accepted as argument, not verified. Same defect flagged in `02` §8, now recurring — it is a Register row, not a footnote.
- No option other than A has been argued for seriously. Saturation condition 3 is unmet.
- 6 of 9 sub-questions unanswered. **Do not treat this as a decision.**
