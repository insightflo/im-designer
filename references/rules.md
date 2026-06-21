# Rules

Reference interpretation, color request, priority, and accessibility rules. Output language is the user's language (Korean by default); English here is for token efficiency.

## Contents
- Color Request Rules (token-first)
- Reference Interpretation Rules
- Priority Rules
- Accessibility Rules

---

## Color Request Rules (token-first)

### Token-first — the default rule (enforced)
**Every color is chosen from a defined token only. Arbitrary hex (#xxxxxx) is forbidden.** Consistency is paramount.
- Reuse one token for one purpose. Example: if selected background, primary button, and unread badge are all emphasis, unify them on **one `color.primary` token** — change Primary and all three change together, preserving consistency.
- Express emphasis "intensity" as a **tint (Primary blended at a ratio)**, not a new color. Example: selected = Primary 10% tint. When Primary changes, the tint follows automatically.
- If a design-system token already exists, use it first. If none exists, offer the "Default token set" below as a **proposal (example)** and note it should be replaced to match the brand.
- Anywhere an arbitrary code is unavoidable (a throwaway mockup), mark it "예시/제안" (example/proposal) — never present it as definitive.

**Default token set (proposal — starting point when no brand token exists):**

| Token | Example value | Use |
|-------|---------------|-----|
| `color.primary` | #2563eb | primary action / point / emphasis |
| `color.primary.tint` | Primary @10% | selected/active background |
| `color.secondary` | #64748b | secondary action |
| `surface.base` | #ffffff | card / base surface |
| `surface.app` | #f4f6f9 | page background |
| `text.primary` | #1d1d1f | body text |
| `text.subtle` | #6e6e73 | supporting text |
| `border.subtle` | #e5e7eb | divider |

### When the user lacks a color code
**Never force the user to provide a hex code.** Express it in design-system (token) language instead.

**Examples:**
- "use `color.primary` at 10% tint for the selected background"
- "a neutral background one step stronger than the base surface"
- "an emphasis level stronger than hover but weaker than error/warning"
- "keep text color; change only the background-color"
- "don't distinguish state by color alone — pair it with an accent bar"

---

## Reference Interpretation Rules
When the user says "like X", **do not clone the brand.** Never instruct to copy a specific company's or product's proprietary UI verbatim.

**Decomposition procedure:**
1. Identify the reference brand or product.
2. Identify the screen type the user is building.
3. Pick which elements of the reference fit the current screen's purpose.
4. Explicitly exclude what doesn't fit.
5. Convert into design language suited to the current screen's purpose.

### Example: "애플처럼 대시보드" (Apple-style dashboard)

**Wrong interpretation:**
> "Put a large hero image and emotional scroll choreography like Apple's website."

(Why wrong: Apple's product landing page conflicts with a data dashboard's purpose — different screen types.)

**Right interpretation:**
> "Don't clone Apple's product landing page; instead apply its restrained color, generous whitespace, clear typographic hierarchy, high readability, neutral background, and gentle state expression — adapted to the dashboard."

**Borrow:** restrained color / generous whitespace / strong typographic hierarchy / neutral background / simple card structure / gentle hover-selected states / decoration removed / data-first composition.
**Exclude:** landing-page-style large hero image / excessive scroll animation / marketing-copy-centric composition / layouts that lower data density too much / decorative-graphic-centric screens.

**Final request (Korean output):**
> "Apple의 제품 랜딩페이지를 그대로 따라 하기보다는, Apple 계열 디자인에서 느껴지는 절제된 색상, 넓은 여백, 가독성 높은 타이포그래피, 명확한 상태 표현을 참고해 데이터 대시보드에 맞게 적용해 주세요. 핵심 목표는 사용자가 KPI, 차트, 필터 상태를 빠르게 이해하고 의사결정할 수 있게 만드는 것입니다."

> Apply this same pattern to other brands (Toss/Notion/Linear/stripe/vercel). The key is explicitly stating what to borrow and what to discard, judged by screen purpose.

---

## Priority Rules
Attach a priority to every feedback or edit request, so the receiver knows where to start.

### Blocker
The user cannot complete the task. **Fix first.**
Examples: button invisible / no next step / no error-recovery path / required inputs unclear / selected state entirely indistinguishable.

### Suggestion
Currently usable but could be better.
Examples: CTA slightly weak / card spacing tight / text hierarchy less clear / high visual density / weak hover.

### Question
Intent needs confirming first.
Examples: why is this info on the first screen? / who is the main user of this button? / is this state `selected` or `active`? / was the reference meant for a landing page or an app?

> Priority is not static. "Selected-state distinction" can be Suggestion or near-Blocker depending on context — judge from the observable evidence.

---

## Accessibility Rules
Accessibility is **not optional** — it is a default checklist.

**Always include accessibility corrections when:**
- Distinguishing state by color
- Expressing selected / active / error / disabled states
- Emphasizing a CTA
- Editing forms, inputs, or error messages
- Information-interpretation-heavy screens (dashboards, tables, charts)

**Recommended corrections:**
- Never express state by color alone. (Info vanishes for color-blind / low-vision users and in high-contrast modes.)
- For `selected`, pair the background with one of: left accent bar, border, icon, or font-weight.
- Never remove the focus ring. (It's the keyboard user's only location cue.)
- For `disabled`, don't just lower opacity — keep text readable.
- Error messages must say what's wrong and how to fix it. (Never just "잘못됨".)
- Charts must not rely on color alone — pair with labels, legends, patterns, and numeric display.

**Why it matters:** color/contrast/state problems are invisible to fully-sighted users but fully block function for others. "Included by default" means "you need an explicit reason to omit it," not "add it if convenient."
