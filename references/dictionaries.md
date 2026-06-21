# Dictionaries & Vocabularies

The dictionary that expands taste-words into design properties, plus component / state / property vocabularies. Output language is the user's language (Korean by default); English here is for token efficiency. Korean entries are kept because they are the actual input the skill must recognize.

## Contents
- Design Language Dictionary (taste-words)
- Component Vocabulary
- State Vocabulary
- Editable Properties

---

## Design Language Dictionary (taste-words)
Translate sensory expressions as below. "Possible meanings" shows one word can point several directions; "Translation example" gives the most practical direction as a sentence (in Korean, the runtime output language).

### "예쁘게" (pretty)
**Possible meanings:** visual polish / alignment / spacing unification / color-system cleanup / typographic hierarchy / removing decoration.
**Translation example:** "전체적인 시각 일관성을 높이기 위해 간격, 정렬, 색상 사용, 타이포그래피 위계를 정리해 주세요."

### "깔끔하게" (clean)
**Possible meanings:** lower density / remove unnecessary elements / more whitespace / unified alignment / clearer section separation.
**Translation example:** "사용자가 핵심 정보를 빠르게 파악할 수 있도록 정보 밀도를 낮추고, 섹션 간 여백과 정렬을 정리해 주세요."

### "고급스럽게" (premium)
**Possible meanings:** low saturation / generous whitespace / restrained color / strong typographic hierarchy / removing heavy shadows or decoration / stable layout.
**Translation example:** "과한 장식보다 충분한 여백, 절제된 색상, 명확한 타이포그래피 위계를 사용해 신뢰감 있는 인상을 만들어 주세요."

### "세련되게" (refined)
**Possible meanings:** modern layout / simple palette / consistent radius / orderly spacing scale / light shadow / clear hierarchy.
**Translation example:** "색상과 여백 사용을 절제하고, 컴포넌트의 radius, shadow, spacing을 일관되게 맞춰 현대적인 인상을 만들어 주세요."

### "눈에 띄게" (stand out)
**Possible meanings:** stronger CTA hierarchy / higher contrast / size adjustment / position adjustment / weakening surroundings / accent color.
**Translation example:** "해당 요소가 주변 정보보다 먼저 인식되도록 대비, 크기, 위치, 여백을 조정해 시각적 위계를 높여 주세요."

### "부드럽게" (soft)
**Possible meanings:** lower contrast / generous whitespace / rounder radius / lighter shadow / gentle transitions / non-aggressive color.
**Translation example:** "강한 대비와 날카로운 경계를 줄이고, 적절한 radius와 부드러운 상태 전환을 사용해 더 편안한 인상을 주세요."

### "덜 복잡하게" (less complex)
**Possible meanings:** restructure information architecture / hide low-priority info / grouping / collapsible areas / card-or-section separation / fewer CTAs.
**Translation example:** "사용자의 핵심 작업에 필요한 정보만 먼저 보이도록 정보 구조를 재정리하고, 보조 정보는 접거나 하위 영역으로 이동해 주세요."

> A new taste-word follows the same pattern: (1) list 3–6 possible meanings → (2) pick the direction best fitting the screen context → (3) translate into a property-centered sentence.

---

## Component Vocabulary
Translate the user's everyday phrasing into likely formal component names.

| User phrase (Korean) | Formal name |
|----------------------|-------------|
| 채팅 목록 하나 | ChatListItem / ConversationListItem |
| 선택된 채팅 | selected chat item / active conversation |
| 왼쪽 메뉴 | Sidebar / Navigation rail |
| 상단 메뉴 | Header / Top navigation |
| 버튼 | Button |
| 주요 버튼 | Primary Button |
| 보조 버튼 | Secondary Button |
| 카드 | Card |
| 표 | Table / Data grid |
| 필터 | Filter bar / Filter chip / Select |
| 입력창 | Text field / Input |
| 검색창 | Search input |
| 팝업 | Modal / Dialog |
| 알림 | Toast / Notification |
| 뱃지 | Badge |
| 탭 | Tabs |
| 드롭다운 | Dropdown / Select menu |
| 그래프 | Chart |
| 지표 카드 | KPI card / Metric card |
| 프로필 이미지 | Avatar |
| 상태 점 | Status indicator |
| 구분선 | Divider |
| 체크박스 | Checkbox |
| 토글 | Switch / Toggle |

---

## State Vocabulary
Always distinguish UI state. Without it, the edit lands on the wrong target.

| State | Meaning |
|-------|---------|
| `default` | resting state |
| `hover` | mouse pointer over |
| `active` | being pressed or currently engaged |
| `selected` | chosen |
| `focused` | keyboard focus present |
| `disabled` | inactive |
| `error` | error state |
| `success` | success state |
| `warning` | warning state |
| `loading` | loading |
| `empty` | no data |
| `unread` | not yet read |
| `expanded` | expanded |
| `collapsed` | collapsed |

**Interpretation rule:** when the user says "활성화된 / 현재 보고 있는 / 선택된 / 열려 있는", it usually means `selected` or `active`. In menus/lists/chat rooms, `selected` is more likely correct (navigation context where one item is highlighted at a time).

---

## Editable Properties
Always identify which property is being modified. One request can span several.

**Color:** background-color / text-color / border-color / icon-color / accent-color / overlay-color
**Layout:** width / height / alignment / grid / column / row / position / sticky area / fixed area
**Spacing:** padding / margin / gap / section spacing / item spacing
**Typography:** font-size / font-weight / line-height / letter-spacing / text hierarchy / label style
**Shape:** border-radius / border-width / border-style
**Elevation:** shadow / surface level / z-index / overlay
**Interaction:** hover state / selected state / focus ring / transition / pressed state / disabled state
**Information Architecture:** grouping / ordering / progressive disclosure / hide-show / collapse-expand / primary vs secondary information

> Requests like "눈에 띄게" usually span several properties (Color + Typography + Spacing + IA). Don't narrow to one — translate as a combination that raises hierarchy.
