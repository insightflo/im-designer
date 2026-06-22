# Anti-generic — guard your render against AI-slop

> **로드 시점**: you are about to render (mode 5). Read this so the HTML you produce does not collapse into the same generic AI design everyone gets — baseless gradients, card overuse, oversized hero.

## Why this exists
Without an explicit direction, the model regresses to the **mode of its training distribution** — "modern SaaS landing page" = 보라/파랑 그라데이션 + card grid + giant hero + kicker labels. A non-designer asking "예쁘게/세련되게" leaves that direction empty, so the average fills the gap. Your job is to fill the gap with *purpose*, not to ban elements.

## The single question (this is a gate, not a ban)
For every decorative element in your render, ask:

> **"이 요소가 제품 목적 / 사용자 행동을 어떻게 돕는가?"**

- Answer tied to purpose/user-action → keep it.
- Answer is only "예뻐서 / 허전해서 / 요즘 다들 그래서 / AI가 자동으로 줘서" → it's a slop signal. Remove or justify.

Nothing here is forbidden. Gradients, cards, heroes, glow are all correct *in the right place*. The anti-pattern is **purposelessness**, not the element.

## Scope — what token-first already covers
The baseless **보라/파랑 그라데이션** case is already blocked by this skill's token-first color rule (no arbitrary hex, single accent, emphasis via tint). You will rarely see it. So this catalog focuses on the slop that **token-first does NOT catch** — structural/compositional defaults that survive even with a disciplined palette.

## The slop catalog (what the color rule misses)

| # | Slop | Why it appears | The fix (not "ban it") |
|---|------|----------------|------------------------|
| 1 | Everything-in-a-card (text/stats/links boxed) | cards cheaply read as "organized" | cards only for independent clickable units (item/conversation/project); lists/tables + dividers for comparable data; group via heading/whitespace/bg-tone |
| 2 | Oversized hero headline + marketing copy on a *tool* screen | landing-page reflex on an app screen | first-fold = the core task; hero belongs on marketing, not a work tool |
| 3 | Fake stats / placeholder numbers | to fill space | never fabricate; leave `[확인 필요]` if a real number is needed |
| 4 | Decorative glow / glassmorphism / kicker-label spam | "premium" reflex | remove unless it serves state, hierarchy, or a confirmed brand identity |
| 5 | Repeated identical 3-column "feature" grid / uniform section structure | template default | vary hierarchy; asymmetric when content warrants |
| (ref) | Baseless 보라/파랑 gradient | "modern SaaS" mood-default | **already covered by token-first** — listed only so you recognize it if a user pastes foreign markup; 1 accent token, color = state/hierarchy only |

## 5 exception conditions (an element stops being slop when any one holds)
1. Explicitly part of the chosen design system / tokens.
2. Directly tied to brand identity.
3. Actually needed for information structure / state communication.
4. Approved by the user (their choice / AskUserQuestion).
5. Neutral-or-helpful for accessibility/usability.

→ When in doubt, drop it. The render should look like it was made *for this product*, not pulled from the average.

## How to use in this skill
- Run the single question over your rendered HTML **before** showing it (the "Before you render" gate in SKILL.md).
- When you recommend an option that *uses* a catalog element (e.g. a card grid), state which exception justifies it — that's the decision provenance.
- This catalog is a subset; for a full 20-pattern breakdown see the source methodology (design-director `references/anti-patterns.md`). Keep this file short — the question matters more than the list.
