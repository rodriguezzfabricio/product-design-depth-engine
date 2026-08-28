# Does anyone need this? — first pass at E2/E3

**You were right about the sequence, and the reason is that we skipped two stages of your own engine.**
Run `20260828-123823-depth-engine-product-ui`.
**✅ Law L-A SATISFIED — check re-run 2026-08-28 after credits were restored. All three claims OVERTURNED. See §7, which is the most important section in this repository.**

---

> ## ⛔ READ §7 FIRST
>
> **"No one has had a solution for it before" is false.** Six existing products were named and I verified every one. GitHub itself ships spec-driven development at **132,004 stars**. A product describing itself as *"Governance substrate for your AI coding agents — adversarial review, drift-detected rules, immutable audit"* was pushed to **today**. Sections 2 through 5 below were written before this was known, and §3's claim that formal verification failed commercially is **also wrong**. §7 has the corrections.

---

## 1. The argument you asked for

**You are right, and here is the sharper version of why.** Your engine's own order is: intake → interview → **E2 become the domain expert** → **E3 mine the world's scar tissue** → decompose → question battery. We went E0 → E1 → straight into design decisions. **E2 and E3 were skipped.** Every conclusion in files 02 through 07 was reached without domain expertise or failure research underneath it. Your instinct to go back is not a change of plan; it is the protocol asserting itself against a run that cut corners.

**Where I'd push back — one place only.** You wrote: *"There is [a need], no one has had a solution for it before."* That sentence is the riskiest thing in the project, not because it is wrong but because it is **flattering, load-bearing, and stated in advance of the research meant to test it.** Handing a researcher a question with the answer attached is how you get a confirmatory report. Your own law L-A exists precisely for claims like this.

And "no one has solved it" has **two explanations that look identical from outside**: a genuinely new category, or a graveyard where many tried and failed. You cannot tell them apart without going to look for the bodies. That is what E3 is for, and it is the half of your sequence I want to make explicit — not just *is there a need*, but **what has already died trying to serve it.**

**One structural correction to the sequence.** Desk research can establish prior art and failure modes. It **cannot** establish willingness to pay for a category that does not exist yet — there is no data about a product nobody has bought. So the order is: graveyard sweep (I can do) → customer interviews (only you can do) → product design. If we ran only the desk half and concluded "there is a need," we would have committed the exact error this engine was built to prevent.

## 2. The graveyard — what it says about rigor products

Two findings from academic sources, not vendor blogs:

- **"Significantly less than 1% of developers use formal verification."** Formal verification means mathematically proving code correct rather than testing it. It is the most rigorous thing our field has ever built, it works, and almost nobody uses it. The stated reason: *the additional effort needs an obvious, short-term benefit that justifies it, and over each week of use the cost must pay for itself.* **The Depth Engine is slow by design. That is the same tax, and this is the corpse most similar to it.**
- **Developers use free static-analysis tools even when their executives would fund paid ones** — because the expectations attached to a costly tool land on the developer who asked for it.

And the mechanism that kills these tools once adopted: *false positives, and the way warnings are presented, are barriers to use… many tools generate thousands of warnings, making it difficult to extract meaningful insights.*

**Read that against your own failure log.** F8 is "raw output is unreadable AI language." F1 is "no stopping point." **Those are not annoyances — they are the exact two symptoms that killed the previous generation of rigor tools.** A tool that produces more findings than a human will read gets ignored, and an ignored check is the same as no check. E3's job is to make you build against that, and it has now named the specific way this category dies.

## 3. The evidence that destroys my own argument

I was going to argue that rigor products have a poor commercial record while speed products win. **That is false, and the numbers are not close:**

| Company | What it sells | Scale |
|---|---|---|
| **Snyk** | Security scanning — correctness, not speed | **$325.0M revenue**, $1.247B raised over 16 rounds |
| **SonarSource** (SonarQube) | Code quality — **~85% of its rules are quality, only ~15% security** | Real company since 2007, self-hosted and cloud |
| **Datadog** | Observability | Broadest commercial platform in the category |
| **Sentry** | "What broke in my code, why, and how do I fix it" | Developer-first, strong in small and mid-size teams |

So "developers won't pay for correctness" is simply wrong. Formal verification failed; Snyk built a $325M business three feet away from it. **The interesting question is what separates them.**

## 4. The pattern that explains both — and it points straight at your buyer

**Rigor sells to whoever eats the cost of failure. It does not sell to whoever pays the cost of the rigor.**

Formal verification asks the individual developer to absorb a large, immediate effort for a benefit that is diffuse and lands elsewhere. Snyk sells to an organization that eats a breach. Sonar sells to an org that eats years of technical debt. Datadog sells to a team that eats a 3am outage. **The payer and the sufferer are the same entity in the winners, and different entities in the corpse.**

The purchasing research says the same thing from the other side: *individual developers discover tools, team leads evaluate them, platform engineering or procurement makes the final decision* — adoption is bottom-up, budget is top-down. And critically: **only 5% of individual developers treat cost-cutting as a priority when choosing a tool, while productivity ranks highly as a motivator to buy.**

**This is the most useful thing in this document.** The Depth Engine is explicitly *not* a productivity tool — you built it to be slow and careful. So the motivation that makes individual developers buy is the one you do not have. But the thing you *do* have — an append-only ledger showing what was challenged and what survived, plus a documented refusal — is a **risk artifact**, and risk is bought by whoever the risk lands on.

**Working hypothesis, to be tested with humans and not with more reading:** the individual developer is your **adopter**, not your **payer**. The money is with whoever absorbs the cost of an AI agent confidently shipping something wrong — a tech lead, a platform team, or anyone who must answer for a decision after the fact. That reframes the interviews in §5: do not ask developers whether they would pay. Ask who gets blamed when an AI-assisted decision turns out wrong, and then go talk to that person.

## 5. What is still missing, stated plainly

This pass established the **category base rate**. It did **not** establish who else is building what you are building. That gap is real and it is the rest of E2/E3:

- **No direct competitor sweep has been run.** Named candidates to check at source: LangSmith and Braintrust evaluation platforms, promptfoo, DeepEval, Guardrails, AI code-review tools, and any agent-verification or "AI decision audit" product. Until that is done, *"no one has had a solution"* remains **your assertion, not a finding.**
- Your PDF's target **T10** already ordered this sweep — *"many tools solve pieces of what the engine wants to solve, including problems the operators haven't identified yet"* — and named a starting index, `ai-boost/awesome-harness-engineering`. **It was never run.** Gate G4 asked you to rule on its scale and you never answered.
- The built-in web search keeps returning SEO listicles, which is your standing rule **R3** earning itself for the third time this run. **Scrapling `StealthyFetcher` (v0.4.15, already in the run venv) has still not been used.** A real prior-art sweep needs it.
- **Zero customer interviews.** Unchanged.

## 6. Honest ceiling

- **No cross-family check ran.** Codex died on quota mid-verdict. Everything here is one model family reasoning about a market, which is the condition your L-A exists to forbid. Re-run before acting.
- Snyk's $325.0M and the funding total come from an aggregator, not from company filings. The formal-verification and static-analysis findings come from peer-reviewed and arXiv sources and are the strongest evidence in this document.
- §4 is my synthesis. It is clean, which under L-A means it deserves more scrutiny, not less — and it has had none.
- No claim here establishes that anyone will pay for the Depth Engine. **The base rate for the category is encouraging; that is not the same as demand for your product,** and no amount of further desk research closes that gap.

---

# 7. The cross-family verdict — all three claims overturned

Codex ran with restored credits. **Nothing survived.** Every competitor below was independently verified by me against GitHub's API or by HTTP request on 2026-08-28, because accepting citations unopened is a defect this run has already committed three times.

## 7.1 Your premise is falsified. There are competitors, and one of them is GitHub.

> "The founder's 'no solution before' premise is already falsified, so it is not the deepest remaining uncertainty. The harder risks are differentiation, measurable quality improvement, workflow tolerance, and payment."

| Product | What it does | Verified |
|---|---|---|
| **[GitHub Spec Kit](https://github.github.com/spec-kit/)** | intent → spec → plan → tasks → implementation; agent-independent workflows, checklists, cross-artifact analysis | **`github/spec-kit`, 132,004 stars**, pushed 2026-08-28 |
| **[Nexus Agents](https://github.com/nexus-substrate/nexus-agents)** | *"Governance substrate for your AI coding agents — adversarial review, drift-detected rules, immutable audit, closed-loop telemetry"* | **18 stars**, pushed 2026-08-28 |
| **[Sigil](https://runsigil.com/)** | markdown spec → hidden verification scenarios → allow/review/block verdict, **signed append-only ledger** | HTTP 200 |
| **[Findry](https://findry.ai/platform)** | requirement-to-production governance, policy gates, **hash-chained evidence ledger** | HTTP 200 |
| **[Kiro](https://kiro.dev/)** | prompts → executable specifications, documented decisions, correctness validation, parallel agents | HTTP 200 |
| **[Augment Intent](https://www.augmentcode.com/guides/intent-walkthrough-prompt-to-merge)** | coordinator → implementer → verifier, living spec, decomposition, adversarial roles, human gates | HTTP 200 |

**Two of these hurt specifically.** GitHub Spec Kit is *GitHub*, with 132k stars and a commit today — spec-driven development is not an unserved idea, it is a first-party feature of the platform your customers already use. And **Nexus Agents' one-line description is nearly your pitch verbatim** — adversarial review, immutable audit, telemetry — at 18 stars, pushed today. Someone is building this right now, independently, and they are early enough that you cannot dismiss them and cannot yet out-run them either.

**What survives, and it is real but much narrower than you believed:**

> "I found no verified product matching every Depth Engine stage — especially **failure-history mining plus mandatory cross-family attack** — but that makes its differentiation **a particular workflow bundle, not a new category.**"

So you are not one-of-one. You are a **distinct bundle in a category that already has GitHub in it.** That is a survivable position — Linear entered issue-tracking against Jira and won on craft — but it is a completely different strategic posture from "nobody has seen this before," and it changes what you must prove. E3 (failure-history mining) and mandatory cross-family attack are your two genuinely uncommon stages. **Those are the product. Lead with them.**

## 7.2 My rigor-doesn't-sell argument was wrong — and so was my correction to it

I already retracted "rigor products don't sell" in §3. Codex went further: **formal verification supports real businesses too**, so §2's framing of it as the nearest corpse is also wrong.

| Evidence | Figure |
|---|---|
| **Sonar** (static analysis / code quality) | raised **$412M at a $4.7B valuation** |
| **Tricentis** (continuous testing, quality engineering) | **$1.33B investment at a $4.5B valuation** |
| **Synopsys** application-security / static-analysis division | sold for **up to $2.1B** |
| **Runtime Verification** (formal methods) | 100+ clients, **$30K–$50K monthly engagements** |
| **Certora** (formal verification) | seven years operating, **$100B+ of protected assets** |
| **AdaCore / SPARK** | ongoing formal-methods business |

Formal verification is not a graveyard. It is **high-value, low-volume** — five-figure monthly engagements rather than seat licences. That is a different business shape, not a failed one.

> "The sharper threat is not 'rigor never sells.' It is that **individual developers may not personally bear enough failure cost; enterprises, security teams, and regulated sectors usually do.**"

**This confirms §4 rather than overturning it.** The payer-is-not-the-adopter hypothesis survived a genuine attack — the only conclusion in this run that has. Treat it as the most load-bearing finding you own.

## 7.3 My advice to go do interviews was too weak

> "Interviews are neither necessary nor sufficient to establish willingness to pay: **they measure statements, not purchases.** Paid pilots, preorders, retention, workflow telemetry, and abandonment under real latency provide stronger evidence."

I told you to talk to 5–10 developers. That is diagnosis, not validation — people will tell you a rigor tool sounds great and then never pay for it, and *abandonment under real latency* is exactly your risk, because your engine is slow on purpose and nobody discovers whether they will tolerate that by being asked.

**Corrected sequence:**

1. **Competitor / graveyard research** — partly done here, §7.1. Still needs the T10 sweep at source.
2. **A minimal testable workflow** — the smallest thing that runs end to end and produces one real ledger on someone else's real problem.
3. **A paid behavioural test** — a paid pilot or preorder. Money changing hands is the only evidence that settles this.

Interviews run alongside all three as diagnosis. What survives of my original claim is only the narrow part: **desk research alone cannot validate demand for the Depth Engine specifically.**

## 7.4 What this changes

- **Stop saying "no one has solved this."** It is checkably false and it will cost you credibility with the first informed person who hears it. Say instead: *spec-driven development is a real and crowded category; almost nobody does failure-history mining or mandatory cross-family adversarial attack, and here is a ledger proving mine ran.*
- **Go read Nexus Agents' repository.** It is 18 stars and public. It is the closest thing to you that exists, and it is free intelligence.
- **The buyer hypothesis is now your most-tested asset.** Enterprises, security teams, and regulated sectors bear failure cost. Individual developers do not.
- **The next milestone is not a UI.** It is one real ledger from one real external problem, in front of one person willing to pay.

## 7.5 Ceiling on §7

Codex's figures for Sonar, Tricentis, Synopsys, Runtime Verification and Certora come with primary-source URLs (press releases and company pages) that **I did not open** — I verified the six competitor products, not the six financial figures. The competitor verification is solid: star counts and push dates came from GitHub's API, and the four sites returned HTTP 200. I did **not** read Kiro's, Sigil's, Findry's or Augment's actual capabilities beyond Codex's descriptions, so the feature claims in §7.1's middle column are Codex's characterisation, not mine.
