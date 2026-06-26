# Request Classification & Output

Per-type translation structure (for Step 1 classification in SKILL.md) and writing guidance for each output mode (Step 5). Output language is the user's language (Korean by default); English here is for token efficiency.

## Contents
- A. UX Feedback
- B. UI Component Edit
- C. Visual Style Translation
- D. Reference Interpretation
- E. Accessibility / Usability Fix
- Output Modes — writing guidance

---

## A. UX Feedback
Feedback about the whole screen, user flow, information architecture, conversion goal, or usability.

**Example phrases:** "전체적으로 복잡해 보여" (looks cluttered), "첫 화면에서 뭘 해야 할지 모르겠어" (don't know what to do on the first screen), "가입 버튼이 약해 보여" (sign-up button looks weak), "대시보드가 한눈에 안 들어와" (dashboard doesn't read at a glance), "신뢰감이 없어" (feels untrustworthy).

**Translation structure:** situation / user problem / observable evidence / desired outcome / priority / final feedback sentence.

---

## B. UI Component Edit
Modify a specific component, state, property, or scope.

**Example phrases:** "활성화된 채팅 색이 바뀌었으면 좋겠어", "버튼이 더 눌러보고 싶게 보여야 해", "카드가 너무 밋밋해", "선택된 메뉴가 잘 안 보여", "입력창이 비활성화된 건지 모르겠어".

**Translation structure:** target component / state / property to modify / scope / keep unchanged / accessibility / final edit request.

---

## C. Visual Style Translation
Convert sensory expressions into visual-design language.

**Example phrases:** "깔끔하게", "고급스럽게", "세련되게", "덜 촌스럽게", "좀 더 부드럽게", "강조되게", "차분하게".

**Translation structure:** color / contrast / spacing / typography / corner radius / shadow / information density / visual hierarchy / brand tone.

> Per-word expansion (possible meanings + translation example) is in `dictionaries.md` · **Design Language Dictionary**.

---

## D. Reference Interpretation
The user wants to reference a specific brand/app/service/website. **Do not clone the brand.**

**Example phrases:** "애플처럼", "토스처럼", "노션처럼", "리니어처럼", "에어비앤비처럼", "stripe 느낌으로", "vercel 스타일로".

**Translation structure:** the reference the user named / the screen type being built / elements worth borrowing / elements to exclude / conversion direction for the current product / final request.

> The decomposition procedure and Apple-dashboard example are in `rules.md` · **Reference Interpretation Rules**.

---

## E. Accessibility / Usability Fix
State, meaning, actionability, error, contrast, focus, or label is unclear.

**Example phrases:** "잘 안 보여", "선택된 건지 모르겠어", "눌러지는 건지 모르겠어", "에러가 뭔지 모르겠어", "비활성화된 건지 헷갈려".

**Checklist:** color contrast / color-only state reliance / focus / hover / selected / disabled / error-message specificity / label clarity / keyboard accessibility / screen-reader state conveyance.

> Correction recommendations in `rules.md` · **Accessibility Rules**.

---

## Output Modes — writing guidance
The 18-section standard format is the default; sections 14–17 map to modes 1–4. Shift emphasis by purpose.

### 1. Designer sentence
Collaborative, natural phrasing. **Problem-and-goal centered, not imperative.** "해 주세요" / "방향이 좋겠습니다" tone. Give the reasoning so the designer can judge with context.

### 2. AI design-tool command
Concrete, actionable **imperative**. Component, state, property, scope, keep-conditions explicit. No taste-words — property-centric ("apply a subtle selected background to the entire row"). English often works better for AI-tool compatibility.

### 3. Figma / Penpot comment
Short, location-based. Order: **"problem → evidence → desired result."** One or two sentences. Comments attach to a specific element, so be action-centered, not background-explanatory.

### 4. Developer implementation hints
CSS properties, design tokens, state classes, aria attributes where possible. **Mark "예시" (example) if code isn't finalized** — never present unfinalized code as definitive.

Examples: state class `.chat-list-item.is-selected`; tokens `surface.base` / `color.primary`; aria `aria-selected="true"`; keep `:focus-visible` / `:hover` / `:active`.

### 5. Visualization for feel (render)
When a non-designer can't judge from text, **render options or the result as actual HTML** so they compare and pick by seeing. Two patterns: option-comparison (narrow ambiguity) and before/after (confirm result). Full guidance + reusable HTML skeleton in `visualization.md`.

> Default is the **ONE mode** that fits the receiver (see SKILL.md · Output Modes table). Emit the others only on request ("전체 스페셜", "다 받아줘") — emitting all by default dilutes and wastes tokens.
