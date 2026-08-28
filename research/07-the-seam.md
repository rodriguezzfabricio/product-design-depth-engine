# The seam — how to design for a boundary you build later

**Operator decisions, 2026-08-28:** IP boundary = *design the seam now, build it later* · ambition = *real venture, shipping to paying users* · buyer = **not known yet** · notifications = *all operating systems*.

---

## 0. The loudest thing first

You answered "real venture, shipping to paying users" and "don't know who's paying yet." **Those two answers are in tension, and resolving it is now the highest-value work available** — higher than any design artifact in this repo.

Everything downstream forks on it. A solo developer on their own laptop makes local-first correct and makes team features waste. A small team is where Prisma found local-only insufficient and had to add a hosted Console. An enterprise buyer makes your append-only ledger — a record you add to but never edit, so it is tamper-evident — genuinely valuable as a compliance artifact, and makes SSO and procurement unavoidable.

**Concrete next step, and it is not a research pass by me:** talk to 5–10 developers who already run Claude Code or Codex on real work. Ask what happens today when an agent burns an hour and returns something they don't trust. Do not pitch. The question that matters is whether "it survived an attack by a second model" is worth paying for, or whether they just re-run the agent and eyeball it. **Nobody except you has been asked a single question about this product.** For a real venture that is the biggest open risk in the register, and no amount of further design reduces it.

## 1. What "designing the seam" actually means

You chose to keep shipping local Markdown now, while designing so orchestration can move server-side later without a rewrite. That is only real if it constrains how you write stages **starting today**. Otherwise it is a good intention that decays — which your own history says happens to every rule not written as code.

The seam is one rule:

> **Every stage must be expressible as a self-contained task contract that reveals nothing about the pipeline.**

A task contract is the single instruction the orchestrator — the part that decides which step runs next, when to stop, and how to judge the result — hands to an executor, which is whatever agent the customer connected. Self-contained means the executor needs nothing else to do the job. Reveals nothing means an executor completing it learns no more about your method than a contractor learns about a building by installing one window.

## 2. The contract shape

```yaml
task_id:      t-0007
role:         challenger          # researcher | challenger | builder | verifier
objective:    >                   # one plain sentence, no jargon from your method
  Attempt to overturn the claim below. Default to skeptical.
  Flattering agreement is a failure.
inputs:                           # DATA the executor needs — never method
  claim:      "..."
  evidence:   ["...", "..."]
deliverable:                      # the exact shape to return, so grading is mechanical
  verdict:    OVERTURNED | SURVIVES | INCONCLUSIVE
  argument:   string
  citations:  [url]
acceptance:                       # how the orchestrator grades it, stated up front
  - verdict is one of the three permitted values
  - at least one citation resolves to a reachable URL
constraints:
  max_turns:  6                   # a hard cap the executor cannot raise
  tools:      [web_search, read]
forbidden:
  - asking what step this is, or what comes next
  - requesting other tasks, files, or the surrounding process
```

**What is deliberately absent:** no stage number, no law identifier, no mention of what ran before or what runs after, no convergence criteria, no gate logic. The executor sees a job. **Your sequencing — the order of the twelve stages, where the gates sit, how coverage is judged, when a run is allowed to stop — never leaves your side. That ordering is the intellectual property. The individual task almost never is.**

**The litmus test, and it is checkable:** hand one contract to a stranger's agent. If they can do the job, it is self-contained. If they can reconstruct your pipeline from it, it leaks. Both halves must pass.

## 3. Make the seam a lint, not a promise

Your own record is unambiguous: rules written as prose decayed every time; rules that ran as code held every time. So the seam gets a mechanical check — a script, not a review habit. A lint is just a program that scans files and fails the build when it finds a violation.

```bash
# Fails if any emitted contract leaks pipeline structure.
grep -rnE '\b(E1[01]|E[0-9])\b|\bL-[A-E]\b|stage|convergence|aspect map|kill.?loop' contracts/ \
  && { echo "LEAK: contract references pipeline internals"; exit 1; }
exit 0
```

Wire it into CI — the automated checks that run on every commit — so a leaking contract cannot merge. **This is a fail-closed check**, meaning it blocks by default when it finds a problem, as opposed to fail-open, which would let work continue and merely warn. Your prior report's X-004 is the cautionary case: a gate wired to an event that could only display a message, not block, was a fail-open gate wearing a fail-closed label.

One warning drawn from that same report's §10, where a naive `grep -c '^L-0'` counted a wrapped line of prose as a ledger entry and raised a false alarm. **A check that cries wolf gets switched off around the third false alarm, and a switched-off check is a fail-open check.** So tune the pattern above against real contracts before you trust it, and prefer matching structure over matching bare words.

## 4. Notifications on all operating systems

You asked for every OS. The obvious package is `node-notifier`: MIT, **5,538,879 downloads last week**, 5,845 stars. But it was **last pushed 2024-06-24 — over two years ago — with 128 open issues.** Heavily used and effectively unmaintained.

**Recommendation: write it yourself, about 30 lines, no dependency.** Two reasons. First, your engine's README advertises *"No dependencies to install — the CLI is pure Node (≥18)"*, and adding a package to the core loop breaks a property you currently sell. Second, for a venture shipping to paying users, a two-year-stale dependency in a core feature is a supply-chain risk you would inherit for free.

Each platform ships a notifier already:

| OS | Mechanism | Present by default |
|---|---|---|
| macOS | `osascript -e 'display notification "…" with title "…"'` | Yes |
| Linux | `notify-send "title" "body"` | Usually (`libnotify`) |
| Windows | PowerShell toast via `Windows.UI.Notifications` | Yes, Win10+ |

Detect with Node's built-in `process.platform`, shell out, and **fail silently** — a notification that throws must never kill a run. Fall back to a terminal bell (`\x07`) when the platform command is missing, which covers headless Linux and SSH sessions.

**Fire on exactly four events**, because the research on agent monitoring is explicit that *monitors must stay selective, since every output line interrupts*:

1. A gate opens and needs your decision
2. An agent dies or goes stale past its deadline
3. The run reaches a terminal — scaffold, decision, or refusal
4. Spend crosses a threshold you set

Not on stage transitions. Not on findings. Four events, or it becomes noise you learn to ignore, and an ignored notification is the same as no notification — which is F3 again.

**This is the cheapest real win in the whole project.** It fixes F3 — you sitting there waiting on a dead subagent — it costs hours not days, it needs no UI, and it does not depend on the shell decision, the buyer question, or the orchestration boundary. **Build this first.**

## 5. What this changes about the shell

The seam decision partly *unblocks* the shell. Because orchestration stays local for now, the local web app you chose is viable today, and the seam is what keeps the door open to moving it later. So the shell is no longer blocked on S12 being fully answered — it is blocked on the buyer question in §0, which determines whether team features are needed at all.

Still true and still unaddressed: **nobody has seriously argued for any option other than the one you preferred.** Under law L-A — which says a claim's author can never be its only grader — a conclusion that agrees with the person who proposed it earns more scrutiny, not less. That row stays open.

## 6. Honest ceiling

- The contract shape in §2 is a design sketch. **No stage has been rewritten as a contract, and none has been executed.** Whether contracts preserve the engine's output quality is completely untested and is the assumption the entire architecture now rests on.
- The lint in §3 is illustrative and has never been run against a real contract. Expect false positives.
- `node-notifier`'s figures were read from the npm and GitHub APIs on 2026-08-28. The three platform commands are documented behaviour; **I did not execute them on Windows or Linux from this machine.**
- §0's buyer risk is not reduced by anything in this document.
