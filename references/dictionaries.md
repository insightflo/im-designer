# 디자인 언어 사전 및 어휘 (Dictionaries & Vocabularies)

감각어를 디자인 속성으로 풀어내는 사전과, 컴포넌트·상태·수정 속성 어휘를 담는다.

## 목차
- Design Language Dictionary (감각어 사전)
- Component Vocabulary (컴포넌트 어휘)
- State Vocabulary (상태 어휘)
- Editable Properties (수정 속성)

---

## Design Language Dictionary (감각어 사전)
사용자의 감각적 표현을 아래처럼 번역한다. "가능한 의미"는 한 단어가 여러 방향으로 해석될 수 있음을 보여주고, "번역 예"는 가장 실무적인 한 방향을 문장으로 준다.

### "예쁘게"
**가능한 의미:** 시각적 완성도 향상 / 정렬 정리 / 간격 통일 / 색상 체계 정리 / 타이포그래피 위계 정리 / 불필요한 장식 제거

**번역 예:** "전체적인 시각 일관성을 높이기 위해 간격, 정렬, 색상 사용, 타이포그래피 위계를 정리해 주세요."

### "깔끔하게"
**가능한 의미:** 정보 밀도 낮추기 / 불필요한 요소 제거 / 여백 확보 / 정렬 통일 / 섹션 구분 명확화

**번역 예:** "사용자가 핵심 정보를 빠르게 파악할 수 있도록 정보 밀도를 낮추고, 섹션 간 여백과 정렬을 정리해 주세요."

### "고급스럽게"
**가능한 의미:** 낮은 채도 / 충분한 여백 / 절제된 색상 / 강한 타이포그래피 위계 / 과한 그림자나 장식 제거 / 안정적인 레이아웃

**번역 예:** "과한 장식보다 충분한 여백, 절제된 색상, 명확한 타이포그래피 위계를 사용해 신뢰감 있는 인상을 만들어 주세요."

### "세련되게"
**가능한 의미:** 현대적인 레이아웃 / 단순한 색상 팔레트 / 일관된 radius / 정돈된 spacing scale / 가벼운 shadow / 명확한 hierarchy

**번역 예:** "색상과 여백 사용을 절제하고, 컴포넌트의 radius, shadow, spacing을 일관되게 맞춰 현대적인 인상을 만들어 주세요."

### "눈에 띄게"
**가능한 의미:** CTA 위계 강화 / 대비 증가 / 크기 조정 / 위치 조정 / 주변 요소 약화 / accent color 적용

**번역 예:** "해당 요소가 주변 정보보다 먼저 인식되도록 대비, 크기, 위치, 여백을 조정해 시각적 위계를 높여 주세요."

### "부드럽게"
**가능한 의미:** 낮은 대비 / 여유 있는 여백 / 둥근 radius / 약한 shadow / 부드러운 transition / 공격적이지 않은 색상

**번역 예:** "강한 대비와 날카로운 경계를 줄이고, 적절한 radius와 부드러운 상태 전환을 사용해 더 편안한 인상을 주세요."

### "덜 복잡하게"
**가능한 의미:** 정보 구조 재정리 / 우선순위 낮은 정보 숨김 / 그룹핑 / 접힘 영역 사용 / 카드·섹션 분리 / CTA 수 줄이기

**번역 예:** "사용자의 핵심 작업에 필요한 정보만 먼저 보이도록 정보 구조를 재정리하고, 보조 정보는 접거나 하위 영역으로 이동해 주세요."

> 새로운 감각어가 들어와도 같은 패턴으로 처리한다: (1) 가능한 의미 3~6개 나열 → (2) 화면 맥락에서 가장 적절한 방향 선택 → (3) 속성 중심 문장으로 번역.

---

## Component Vocabulary (컴포넌트 어휘)
사용자가 말한 표현을 가능한 정식 컴포넌트 이름으로 번역한다.

| 사용자 표현 | 정식 명칭 |
|-------------|-----------|
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

## State Vocabulary (상태 어휘)
UI 상태를 반드시 구분한다. 상태를 명확히 하지 않으면 수정이 엉뚱한 곳에 적용된다.

| 상태 | 의미 |
|------|------|
| `default` | 기본 상태 |
| `hover` | 마우스를 올린 상태 |
| `active` | 누르고 있거나 현재 활성화된 상태 |
| `selected` | 선택된 상태 |
| `focused` | 키보드 포커스가 있는 상태 |
| `disabled` | 비활성 상태 |
| `error` | 오류 상태 |
| `success` | 성공 상태 |
| `warning` | 경고 상태 |
| `loading` | 로딩 상태 |
| `empty` | 데이터 없음 상태 |
| `unread` | 읽지 않음 상태 |
| `expanded` | 펼쳐진 상태 |
| `collapsed` | 접힌 상태 |

**해석 규칙:** 사용자가 "활성화된", "현재 보고 있는", "선택된", "열려 있는"이라고 말하면 대체로 `selected` 또는 `active`로 해석한다. 단, **메뉴/리스트/채팅방에서는 `selected`가 더 적절할 가능성이 높다.** (한 번에 하나가 강조되는 탐색 맥락이므로.)

---

## Editable Properties (수정 속성)
수정 속성은 반드시 아래 중 무엇인지 구분한다. 한 요청에 여러 속성이 섞일 수 있다.

### Color
background-color / text-color / border-color / icon-color / accent-color / overlay-color

### Layout
width / height / alignment / grid / column / row / position / sticky area / fixed area

### Spacing
padding / margin / gap / section spacing / item spacing

### Typography
font-size / font-weight / line-height / letter-spacing / text hierarchy / label style

### Shape
border-radius / border-width / border-style

### Elevation
shadow / surface level / z-index / overlay

### Interaction
hover state / selected state / focus ring / transition / pressed state / disabled state

### Information Architecture
grouping / ordering / progressive disclosure / hide-show / collapse-expand / primary vs secondary information

> "눈에 띄게" 같은 요청은 보통 여러 속성에 걸친다(Color + Typography + Spacing + Information Architecture). 한 속성으로만 좁히지 말고, 위계를 높이는 속성 조합으로 번역한다.
