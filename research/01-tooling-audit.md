# Tooling audit — what will actually make Claude Code produce non-slop design

**Answers seed ask A5.** Run `20260828-123823-depth-engine-product-ui`, stage E1 MOVE-2.
**Date:** 2026-08-28
**Epistemic rule applied:** L-E — every row carries how it was checked. Registry install counts are reported as *what the registry says*, never as adoption.

---

## 0. The headline

Three findings, in order of how much they change what you do:

1. **The command you suggested does not work.** `npx skills add https://uizze.com/` fails. The skill is real and good, but it installs from a different address.
2. **You already have more design tooling installed than you are using.** Eight relevant skills are on your machine right now. §3.
3. **The registry's install counts are not credible as adoption.** The skill you named reports 532,461 installs against a 12-star repo. §2.

---

## 1. Your suggested command, checked

You wrote: `npx skills add https://uizze.com/`

```bash
git ls-remote https://uizze.com/
# fatal: repository 'https://uizze.com/' not found
```

**Why it fails.** `npx skills add <package>` clones a git repository. `uizze.com` is a marketing site, not a git remote. It answers `200 OK` in a browser, which is probably why it looked installable, but there is no repo behind that URL — I also probed `/skills.json`, `/.well-known/skills.json`, and `/api/skills`, all 404.

**The working command:**

```bash
npx skills add uizze/uizze
```

The skill lives in the GitHub repo `uizze/uizze`. Registry id `uizze.com/anti-ui-slop`; the `uizze.com` half is a *display name*, not a fetchable address.

| Property | Value | How checked |
|---|---|---|
| Repo | `uizze/uizze` | `gh repo view` |
| Stars | **12** | `gh repo view` |
| License | MIT | `gh repo view` |
| Created | 2026-07-15 | `gh repo view` |
| Last push | 2026-08-23 | `gh repo view` |
| Registry installs | **532,461** | `skills.sh/api/search` |

## 2. The 12-stars-vs-532k-installs problem

A repo created six weeks ago with 12 stars reports half a million installs. Those two numbers do not describe the same object.

I cannot tell you which is wrong, and I did not find a documented methodology for the counter. What I can tell you is that **this is the third time this exact pattern has appeared in your own records**:

| Prior claim | What checked out | Source |
|---|---|---|
| Scrapling "74k stars" | ~33k | your PDF, C4 |
| everything-claude-code "16k stars" | 117k+ | your PDF, C6 |
| `uizze.com/anti-ui-slop` "532,461 installs" | 12-star repo | this run |

**Rule for this project: never rank a tool by a registry number.** Rank by reading the skill. Which is what I did next.

## 3. What the skill actually says — and it is good

I read `plugins/claude-directory/skills/anti-ui-slop/SKILL.md` from source. Condensed:

> 1. Inspect product intent, primary user job, primary action, existing design system, required states.
> 2. Browse a public catalogue for relevant screens — structural evidence only, never copy branding or layout.
> 3. Record transferable decisions about hierarchy, density, navigation, controls, state behavior, responsive treatment in `.uizze/design-contract.md`.
> 4. Build with the repository's existing tokens and components.
> 5. Test loading, empty, error, success, validation, narrow, wide, keyboard, interaction.
> 6. Run validation, inspect the rendered result, fix every blocking finish-gate issue.
>
> Reject: interchangeable card grids, gradients used as decoration, filler metrics, generic copy, inert controls, weak hierarchy, missing states, design-system drift.

**Your instinct was right.** Three things make this better than most design skills:

- **It writes a design contract to disk** (`.uizze/design-contract.md`). A file on disk is enforceable; a paragraph in a prompt decays. This is the same medium argument your prior report made about the whole engine.
- **It enumerates nine states** and makes them a gate. "Missing states" is the single most common tell of agent-generated UI.
- **It has a finish gate** — a fail-closed check, which is the vocabulary your own laws use.

**One caveat, stated plainly.** The repo description reads "Four free UI skills, focused UIZZE MCP references." There is a commercial hosted MCP behind it. The skill file is honest about this — *"Use this workflow for free. Do not require a UIZZE account… Do not claim a connection that does not exist or block work without MCP."* — which is better behavior than most funnels. But know that it is a funnel.

## 4. What the registry offers, ranked by reading not by number

| Skill | Registry installs | What it is for |
|---|---|---|
| `anthropics/skills/frontend-design` | 828,622 | Anthropic's own frontend aesthetic baseline |
| `vercel-labs/agent-skills/web-design-guidelines` | 585,832 | Vercel's web design rules |
| `uizze.com/anti-ui-slop` → `uizze/uizze` | 532,461 | Design contract + 9-state gate + finish gate |
| `leonxlnx/taste-skill/design-taste-frontend` | 414,632 | Taste/aesthetic pass |
| `nextlevelbuilder/ui-ux-pro-max-skill/ui-ux-pro-max` | 334,273 | Broad UI/UX pass |
| `arvindrk/extract-design-system` | 128,125 | Extract a design system from an existing product |
| `anthropics/skills/brand-guidelines` | 83,101 | Brand consistency |
| `mattpocock/skills/codebase-design` | — | **T2 in your PDF** — Matt Pocock's suite |
| `affaan-m/ecc/design-system` | 7,684 | **T5 in your PDF** — everything-claude-code |

Two of your PDF's named targets (T2 Pocock, T5 everything-claude-code) publish through this same registry. That is a cheaper audit path than scraping his channel.

## 5. What you already have installed — read this before installing anything

This is the finding that should change your afternoon. Your machine already carries:

| Already installed | What it does |
|---|---|
| `design-consultation` (gstack) | Researches the landscape, proposes a full design system — aesthetic, typography, color, layout, spacing, motion — and generates font + color previews |
| `design-html` (gstack) | Generates production-quality HTML/CSS |
| `design-review` (gstack) | Finds visual inconsistency, spacing, hierarchy problems, **and explicitly "AI slop patterns"** |
| `design-shotgun` (gstack) | Generates multiple design variants, opens a comparison board, collects structured feedback |
| `plan-design-review` (gstack) | Designer's-eye review of a *plan*, before code |
| `artifact-design` | Design fundamentals for shareable artifacts |
| `dataviz` | Chart/dashboard design system — directly relevant, see §6 |
| `humanizer` | Removes AI-writing tells from copy — **this is your M4 / F8**, already on disk |

`design-consultation` → `design-shotgun` → `design-html` → `design-review` is a complete design pipeline you already own and have not run.

**This is §8 of your own prior report happening again**: *"Things D1 plans to build that already exist… before designing a mechanism, read the harness documentation. This run has now made that correction three times."* Make it four. The correction is cheap and it keeps recurring, which per that report means it is a missing protocol step, not an insight.

## 6. Recommended stack

**Install (2):**
```bash
npx skills add uizze/uizze
npx skills add anthropics/skills
```
The first for the design-contract + 9-state finish gate. The second for `frontend-design` and `brand-guidelines`.

**Run what you have, in this order:**

| Order | Skill | Why here |
|---|---|---|
| 1 | `design-consultation` | Produces the design system *before* any pixel — colors, type, spacing with stated rationale. This is your "psychology behind the colors" ask (A8), done as research rather than vibes. |
| 2 | `anti-ui-slop` | Writes `.uizze/design-contract.md`. Freeze it. This is the artifact everything downstream is graded against. |
| 3 | `design-shotgun` | Multiple variants + comparison board. Correct for a product with no precedent — you cannot pick the right design for something unseen by reasoning alone; you generate and compare. |
| 4 | `dataviz` | The Depth Engine UI is largely status, coverage, and cost — that is data display, not marketing pages. |
| 5 | `design-html` | Build. |
| 6 | `design-review` + the 9-state gate | Fail-closed finish. |
| 7 | `humanizer` | On every string in the UI. Fixes F8 at the surface. |

**Do not install** the taste/pro-max skills yet. They overlap with what you have, and adding four opinionated design skills at once produces conflicting instructions — which is its own slop generator.

## 7. Honest ceiling

- I read the `anti-ui-slop` SKILL.md and the repo metadata. I did **not** run any of these skills, so I have no evidence about output quality. Rankings here are by *stated method*, not by measured result.
- Install counts are reported as registry output and are contradicted by star counts. Treat the whole column as decorative.
- I did not audit `leonxlnx/taste-skill`, `nextlevelbuilder`, or `arvindrk` at source. They are listed for completeness, not endorsed.
- The gstack skills are listed from your session's skill manifest. I confirmed they are *available*; I did not read their implementations.
