# The design canon — more resources of the kind your mentor gave you

**Answers seed ask A4.** Run `20260828-123823-depth-engine-product-ui`, stage E1 MOVE-2.
**Every URL below returned HTTP 200 on 2026-08-28.** Checked with `curl`, not assumed.

Your mentor gave you one usability source and one marketing source. That pairing is deliberate and worth noticing: **how it works** and **how you say it**. This list extends both legs, ordered by how soon you will need each.

---

## Tier 1 — read this week

### [Nielsen's 10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) — *your mentor's link, verified*
Jakob Nielsen, last updated 30 January 2024. The ten, verbatim from the page:

1. Visibility of system status · 2. Match between system and real world · 3. User control and freedom · 4. Consistency and standards · 5. Error prevention · 6. Recognition rather than recall · 7. Flexibility and efficiency of use · 8. Aesthetic and minimalist design · 9. Help users recognize, diagnose, recover from errors · 10. Help and documentation

**Three of these are load-bearing for a long-running-run UI, and one is nearly the whole product:**

- **#1 Visibility of system status** — *"keep users informed about what is going on, through appropriate feedback within a reasonable amount of time."* Your **F3** (sitting there waiting on a dead subagent) is a textbook violation. Heuristic #1 is not a nice-to-have here; it is the product.
- **#6 Recognition rather than recall** — *"the user should not have to remember information from one part of the interface to another."* Your current workflow is: run finishes, paste output into a fresh chat, ask what it means. That is pure recall. M1's PM panel is heuristic #6.
- **#8 Aesthetic and minimalist design** — *"every extra unit of information competes with the relevant units."* This is the formal statement of your "no random buttons" instinct.

### [Linear's Method](https://linear.app/method)
Linear's own principles, published. The nearest thing to a spec for the product you are describing. Pair with the [Figma interview](https://www.figma.com/blog/the-linear-method-opinionated-software/) on opinionated software.

### [Refactoring UI](https://www.refactoringui.com/)
Steve Schoger and Adam Wathan. The most practical resource for a developer who cannot yet reliably tell good from bad — it teaches by before/after rather than by principle. Directly targets the gap you named ("I'm not a senior engineer yet" / non-slop). If you buy one thing on this list, this.

### [Laws of UX](https://lawsofux.com/)
Jon Yablonski. Named cognitive laws with citations. The four you will actually use:
- **Hick's Law** — decision time grows with the number of choices. The argument for one dial and one action.
- **Fitts's Law** — time to hit a target depends on distance and size. Why the primary action gets the biggest, closest hit area.
- **Jakob's Law** — users expect your site to work like every other site they know. **The direct rebuttal to "no one has ever seen this product"**: they have seen a CI run, an inbox, a trace viewer. Borrow those.
- **Aesthetic-Usability Effect** — users perceive attractive designs as more usable. Why polish is not vanity on a tool asking for trust.

## Tier 2 — read before you commit to a layout

### [Dieter Rams — Ten Principles for Good Design](https://www.vitsoe.com/us/about/good-design)
The source Nielsen's #8 descends from. "Good design is as little design as possible." Rams is where the minimalism instinct comes from; reading the original stops it from degrading into "beige and empty."

### [Tog's First Principles of Interaction Design](https://asktog.com/atc/principles-of-interaction-design/)
Bruce Tognazzini. Denser and more opinionated than Nielsen. Strongest on **latency**, **state visibility**, and **defaults** — precisely the three areas a long-running-run UI lives or dies on.

### [Shape Up](https://basecamp.com/shapeup) — free online
Ryan Singer, Basecamp. Not a UI book — a book about **scoping** design work so it finishes. Given your **F1** (no stopping point) and **L-D** (the freeze law), this is thematically the same problem you already have in the engine, solved for product teams. Its "appetite" concept is your thoroughness dial in another domain.

### [Anthropic — Claude Code best practices](https://www.anthropic.com/engineering/claude-code-best-practices)
Not design, but it belongs on this list for the reason your prior report gave three times: **read the harness documentation before designing a mechanism.** §8 of that report logged that correction being relearned once per batch.

## Tier 3 — the marketing leg

### [Marketing Examples](https://marketingexamples.com/) — *your mentor's link, verified*
Harry Dry. Short, concrete teardowns of copy and landing pages. Its central lesson — **be specific, show don't tell** — is the whole reason §5 of `03-market-and-business.md` argues your ledger *is* the sales asset. "Rigorous AI research" is a claim. "This run overturned two of its own conclusions, here they are" is a demonstration.

### The pairing, made explicit
Nielsen governs the product; Harry Dry governs the page. They meet at one question: **what is the single frame that proves the value?** For you that frame is the coverage bar with a closed denominator (`02-what-to-display.md` §4). Design it as a UI component *and* as the landing-page hero. Same asset.

---

## What to do with this list

Do not read all of it. In order:

1. **Refactoring UI** — buys the most taste per hour for where you are.
2. **Nielsen's ten**, re-read specifically against your F1–F8. You will find most of your failures are already named there.
3. **Linear's Method** — the closest thing to a spec for your product's posture.
4. **Laws of UX**, four laws only (Hick, Fitts, Jakob, Aesthetic-Usability).

Then run `design-consultation` (already installed — see `01-tooling-audit.md` §5). It does the landscape research and proposes an actual palette and type scale, so you are choosing between concrete options rather than reading theory indefinitely.

**A note on that, and it is the L-D freeze law applied to you:** this list could be twenty entries. It is nine because you have a product to design, and reading is the most comfortable way to avoid designing. Four items, then build something and run `design-review` against it.

## Honest ceiling

- Every URL returned 200 on 2026-08-28. **I verified reachability, not current content** — except the Nielsen page and the Figma and Sequoia articles, which I read.
- Tier assignments and the "read these four" ordering are my judgment for your specific situation. Not evidence-backed rankings; another designer would order them differently.
- Rams, Tognazzini, Shape Up, and Laws of UX are named from established reputation. I did not re-read them during this run.
- No resource here was evaluated *by using it on this project*. The claim "Refactoring UI buys the most taste per hour" is a recommendation, not a measurement.
