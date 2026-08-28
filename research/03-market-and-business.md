# How AI developer products actually grew — and what transfers

**Answers seed asks A2 (market research on successful developer apps, AI era) and A3 (how they blew up, how they look).**
Run `20260828-123823-depth-engine-product-ui`, stage E1 MOVE-2.

---

## 0. A warning about this document's own sources

Your rule **R3** says built-in web search bounces off Cloudflare and returns titles, so stealth scraping is mandatory on every research pass. That rule earned itself again here. My first search for AI-tool growth returned nine results, of which **seven were SEO listicles** — several published by the vendors being ranked (`lovable.dev/guides/best-ai-app-builders` ranking Lovable first).

So this document is split by evidence grade, and the weak tier is quarantined in §4 rather than mixed in. **Do not build a pitch deck on §4.**

---

## 1. The pattern that actually explains the AI era: bottom-up, design-led

The strongest-evidenced growth story I could retrieve at primary grade is Linear's, via [Sequoia](https://sequoiacap.com/article/linear-spotlight). It is not an AI product, which is exactly why it is useful — it isolates *design* as the growth variable.

**Facts:**
- Founded January 2019, **profitable by July 2021**.
- No waitlist, no launch campaign. The founders tweeted their work; that is how Sequoia found them.
- Growth came through **internal revolts** — teams refusing management's mandated tool. Sequoia's own teams sent "a full memo" refusing alternatives.

**The mechanism.** Design quality made individual contributors advocate *against their own management's* tooling choice. Nothing else in the developer-tools playbook produces that. Not features, not pricing, not sales.

**What Linear chose, concretely** ([Figma](https://www.figma.com/blog/the-linear-method-opinionated-software/), [linear.app/method](https://linear.app/method)):

> "There's one really good way of doing things." — and they design to force it.
> "Flexible software lets everyone invent their own workflows, which eventually creates chaos as teams scale." — Jori Lallo
> They take deliberate **product debt in settings** to ship a stronger core.
> Dark gray sans-serif on black, "inspired by coding environments engineers prefer" — professional, not playful.
> "How can we make it reduce the friction as much as possible." — Tuomas Artman

**Transfer to you.** Your A8 constraint — *no random buttons, no dropdown menus, little to no friction* — is not a preference. It is the documented growth mechanism of the most design-respected tool in your category. And Linear's willingness to take product debt in settings is permission you should use: **your settings screen is allowed to be ugly.** Your run view is not.

## 2. What the AI-era products did differently

Three structural moves, each verifiable from the products themselves:

**Zero migration cost.** Cursor forked VS Code. A developer's extensions, keybindings, and muscle memory survived the switch, so the adoption decision cost an afternoon instead of a quarter. *Transfer:* the Depth Engine already installs into an existing repo as a folder and is driven by an agent the developer already runs. Preserve that. A UI that demands a new workspace concept throws away your best structural advantage.

**Time-to-first-working-artifact as the headline metric.** Bolt, Lovable, and Replit Agent all compete on minutes-to-something-that-runs. *Transfer, and it cuts against you:* the Depth Engine is deliberately slow — 12 stages, adversarial checks, saturation. **You cannot win on speed and you should not try.** Your equivalent metric is *time-to-first-defensible-answer*, and your differentiator is that the answer survived an attack. Which means the UI must make the attack visible, or you are selling slowness with no visible compensation.

**The demo is the marketing.** These products grew on screenshots and 30-second clips, not on documentation. *Transfer:* §4 of `02-what-to-display.md` identifies your screenshot — the coverage bar with a closed denominator. A progress bar that actually reaches 100% on an agent task is a claim no competitor can screenshot, because none of them has solved the stopping problem. Design *that frame* first and let the rest of the UI follow it.

## 3. How they look — the shared visual grammar

Observed across Linear, Cursor, Vercel, Raycast, and the current generation of agent tools:

| Pattern | What it looks like | Why it works here |
|---|---|---|
| Dark-first, near-black | Not pure `#000`; a desaturated near-black with lifted surfaces | Matches the terminal/editor the user just came from. Linear chose this deliberately. |
| One accent, used sparingly | A single hue for the primary action and active state | Your **A8 "psychology behind the colors"** ask resolves to this: color carries *status*, not decoration. Reserve saturation for meaning — a red heartbeat, a green survived-verdict. |
| Dense, monospaced where it is data | Tabular numbers, monospace for IDs and paths | Ledger IDs, run IDs, token counts are all data. Do not set them in a display font. |
| Keyboard-first, command palette | `⌘K`, no chrome | Answers "no random buttons" literally: the buttons live in a palette, not on screen |
| Motion only to explain change | ~150ms, ease-out, no bounce | On a long-running run, motion means "something moved." Decorative motion destroys that signal. |

**The color psychology answer, stated properly.** There is no lookup table where blue means trust. What holds up is: (a) **semantic reservation** — a hue that means one thing means it everywhere; (b) **contrast as hierarchy** — the eye goes to the highest-contrast element, so the coverage bar must be the highest-contrast thing on screen; (c) **accessible defaults** — WCAG AA, 4.5:1 for text, which is a check, not a taste. Anything beyond that in "color psychology" is culturally contingent and mostly folklore. Run `design-consultation` (already installed) to derive the actual palette with stated rationale.

## 4. Quarantine: numbers I could not verify

These circulated in the listicle tier. **Every one is UNVERIFIED.** I am recording them so they are not silently reintroduced later as fact.

| Claim | Status |
|---|---|
| Lovable reached $100M ARR in 8 months | **UNVERIFIED** — vendor-adjacent blogs only |
| Lovable at $200M ARR, $6.6B valuation | **UNVERIFIED** — no primary source retrieved |
| Replit $10M → $100M ARR in 9 months post-Agent | **UNVERIFIED** — no primary source retrieved |
| Developers spend $15B/yr on AI coding tools | **UNVERIFIED** — no methodology found |
| 84% of developers use or plan to use AI coding tools | **UNVERIFIED** — no survey instrument found |
| Bolt 28 min / Lovable 35 min / Replit 45 min to prototype | **UNVERIFIED** — single blogger's test, n=1 |

Your prior report's C4 and C6 are the precedent: "74k stars" was ~33k, "16k stars" was 117k. Both directions. **Registry, vendor, and listicle numbers are decorative until a primary source is opened.**

To upgrade these properly: fetch each company's own announcements with Scrapling's `StealthyFetcher` (v0.4.15, already in your venv per R3), or pull filings/press releases directly. That is a scoped follow-up task, not something to fake now.

## 5. What this means for positioning

The uncomfortable one first: **"like Cursor" is a hard place to compete.** Cursor's category is crowded and its incumbents are extremely well funded. But §1 of `02-what-to-display.md` established via cross-family check that Cursor's *Background Agents* — launch, leave, monitor, review — is the shape you actually match.

Which suggests the honest positioning is **not** "an AI coding tool." It is closer to:

> **A rigor layer for agent work.** You already have an agent that writes code. This is the thing that decides whether it should, proves the decision survived attack, and knows when to stop.

That framing has three properties worth having: it does not compete with Cursor, it composes with whatever agent the developer already uses, and it is the literal truth about what the engine does — including its willingness to refuse, which no competitor advertises because no competitor can.

**Adjacent risk, named:** you would be positioning against "just use the agent directly," which is free. The burden of proof is a visible, reproducible demonstration that the rigor caught something the bare agent missed. Your ledger already records exactly that — this run overturned two of its own claims in §1. **That artifact is the sales asset.** Ship the UI that renders it.

## 6. Honest ceiling

- One primary-grade growth source (Sequoia on Linear) and two design-principle sources (Figma, linear.app). Everything in §4 is unverified and marked.
- §2's three moves are my synthesis from product observation, **not** from company statements about strategy. Codex's overturn in `02-what-to-display.md` §1 already showed my product-category reasoning can be wrong; treat §2 and §5 as arguable.
- No AI-native company's growth was verified at primary grade. The Linear analogy carries load it was not designed to carry — Linear is not an AI product and grew in a different funding climate.
- No competitive teardown was performed. I did not open Cursor Background Agents, LangSmith, or GitHub Actions and study their actual screens. That is the obvious next research pass and it is cheap.
- Zero customer evidence. No developer other than you has said they want this.
