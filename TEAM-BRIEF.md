# Depth Engine: where we actually are

Written 2026-08-28 for the team, so we can discuss this with the same facts in front of us. Everything here is backed by a file in this repo. Where a number is unverified, it says so.

This document was written by an AI coding agent (Claude Code) during depth-engine run `20260828-123823-depth-engine-product-ui`. Per our repo rule, AI-written docs say they are AI-written.

## What the Depth Engine is, in plain terms

It is not a program. It is 22 Markdown files, which are plain text files with light formatting, that an AI coding agent reads and follows. Twelve of them are steps we call E0 through E11: take in the goal, interview the operator, research the domain, find how similar projects already failed, break the goal into pieces, generate questions, answer and attack them, check whether we are done, build a small test slice, then emit a result. Five more are always-on rules we call laws, the important one being L-A, which says the model that made a claim can never be the only one grading it. A run ends in one of three ways: a build-ready scaffold, a decision, or a documented refusal to proceed.

Nothing in it executes. When a stage file says "this gate cannot be bypassed," the only thing enforcing that sentence is a model choosing to obey a sentence. That single fact explains most of what follows.

Every run writes four files. `LEDGER.md` is append-only, meaning you add to the bottom and never edit what is above, so it becomes a record you can audit. `STATE.md` is a small snapshot of where the run is, so if the agent's memory gets wiped it can read one file and continue. `INDEX.md` is a table of contents. `REGISTER.md` is a list where each row is one thing that must be answered, with a status.

## Why we started this

Fabricio logged eight failures from real use, F1 through F8. The engine never decides it has done enough and stops. Its thoroughness does not adapt to how big the job is. Sub-agents die quietly and nobody notices until a human checks by hand. Model routing silently fails to apply and there is no way to see what ran on what. You cannot see what changed when it writes code. Pull request documentation has to be requested every time. Token spend is enormous with no tracking. And the raw output is hard to read, which forces a manual habit of pasting everything into a fresh chat to ask what it means.

The original request was a user interface. The reasoning was that the command line feels incomplete and we want to sell this to developers, something like Cursor.

## What we did

We started a depth-engine run on the engine itself and walked it. Along the way we used the engine's own law L-A, which requires that every load-bearing claim gets attacked by a model from a different company. We used Codex for that, because two instances of Claude share training and biases, so they agree with each other confidently and prove nothing.

We ran nine of those adversarial checks. Seven came back overturned. Two came back inconclusive. **Not one of our conclusions survived clean.** Every single correction moved toward Fabricio's instinct and away from the AI's, which is worth saying plainly because it is the opposite of what people expect from this kind of exercise.

## The finding that changes our positioning

We believed nobody had built this before. That is false, and it took under a minute to check.

`github/spec-kit` has 132,004 stars on GitHub and a commit from today. It does intent to spec to plan to tasks to implementation, works with any agent, and ships checklists. Spec-driven development is a first-party GitHub feature, not an unserved idea.

Then there is `nexus-substrate/nexus-agents`. MIT licensed, published on npm, 18 stars, also pushed today. We read its source. It already ships six of our seven v2 mechanisms:

| Our v2 mechanism | What Nexus already has |
|---|---|
| M2 staleness watchdog | A circuit breaker that detects a failing agent and routes work around it automatically |
| M3 routing plus a visible model panel | Closed-loop routing that feeds real outcomes back into a scoring algorithm, so routing learns from what shipped. Ahead of our spec, not level with it |
| M7 thoroughness dial | A seven-role review panel with a `--quick` flag that drops it to three |
| M6 repo-aware auto documentation | A drift-detected charter: automated checks on every commit that fail the build when documented rules stop matching real behavior |
| M1 project manager with isolated judgment | They have `pm` and `scope_steward` voter roles. They do not have our two-way bias isolation |
| Mandatory cross-family attack | Their agents are Claude Code, Codex, Gemini and OpenCode, with five adversarial review roles, one named "catfish" |
| Our append-only ledger | A hash-chained tamper-evident audit trail, where each entry is cryptographically linked to the one before it so any edit to history is detectable. This is strictly stronger than Markdown files we promise not to edit |

Two more things they do that should bother us. They publish "100% bug-catch on a focused synthetic dataset (n=10) and a 50% raw false-positive rate, directional small-n figures, not measured rates." That is our own law L-E, evidence over assertion, already shipped by someone else with the embarrassing number attached. And they run an authority ladder where every automated loop sits at observe, then suggest, then advisory, then enforce, and has to earn promotion against evidence plus human sign-off. More mature than our fail-open and fail-closed thinking.

Four more products exist and resolve live: Sigil, Findry, Kiro, and Augment Intent. We have not read those at source yet.

## What survives, and it is real

No competitor matches every stage. The two nobody else has are mining failure history and the refusal terminal, the ability to say the evidence does not support building this.

There is also a category distinction that holds. Nexus and Spec Kit govern work that is being done: they admit it, review it, audit it, route it. Our engine decides whether the work should happen at all. That is a genuine difference and it is our opening. It is not the difference we were claiming.

## The one thing worth building a company around

The adversarial check was asked directly which single item could carry a business. The answer was mining failure history, reframed narrowly as **repo-specific recurrence prevention**, because it "can accumulate proprietary incident-to-change outcome data and prove value through reduced repeat regressions."

Every other mechanism on our list is orchestration, which is code somebody else can write. This one accumulates data that compounds per customer. Each run on a customer's repository learns what has broken there before, what the fix was, and whether it came back. That dataset is their own history. A competitor cannot copy it and the customer cannot take it elsewhere. That is switching cost, which is the thing we currently do not have. It also carries a number we can count, fewer repeat regressions, where "lossless humanization" carries no number at all.

The reframe matters more than it looks. Our E3 as written mines the world's failures, meaning external post-mortems of similar projects. That is research and it is copyable. Repo-specific recurrence prevention mines this customer's failures. Same stage, different subject, completely different economics.

## Where we were wrong about the market

We assumed rigor products do not sell and speed products do. Wrong, and not close. Sonar raised $412M at a $4.7B valuation selling code quality. Tricentis took $1.33B at $4.5B selling continuous testing. Synopsys sold its application security division for up to $2.1B. Snyk does $325M in revenue. Even formal verification, which means mathematically proving code correct instead of testing it and is used by well under 1% of developers, supports real businesses: Runtime Verification runs 100+ clients at $30,000 to $50,000 monthly engagements, and Certora has operated seven years.

The pattern that separates the winners from the failures is the useful part. **Rigor sells to whoever eats the cost of failure. It does not sell to whoever pays the cost of the rigor.** Formal verification asks one developer to absorb a large immediate effort for a benefit that lands somewhere else. Snyk sells to a company that eats a breach. Datadog sells to a team that eats a 3am outage, and booked $3.43B in 2025.

Applied to us: only 5% of individual developers rank cost-cutting when picking a tool, while productivity ranks high. Our engine is deliberately slow, so the one motive that makes an individual developer buy is the motive we do not have. What we produce instead is a risk artifact, and risk gets bought by whoever the risk lands on. **Working hypothesis: the developer adopts, the organisation pays.** This is the only conclusion in the entire run that survived an adversarial attack rather than being overturned by one.

## The intellectual property problem

We said we wanted to hide how the engine works, the way Cursor and Claude Code hide their prompts. Those prompts are public. A GitHub repo with 143,196 stars publishes them, including the machine-readable tool definitions, with folders literally named `Cursor Prompts` and `Anthropic`. What those companies achieve is not showing you, which is a presentation choice.

More to the point, `depth-engine init` copies every stage and law file onto the customer's hard drive. Someone types `cat` and reads the whole method. Secrecy is impossible under our current architecture. That is not a design problem for the interface, it sits upstream of every interface decision.

There is a fix, and it came from the adversarial check rather than from us. The boundary is not hosted versus local, it is orchestration versus execution. The orchestrator, meaning the part that decides which step runs next and how to judge the result, stays on our side. The customer's agent receives one narrow task at a time, something like "research these five failure modes and return findings with citations," and learns nothing about the pipeline. GitLab already ships this shape: customer code and model traffic stay inside the customer's own cloud account while GitLab supplies the orchestration.

Fabricio's decision was to design for that boundary now and build it later, which keeps the option open without a rewrite before a paying customer asks for one.

## Two smaller things worth knowing

The command we were going to use to install a design tool, `npx skills add https://uizze.com/`, does not work. That command clones a git repository and uizze.com is a marketing site. The working one is `npx skills add uizze/uizze`. Related: that registry claims 532,461 installs for a repository with 12 stars, so we stopped ranking tools by registry numbers and started reading them instead. This is the third time a public number has failed to check out on this project.

Also, eight design tools were already installed on Fabricio's machine and unused, including one that removes AI writing tells, which is our M4 sitting on disk. The prior report logged this same "we were about to build something that already exists" correction three separate times before this one.

## Where the run stands

The coverage register has 46 rows, of which 19 are covered, 10 in progress, and 17 open. The run has been sent back to stages E2 and E3, becoming the domain expert and mining failure history, because we skipped both and every design conclusion was built without them underneath.

Interface work is on hold. The next milestone is not a screen. It is one real ledger, on one real external repository, showing one prevented recurrence. That is both the demo and the test, because interviews measure what people say and not what they buy. The specific risk nobody can answer in a meeting is whether anyone tolerates how slow the engine is once they are actually waiting on it.

## What we should decide together

Who our buyer is, since we are treating this as a venture and nobody outside this team has been asked a single question about it. Whether we accept that we are a distinct bundle in a category that already contains GitHub, rather than the only ones who have seen the problem. Whether repo-specific recurrence prevention is the wedge we commit to, and what we drop to focus on it. How the refusal gets designed so it reads like Stripe Radar blocking a fraudulent charge rather than a tool telling a paying customer they wasted their money, which means evidence-linked, scoped, and appealable. And whether M4 gets an actual way to measure "lossless" or gets deleted from the list.

One practical thing before that conversation: somebody should read `nexus-substrate/nexus-agents` end to end. It is public, it is MIT, and it is ahead of us in several places. That is free intelligence about what a person who arrived at our idea independently thinks it should be.
