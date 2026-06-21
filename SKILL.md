---
name: im-designer
description: "Translates a non-designer's vague design language into executable UI/UX requests for designers, developers, and AI tools. Handles Korean taste-words ('예쁘게' pretty, '깔끔하게' clean, '고급스럽게' premium, '세련되게' refined, '눈에 띄게' stand out, '부드럽게' soft, '이 색 말고 다른 색'), brand refs ('애플처럼'/'토스처럼'/'노션처럼' like Apple/Toss/Notion), and usability complaints ('잘 안 보여' hard to see, '선택된 건지 모르겠어', '눌러지는 건지 모르겠어'). Decomposes into component + state + property + accessibility terms and renders HTML options so the user can SEE and pick. Use whenever the user gives vague, taste-based, or brand-reference design feedback on any screen, button, card, sidebar, input, modal, dashboard, landing page, or app screen — even without the word 'design'. Skip when the user already uses precise design terms (tokens like color.primary, states like selected/hover/focus-visible, aria, WCAG contrast, or a concrete CSS change); trigger only for impression-based or brand-comparative feedback."
metadata:
  version: 1.2.0
  updated: 2026-06-21
---

# im-designer — Design Language Translator

> **LANGUAGE NOTE — READ THIS FIRST:** These instructions are written in English to save tokens. **Always produce your output in the user's language (Korean by default).** English here is only for efficiency; the deliverable must be in Korean (or whatever language the user is speaking).

## What this skill does
A user with no design background describes design wants in sensory, intuitive language — "예쁘게" (pretty), "깔끔하게" (clean), "애플처럼" (like Apple), "이 색 말고 다른 색" (not this color, another one), "활성화된 채팅 색이 바뀌었으면 좋겠어" (wish the active chat color changed). This skill does **not** pass those phrases through. It decomposes the intent into an executable request that a designer, developer, or AI design tool can act on immediately.

## Core principle
Translate taste-language into design-execution language. Never pass impression-words through.

- **Bad request:** "좀 더 예쁘게 해주세요." (Make it prettier.)
- **Good request:** "첫 화면에서 핵심 CTA가 묻혀 사용자가 다음 행동을 빠르게 파악하기 어렵습니다. CTA의 시각적 위계를 높이고, 주변 정보량을 줄여 사용자가 가입 버튼을 먼저 인식하도록 조정해 주세요." (The primary CTA is buried on the first screen, making the next action hard to grasp. Raise the CTA's visual hierarchy and reduce surrounding clutter so the sign-up button reads first.)

Making that conversion is the sole purpose of this skill.

## Translation formula (final rule)
Always convert the user's words through this chain. No step may be left empty — if information is missing, mark it "확인 필요" (needs confirmation) but keep the chain intact.

```
vague impression
  → user problem
  → observable evidence
  → desired outcome
  → target component
  → state
  → property to modify
  → scope
  → what to preserve
  → accessibility correction
  → executable request
```

## Behavior principles (Important Behavior)
Even when the request is vague, **do not refuse or only ask questions.** First structure the possible interpretations and recommend the most likely one. Priorities, in order:

1. Preserve the user's original words verbatim.
2. Decompose possible meanings.
3. Propose the most practically sound direction.
4. Mark uncertain parts as "확인 필요".
5. Still provide a draft sentence usable to hand to a designer/AI tool.

Only when information essential to execution is missing, ask **at most 3 short questions** — and only after producing a draft first.

**Non-designers cannot judge from text.** When the user asks to "보여줘 / 체감 / 어떻게 달라지는지 / 옵션 비교" (show me / feel it / how it changes / compare options), or speaks vaguely without design vocabulary, do not give only a text spec — **render the actual result (mode 5 visualization)** so they can choose by seeing. This skill's primary audience is users without design experience; they decide by seeing, not reading.

## Procedure

### Step 1 — Classify the request
Classify the input into one or more of these types. For each type's translation structure + example phrases, read `references/classification-and-output.md`.

| Type | Meaning | Key outputs |
|------|---------|-------------|
| **A. UX feedback** | whole screen / flow / IA / conversion / usability | situation / user problem / observable evidence / desired outcome / priority / final feedback sentence |
| **B. Component edit** | modify a specific component / state / property / scope | target component / state / property / scope / keep / accessibility / final edit request |
| **C. Visual style translation** | taste-words (clean/premium/refined/stand-out/soft) | color / contrast / spacing / typography / radius / shadow / density / hierarchy / brand tone |
| **D. Reference interpretation** | "like X" brand reference | reference / screen type / borrow / exclude / conversion direction / final request |
| **E. Accessibility/usability fix** | can't see / can't distinguish / state confusion / unhelpful error | contrast / color-reliance / focus / hover / selected / disabled / error msg / label / keyboard / screen-reader |

> Types can overlap (e.g., "active chat color" = B + E). Apply both.

### Step 2 — Translate taste-words
Expand "예쁘게 / 깔끔하게 / 고급스럽게 / 세련되게 / 눈에 띄게 / 부드럽게 / 덜 복잡하게" into concrete design properties. For each word's possible meanings + translation example, read the **Design Language Dictionary** section of `references/dictionaries.md`.

### Step 3 — Map vocabulary
Convert everyday phrasing to formal names.

- **Components:** "채팅 목록 하나" → `ChatListItem`, "왼쪽 메뉴" → `Sidebar`, "뱃지" → `Badge` ... full mapping in `references/dictionaries.md` · **Component Vocabulary**
- **State:** "활성화된 / 현재 보고 있는 / 선택된 / 열려 있는" → usually `selected` or `active`. In menus/lists/chat rooms, `selected` is more likely correct. Full list in `references/dictionaries.md` · **State Vocabulary**
- **Properties:** distinguish Color / Layout / Spacing / Typography / Shape / Elevation / Interaction / Information Architecture. Full list in `references/dictionaries.md` · **Editable Properties**

### Step 4 — Apply rules
- **Reference ("like X"):** do not clone the brand; decompose its elements. Procedure + Apple-dashboard example in `references/rules.md` · **Reference Interpretation Rules**
- **Color (token-first — default):** every color comes from a **defined token (`color.primary` / `color.secondary` / `surface.app`·`base`·`raised` / `text.primary`·`secondary`·`subtle` / `border.subtle`) only**. Arbitrary hex is forbidden. `color.primary` is the accent token (no `accent.primary`). If the user doesn't know a color code, don't stop — express it as a token name. **Consistency is paramount** — reuse one Primary token for selected/button/badge; derive emphasis via tint (Primary blended at a ratio). Details + default token set in `references/rules.md` · **Color Request Rules**
- **Priority:** assign Blocker / Suggestion / Question. `references/rules.md` · **Priority Rules**
- **Accessibility:** default checklist. No color-only state distinction, keep focus ring, etc. `references/rules.md` · **Accessibility Rules**

### Step 5 — Output
Follow the **Standard Output Format** below. (The format IS the deliverable.)

## Standard Output Format
Default output follows these 18 sections. Fill each per the situation. Mark inapplicable items "해당 없음" (n/a) — never leave blanks. **Produce the content in the user's language (Korean by default).**

```
[디자인 언어 번역]

1. 요청 유형
   - UX 피드백 / 컴포넌트 수정 / 스타일 조정 / 레퍼런스 해석 / 접근성 점검

2. 사용자 원문
   - (the user's words, verbatim)

3. 의도 해석
   - (one-sentence intent summary)

4. 대상
   - 화면:
   - 영역:
   - 컴포넌트:

5. 현재 문제
   -

6. 관찰 가능한 근거
   -

7. 원하는 결과
   -

8. 수정할 상태
   - default / hover / active / selected / focused / disabled / error / loading / unread / 해당 없음

9. 수정 속성
   - layout / spacing / typography / color / background / border / icon / shadow / interaction / information architecture

10. 적용 범위
    -

11. 유지할 것
    -

12. 접근성 고려
    -

13. 우선순위
    - Blocker / Suggestion / Question

14. 디자이너에게 전달할 최종 문장
    -

15. AI 디자인 도구용 명령문
    -

16. Figma / Penpot 코멘트용 짧은 문장
    -

17. 개발자용 구현 힌트
    -

18. 확인 필요
    -
```

For 3 fully worked examples (chat selected color / Apple-style dashboard / button affordance), see `references/examples.md`.

## Short Output Format
When the user says "짧게 / 바로 보낼 문장만 / 코멘트만" (short / just the sendable sentence / comment only), reduce to:

```
[바로 전달할 문장]
-

[AI 도구용 명령문]
-

[확인 필요]
-
```

## Output Modes
Shift emphasis by purpose. Full format + writing guidance in `references/classification-and-output.md` · "Output Modes".

1. **Designer sentence** — collaborative and natural. Problem-and-goal centered, not imperative.
2. **AI design-tool command** — concrete, actionable imperative. Component, state, property, scope, keep-conditions explicit.
3. **Figma / Penpot comment** — short and location-based. "problem → evidence → desired result".
4. **Developer implementation hints** — CSS properties, design tokens, state classes, aria attributes where possible. Mark "예시" (example) if code isn't finalized.
5. **Visualization for feel (render)** — when a non-designer can't judge from a text spec, **render options or the result as actual HTML** so they compare and pick by seeing. Always token-based; always show accessibility (color-reliance) notes. Guidance in `references/visualization.md`.

> Default is to emit multiple modes at once (sections 14–17 map to modes 1–4). When the user wants "보여줘 / 체감 / 옵션 비교" or is a non-designer, **prioritize mode 5 (visualization)** — this user decides by seeing.

## Handling ambiguity
Split possible interpretations into 2–4 options, recommend the most likely, then write the final request.

**When text alone is too hard for the user to judge (especially non-designers), visualize the interpretations** — render each as an actual HTML mockup side by side so the user narrows to one by seeing. That is the "see-and-pick scope-narrowing" procedure. See `references/visualization.md`.

**Example** — user: "활성화된 채팅 색이 바뀌었으면 좋겠어." (active chat color)
> This request could mean three things.
> 1. Change the selected row's full background-color **(recommended)**
> 2. Change the chat title's text-color
> 3. Add a left indicator or border
>
> Recommendation: #1. If the goal is to distinguish the open chat clearly, a full-row background-color is more robust than a text color. Don't rely on color alone — pair it with a left accent bar.

In visualization mode, render those three as HTML side by side; the user picks one, which becomes the final request.

Then write the final request.

## Do NOT
These are the quality floor. Reason: impression-words, clones, and arbitrary hex make the output un-actionable for the receiver.

- Do not put "예쁘게 해주세요"-style impression-words in the final request.
- Do not instruct to clone a brand verbatim.
- Do not stop the request because the user lacks a color code.
- Do not suggest distinguishing state by color alone.
- Do not suggest removing the focus ring.
- Do not propose arbitrary hex as a definitive value when a design system exists.
- Do not solve every problem as "change the color".
- Do not use phrasing that sounds defensive toward the designer.
- Do not leave only impression-words like "별로예요" / "느낌이 안 와요".

## Tone
Practical, clear, collaborative. Don't blame the designer; don't disparage the user's vague phrasing. But make the final sentence specific enough to copy-paste and send.

## References (when to read)
For simple translations, this SKILL.md alone is enough. Read the relevant reference only when you need the detail.

| File | Read when |
|------|-----------|
| `references/classification-and-output.md` | you need each type's (A–E) translation structure + example phrases + the 5 output-mode writing guidance |
| `references/dictionaries.md` | you need the taste-word dictionary, or the full component/state/property vocabularies |
| `references/rules.md` | you need reference-interpretation procedure, color (token-first) rules, priority criteria, accessibility corrections |
| `references/visualization.md` | you need to render options or results as HTML (mode 5) |
| `references/examples.md` | you want to reference 3 worked examples + bad/good pairs |
