# Does anyone need this? — first pass at E2/E3

**You were right about the sequence, and the reason is that we skipped two stages of your own engine.**
Run `20260828-123823-depth-engine-product-ui`.
**⚠ Law L-A UNSATISFIED on this pass.** Codex hit a usage limit mid-check and died terminally. Everything below is **single-family** — a Claude model reasoning about a market — and has had no adversarial pass. Per your prior report's X-003, rate-limit errors never trigger fallback and nothing resumes by itself. Retry the check before acting on §4.

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
