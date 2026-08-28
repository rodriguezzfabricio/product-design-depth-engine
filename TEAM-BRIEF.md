# Depth Engine: where we actually are

Written 2026-08-28 for the team, so we can discuss this with the same facts in front of us. Everything here is backed by a file in this repo. Where a number is unverified, it says so.

This document was written by an AI coding agent (Claude Code) during depth-engine run `20260828-123823-depth-engine-product-ui`. Per our repo rule, AI-written docs say they are AI-written.

## What the Depth Engine is, in plain terms

It is not a program. It is 22 Markdown files, which are plain text files with light formatting, that an AI coding agent reads and follows. Twelve of them are steps we call E0 through E11: take in the goal, interview the operator, research the subject, find how similar projects already failed, break the goal into pieces, generate questions, answer and attack them, check whether we are done, build a small test slice, then emit a result. Five more are always-on rules we call laws, the important one being L-A, which says the model that made a claim can never be the only one grading it.

A run ends one of three ways. It hands back a scaffold, meaning a starting skeleton of files and structure you build from. Or it hands back a decision. Or it refuses, saying the evidence does not support doing this at all.

Nothing in it executes. When a stage file says "this gate cannot be bypassed," the only thing enforcing that sentence is a model choosing to obey a sentence. That single fact explains most of what follows.

Every run writes four files. `LEDGER.md` is append-only, meaning you add to the bottom and never edit what is above, so it becomes a record you can audit later. `STATE.md` is a small snapshot of where the run is, so if the agent's memory gets wiped it can read one file and continue. `INDEX.md` is a table of contents. `REGISTER.md` is a list where each row is one thing that must be answered, with a status.

## Why we started this

Fabricio logged eight failures from real use, F1 through F8.

The engine never decides it has done enough and stops. Its thoroughness does not adapt to how big the job is. Sub-agents, meaning the helper AI agents the main one spawns to do parts of the job, die quietly and nobody notices until a human checks by hand. Model routing, which is the logic that picks a cheaper or more expensive model for each piece of work, silently fails to apply, and there is no way to see what actually ran on what. You cannot see what changed when it writes code. Documentation for a pull request, which is the request to merge your changes into the main codebase where teammates review them, has to be asked for every single time. Token spend is enormous with no tracking, where tokens are the chunks of text a model reads and writes and are the thing you get billed on. And the raw output is hard to read, which forces a manual habit of pasting everything into a fresh chat to ask what it means.

The original request was a user interface. The reasoning was that the command line feels incomplete and we want to sell this to developers, something like Cursor.

## What we did

We started a depth-engine run on the engine itself and walked it. Along the way we used the engine's own law L-A, which requires that every load-bearing claim gets attacked by a model from a different company. We used Codex for that, because two copies of Claude share the same training and the same blind spots, so they agree with each other confidently and prove nothing.

We ran nine of those adversarial checks. Seven came back overturned. Two came back inconclusive. **Not one of our conclusions survived clean.** Every single correction moved toward Fabricio's instinct and away from the AI's, which is worth saying plainly because it is the opposite of what people expect from this kind of exercise.

## The finding that changes our positioning

We believed nobody had built this before. That is false, and it took under a minute to check.

`github/spec-kit` has 132,004 stars on GitHub, where a star is roughly a bookmark and a rough popularity signal, and it has a commit from today. It does spec-driven development, which means you write a precise specification first and the agent builds from that instead of from a loose prompt. It goes intent, then spec, then plan, then tasks, then implementation, and works with any agent. So this is a first-party GitHub feature, not an unserved idea.

Then there is `nexus-substrate/nexus-agents`. It is MIT licensed, meaning anyone can take it, change it, and sell it. It is published on npm, the package registry Node.js developers install from, so getting it is one command. It has 18 stars and was also pushed today. We read its source. It already ships six of our seven v2 mechanisms:

| Our v2 mechanism | What Nexus already has |
|---|---|
| M2 staleness watchdog | A circuit breaker, a term borrowed from electrical wiring: when an agent keeps failing, it trips and stops sending work there, routing around it automatically |
| M3 routing plus a visible model panel | Routing that watches what actually shipped and feeds those results back in, so it gets better at choosing over time. Ahead of our spec, not level with it |
| M7 thoroughness dial | A seven-role review panel, with a `--quick` flag that drops it to three |
| M6 repo-aware auto documentation | Automated checks that run on every commit and fail the build when the written rules stop matching what the code actually does |
| M1 project manager with isolated judgment | They have project-manager and scope-guard reviewer roles. They do not have our two-way bias isolation |
| Mandatory cross-family attack | Their agents are Claude Code, Codex, Gemini and OpenCode, with five adversarial reviewer roles, one named "catfish" |
| Our append-only ledger | A hash-chained audit trail, meaning each entry carries a fingerprint of the entry before it, so if anyone edits old history the chain breaks and you can prove it. That is stronger than Markdown files we simply promise not to edit |

Two more things they do that should bother us. They publish "100% bug-catch on a focused synthetic dataset (n=10) and a 50% raw false-positive rate." A false positive is when the tool flags something as a problem and it turns out to be fine, and n=10 means they only tested ten cases, which they say themselves is too few to draw firm conclusions from. So they are publishing the unflattering number and the small sample size on purpose. That is our own law L-E, evidence over assertion, already shipped by someone else.

They also run an authority ladder. Every automated check starts out only allowed to observe, then can be promoted to suggest, then to advise, then finally to actually block work, and each promotion has to be earned against evidence plus a human signing off. Compare that to our thinking about fail-open and fail-closed, where a fail-open check lets work continue when it breaks, like a smoke alarm that goes silent on a dead battery, and a fail-closed one stops everything. Their version is more mature than ours.

Four more products exist and their sites load: Sigil, Findry, Kiro, and Augment Intent. We have not read those at source yet.

## What survives, and it is real

No competitor matches every stage. The two nobody else has are mining failure history and the refusal, meaning the ability to say the evidence does not support building this.

There is also a difference in what the tools are for, and it holds up. Nexus and Spec Kit govern work that is already being done: they let it in, review it, record it, route it. Our engine decides whether the work should happen at all. That is a genuine difference and it is our opening. It is not the difference we were claiming.

## The one thing worth building a company around

The adversarial check was asked directly which single item could carry a business. The answer was mining failure history, reframed narrowly as **repo-specific recurrence prevention**, because it "can accumulate proprietary incident-to-change outcome data and prove value through reduced repeat regressions."

In plain terms: a regression is when something that used to work stops working after a change, or when a bug you already fixed comes back. The pitch is that the tool remembers what has already broken in your codebase and stops it happening a second time.

Every other mechanism on our list is orchestration, meaning the logic that decides which step runs next and judges the result. That is code somebody else can write. This one accumulates data that builds up per customer. Each run on a customer's codebase learns what has broken there before, what the fix was, and whether it came back. That record is their own history. A competitor cannot copy it and the customer cannot take it elsewhere, which means leaving us gets more painful the longer they stay. That is switching cost, and it is the thing we currently do not have. It also carries a number we can count, fewer repeat breakages, where "lossless humanization" carries no number at all.

The reframe matters more than it looks. Our E3 as written mines the world's failures, meaning write-ups that other teams publish after something went badly wrong, explaining what broke and why. Those are public, so that research is copyable. Repo-specific recurrence prevention mines this one customer's failures instead. Same step, different subject, completely different economics.

## Where we were wrong about the market

We assumed rigor products do not sell and speed products do. Wrong, and not close. Sonar raised $412M selling code quality, at a $4.7B valuation, meaning that is the price investors put on the whole company. Tricentis took $1.33B at $4.5B selling testing tools. Synopsys sold its security-scanning division for up to $2.1B. Snyk does $325M a year in revenue. Even formal verification, which means mathematically proving code correct instead of just testing it, and which well under 1% of developers use, supports real businesses. Runtime Verification runs over 100 clients at $30,000 to $50,000 a month, and Certora has been going seven years.

The pattern separating the winners from the failures is the useful part. **Rigor sells to whoever eats the cost of failure. It does not sell to whoever pays the cost of the rigor.** Formal verification asks one developer to absorb a large amount of extra work now, for a benefit that lands on somebody else later. Snyk sells to a company that eats a security breach. Datadog sells to a team that eats a 3am outage, and booked $3.43B in 2025.

Applied to us: only 5% of individual developers rank saving money as a priority when picking a tool, while getting more done ranks high. Our engine is deliberately slow, so the one motive that makes an individual developer buy is the motive we do not have. What we produce instead is a record that protects somebody from being blamed later, and that kind of thing gets bought by whoever carries the blame. **Working hypothesis: the developer adopts, the organisation pays.** This is the only conclusion in the entire run that survived an adversarial attack instead of being overturned by one.

## The problem with hiding how it works

We said we wanted to hide our method, the way Cursor and Claude Code hide the instructions they send to their models. Those instructions are public. A GitHub repo with 143,196 stars publishes them, with folders literally named `Cursor Prompts` and `Anthropic`, including the machine-readable lists of what each tool is allowed to do. What those companies achieve is not showing you, which is a choice about presentation.

More to the point, our own installer copies every stage and law file onto the customer's hard drive. They type `cat`, a one-word command that prints a file to the screen, and they have read our whole method. Hiding it is impossible with the way we ship today. That is not a design problem for the interface. It sits above every interface decision.

There is a fix, and it came from the adversarial check rather than from us. The line to draw is not hosted versus local. It is between deciding and doing. The deciding part, which picks the next step and judges what comes back, stays on our side and never ships. The customer's agent gets one narrow job at a time, something like "research these five failure modes and return findings with sources," and learns nothing about the shape of the pipeline. GitLab already ships this exact arrangement: the customer's code and model traffic never leave the customer's own cloud account, while GitLab supplies the deciding layer.

Fabricio's decision was to design for that split now and build it later, which keeps the option open without forcing a rewrite before a paying customer asks for one.

## Two smaller things worth knowing

The command we were going to use to install a design tool, `npx skills add https://uizze.com/`, does not work. That command copies down a git repository, meaning a versioned folder of code, and uizze.com is a marketing website with no repository behind it. The working command is `npx skills add uizze/uizze`. Related: that same registry claims 532,461 installs for a repository with 12 stars, so we stopped ranking tools by public numbers and started reading them instead. This is the third time on this project a public number has failed to check out.

Also, eight design tools were already installed on Fabricio's machine and unused, including one that strips AI writing tells from text, which is our M4 sitting on disk already. The earlier report logged this same "we were about to build something that already exists" correction three separate times before this one.

## Where the run stands

The coverage register has 46 rows, of which 19 are covered, 10 in progress, and 17 open. The run has been sent back to stages E2 and E3, becoming the expert and mining failure history, because we skipped both and every design conclusion was built without them underneath.

Interface work is on hold. The next milestone is not a screen. It is one real record, on one real outside codebase, showing one breakage that got caught before it happened again. That is both the demo and the test, because interviews measure what people say and not what they buy. The specific risk nobody can answer in a meeting is whether anyone tolerates how slow the engine is once they are actually sitting there waiting on it.

## What we should decide together

Who our buyer is, since we are treating this as a venture and nobody outside this team has been asked a single question about it. Whether we accept that we are one option in a category that already contains GitHub, rather than the only people who have seen the problem. Whether repo-specific recurrence prevention is the wedge we commit to, and what we drop to focus on it. How the refusal gets designed so it reads like a bank blocking a fraudulent charge rather than a tool telling a paying customer they wasted their money, which means every refusal points at the evidence behind it, stays narrow, and can be appealed. And whether M4 gets a real way to measure "lossless" or gets deleted from the list.

One practical thing before that conversation: somebody should read `nexus-substrate/nexus-agents` end to end. It is public, it is free to use, and it is ahead of us in several places. That is free intelligence about what a person who arrived at our idea independently thinks it should be.
