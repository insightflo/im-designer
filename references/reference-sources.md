# Reference sources — pull objective tokens for "like X" requests

> **로드 시점**: a "like X" / "X처럼" request names a real brand or product (Apple, Toss, Notion, Linear, Stripe, Vercel, Cursor…). Read this **before** decomposing the reference, so you pull real color/type/spacing tokens instead of guessing.

## Core rule (do not contradict the "no clone" rule)
- **Never clone a brand's UI verbatim.** Keep the decompose-then-adapt procedure from `rules.md` · Reference Interpretation Rules.
- **But the objective, non-expressive tokens are fair game to pull from a structured source** — exact accent hex, type scale ratios, spacing scale, radius, shadow style. These are measurements, not the brand's expression. Guessing them makes the adaptation wrong; pulling them makes it faithful.

So: borrow **tokens and rules** (color values, type scale, spacing cadence, elevation style, density), never the **composition** (layout choreography, hero imagery, marketing structure). Judge each by whether it fits the current screen's purpose.

## Structured sources (ready-to-use token libraries)
These extract complete design systems from real products into a format you can read directly:

| Source | What it gives | When to use |
|---|---|---|
| **Refero Styles** (`styles.refero.design`) | `DESIGN.md` per product — full palette (named tokens + hex + use), type scale (size/weight/tracking/line-height per step), spacing & shape table, elevation, DO/DON'T rules. ~2,000 products. | A "X처럼" request names a product in the catalog. This is the richest single source — read the product's style page and lift tokens+rules verbatim into your token table. |
| **awesome-design-md** (`github.com/voltagent/awesome-design-md`) | Community DESIGN.md collection by brand; drop-in context. | Refero lacks the brand, or you want a second token set to cross-check. |
| The product's own design/docs site | Official tokens when the brand publishes them (e.g. Stripe, Vercel/Geist, Radix, shadcn). | When the brand ships an open token table — that is ground truth, prefer it over any extractor. |

## How to use a source in this skill
1. Identify the named reference + the screen type you are building (Reference Interpretation Rules).
2. Pull the source's **palette + type scale + spacing/shape + elevation rules** into your token set. Map them onto this skill's token names (`color.primary` / `surface.app`·`base`·`raised` / `text.*` / `border.subtle`). Keep token-first discipline — no arbitrary hex.
3. Explicitly **exclude** what doesn't fit the screen's purpose (e.g. exclude Apple's landing-page hero choreography when building a data dashboard; exclude a dark dev-tool's neon if the target is a light docs library).
4. Adapt to the **current brand** if one exists — e.g. if the product's identity is warm paper, keep the warm substrate and borrow only the reference's type hierarchy / whitespace, not its cool canvas. Brand-fit is a hard filter (a cool reference applied to a warm brand can read as a rebrand — flag it).
5. Render the adapted tokens as a real HTML mockup (mode 5) with a token table, so the user sees both the direction and the baseline values.

## Two-axis decomposition — visual style vs UX pattern
Do not borrow a whole service. Split the reference on **two independent axes** — you may take visual style from product A and UX structure from product B:

| Axis | What you borrow | Example |
|---|---|---|
| **Visual Style** | color, type, surface, whitespace, radius, icon style, mood | Cursor's warm-paper palette + Orange accent |
| **UX Pattern** | navigation, IA, search, filter, list/table, detail, form, states | master-detail, sticky section nav, progressive disclosure |

For each element you consider borrowing, split into **apply** (take this principle) vs **doNotApply** (this fits the reference but not our screen). "이 사이트는 색은 좋은데 타이포는 우리 제품엔 과하다" is the model — record both sides.

**Render it, don't just list it.** In reference mode, render an apply/doNotApply comparison panel: left = "가져올 원칙(apply)" with the borrowed element applied, right = "버릴 것(doNotApply)" with why it doesn't fit this screen's purpose. This makes the decomposition visible and choosable, the same way option-compare makes a direction choosable.

This prevents the two classic reference failures: (a) cloning a whole site's composition, (b) rejecting a good reference because one axis (e.g. its marketing hero) doesn't fit, while its visual style is exactly right.

## Honest limits
- Extractors reflect a snapshot of a site; verify against the live site if a value looks off.
- A brand's *feel* is more than its tokens — composition, motion, copy tone. Tokens get you 70%; the rest is the decompose/adapt step. Do not present token-lifting as a substitute for judgment.
- Some brands are deliberately not in any library (proprietary, NDA). Then fall back to the manual decompose procedure in `rules.md` — do not fabricate tokens; mark guesses `[확인 필요]`.
