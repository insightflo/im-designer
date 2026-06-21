# Examples

Worked examples and bad/good pairs. Use as the quality bar. Output is in the user's language (Korean); English here is for token efficiency. Examples are condensed to the essentials (classification → diagnosis → the 4 sendable sentences + accessibility/priority), not the full 18-section dump.

## Contents
- Example 1 — chat selected color (component edit + accessibility)
- Example 2 — Apple-style dashboard (reference + initial request + style)
- Example 3 — button affordance (component edit + style)
- bad / good pairs

---

## Example 1
**User:** "채팅 목록에서 활성화된 채팅은 색상이 변했으면 좋겠어."

- **Type:** component edit + accessibility check
- **Target:** ChatListItem / ConversationListItem, state `selected`/`active`
- **Problem:** the selected state isn't distinct enough; the user can't instantly tell which chat is open.
- **Evidence:** the active item's visual state isn't sufficiently different from `default`/`hover`.
- **Desired outcome:** the user instantly recognizes the selected chat in the list.
- **Modify:** background (selected row background-color via `color.primary` 10% tint) / typography (title font-weight up if needed) / border (left accent bar if needed) / interaction (selected stronger than hover).
- **Scope:** the entire selected row.
- **Keep:** text color, icon color, list spacing and layout.
- **Accessibility:** don't rely on color alone — pair with a left accent bar or font-weight difference; keep the focus ring separate so keyboard focus and selected don't collide.
- **Priority:** Suggestion (near-Blocker if selection is currently indistinguishable).

**Final sentences:**
- **Designer:** 채팅 목록에서 현재 열려 있는 채팅방이 더 명확히 보이도록 ChatListItem의 selected 상태를 추가해 주세요. 글자색보다는 선택된 row 전체의 background-color를 기본 배경보다 한 단계 강조된 색으로 변경하는 방향이 좋겠습니다. hover보다 selected가 더 강하게, 왼쪽 accent bar나 제목 font-weight 차이도 함께 적용해 주세요.
- **AI-tool command:** Update the ChatListItem selected state. Apply a subtle selected background to the entire active row. Keep text/icon colors, spacing, and layout unchanged. Make selected visually stronger than hover. Add a left accent indicator or increase title font-weight so it's recognizable without color alone.
- **Figma comment:** 선택된 채팅방이 default/hover와 잘 구분되지 않습니다. selected row 전체에 subtle background + left accent bar 또는 font-weight 차이를 추가해 주세요.
- **Dev hints:** `.chat-list-item.is-selected`; bg = `color.primary` 10% tint or neutral surface +1; `aria-selected="true"`; keep `:focus-visible`.
- **Needs confirmation:** background-centered vs left-indicator-centered selected treatment.

---

## Example 2
**User:** "애플처럼 깔끔한 대시보드 만들어줘."

- **Type:** reference interpretation + initial request + style
- **Intent:** not cloning an Apple screen, but applying Apple-like restraint, generous whitespace, clear typography, neutral color, and orderly hierarchy to a data dashboard. "깔끔한" = lower density, remove decoration, data-first.
- **Target:** data dashboard, whole layout (KPI card, chart, sidebar, filter, table).
- **Borrow:** restrained color / generous whitespace / strong typographic hierarchy / neutral background / simple cards / gentle hover-selected / decoration removed / data-first.
- **Exclude:** large hero image / excessive scroll animation / marketing-copy-centric / layouts that over-lower data density / decorative graphics.
- **Accessibility:** chart colors must distinguish series beyond color (labels/legend/pattern/numbers); show rate-of-change with +/− and labels, not color alone; distinguish selected filter/active menu beyond color (background/border/indicator); keep `focus-visible`.
- **Priority:** Question — which Apple layer (iOS app / macOS app / landing page / settings) is the reference? (Though for a dashboard, landing-page elements should be borrowed only sparingly.)

**Final sentences:**
- **Designer:** Apple의 제품 랜딩페이지를 그대로 따라 하기보다는, 절제된 색상, 넓은 여백, 가독성 높은 타이포그래피, 중립적인 배경, 명확한 상태 표현을 참고해 데이터 대시보드에 맞게 적용해 주세요. 핵심 목표는 사용자가 KPI, 차트, 필터 상태를 빠르게 이해하고 의사결정할 수 있게 만드는 것입니다. 대형 히어로 이미지나 감성적 스크롤 연출보다는 카드 기반 정보 구조, 명확한 숫자 위계, 중립 배경, 제한된 포인트 컬러를 우선해 주세요.
- **AI-tool command:** Create a clean Apple-inspired data dashboard without copying Apple's landing page. Use generous spacing, neutral surfaces (base/raised), strong typographic hierarchy, subtle dividers, minimal shadows, restrained accent colors. Prioritize KPI cards, readable charts, clear filters, distinguishable selected states. Structure KPI → primary chart → detail table. Avoid hero sections, gradients, excessive motion, or anything reducing data readability.
- **Figma comment:** "Apple처럼"을 랜딩페이지 복제가 아니라 절제된 색·여백·타이포 위계·중립 배경·명확한 상태 표현으로 해석해 대시보드에 적용해 주세요.
- **Dev hints:** tokens `surface.base`/`surface.raised`/`text.primary`/`text.secondary`/`color.primary`/`border.subtle`; separate KPI card, ChartCard, FilterBar, SidebarNav, DataTable.
- **Needs confirmation:** which Apple screen is the reference; light vs dark mode priority.

---

## Example 3
**User:** "버튼이 좀 더 눌러보고 싶게 보였으면 좋겠어."

- **Type:** component edit + style
- **Target:** Button, states `default`/`hover`/`active`(pressed)
- **Problem:** the button doesn't separate from its surroundings or doesn't read as clickable.
- **Evidence:** weak contrast, size, padding, hover, or label weight.
- **Desired outcome:** the user reads the button as the primary action and feels it's clickable.
- **Modify:** background (stronger CTA background vs surrounding surface or brand primary) / typography (label font-weight up) / spacing (padding; min-height ≥40px) / border (clearer boundary if needed) / shadow (subtle elevation; avoid heavy) / interaction (add hover + pressed with transition).
- **Scope:** the Primary Button only (secondary/ghost out of scope).
- **Keep:** button label text, button position, overall layout, design-system color tokens (no arbitrary hex).
- **Accessibility:** background/text contrast meets WCAG; keep `focus-visible`; default state alone must read as clickable (don't rely on hover); pressed state shouldn't rely on color alone (add subtle transform like `translateY(1px)` or inset shadow).
- **Priority:** Suggestion (near-Blocker if it's the only CTA on a key conversion path).

**Final sentences:**
- **Designer:** Primary Button이 더 명확한 행동 요소로 인식되도록 시각적 위계를 높여 주세요. 배경 대비, padding, label font-weight를 조정하고 hover와 pressed 상태를 추가해 클릭 가능한 느낌을 강화하면 좋겠습니다. 단, 과한 그림자나 장식보다는 현재 디자인 시스템 안에서 자연스럽게 강조되는 방향이 좋습니다.
- **AI-tool command:** Improve the primary button affordance. Increase visual hierarchy via stronger background contrast, comfortable padding, clearer label weight, subtle elevation, and defined hover/pressed states. Add a pressed (active) state with a subtle non-color change (slight bg shift, 1px translate, or inset shadow). Keep position, label text, and layout unchanged. Avoid excessive shadows or decoration.
- **Figma comment:** 버튼의 클릭 가능성이 약해 보입니다. 배경 대비, padding, label weight, hover/pressed 상태로 CTA 위계를 높여 주세요. focus ring은 유지해 주세요.
- **Dev hints:** `.button.primary:hover`/`:active`/`:focus-visible`; bg = brand primary token or surface +1; weight 500→600 (example); min-height ≥40px; `:active` = `translateY(1px)` or inset shadow (example); keep `:focus-visible`; don't hover-rely on touch devices. Values are examples — prefer real design-system tokens.
- **Needs confirmation:** is this button a primary CTA or secondary action? (affects intensity)

---

## bad / good pairs
The typical pattern of converting impression-words into executable language.

- **Bad:** "좀 더 예쁘게 해주세요."
- **Good:** "첫 화면에서 핵심 CTA가 묻혀 사용자가 다음 행동을 빠르게 파악하기 어렵습니다. CTA의 시각적 위계를 높이고, 주변 정보량을 줄여 사용자가 가입 버튼을 먼저 인식하도록 조정해 주세요."

- **Bad:** "채팅 목록에서 활성화된 채팅 색 바꿔주세요."
- **Good:** "ChatListItem의 selected 상태가 더 명확히 보이도록 선택된 row 전체의 background-color를 변경해 주세요. 텍스트 색상은 유지하고, hover보다 selected가 더 강하게 구분되도록 조정해 주세요. 색상만으로 구분되지 않도록 왼쪽 accent bar 또는 font-weight 차이도 함께 적용해 주세요."

> Common pattern: remove the impression-word (예쁘게/눈에 띄게) → replace with concrete properties (hierarchy/contrast/position/property) → add keep-conditions and accessibility conditions.
