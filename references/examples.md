# 예시 (Examples)

완성된 3개 예시와 bad/good 쌍을 담는다. 출력 품질의 기준점으로 사용한다.

## 목차
- Example 1 — 채팅 selected 색 (컴포넌트 수정 + 접근성)
- Example 2 — 애플풍 대시보드 (레퍼런스 + 초기 요청 + 스타일)
- Example 3 — 버튼 affordance (컴포넌트 수정 + 스타일)
- bad / good 쌍 모음

---

## Example 1
**사용자:** "채팅 목록에서 활성화된 채팅은 색상이 변했으면 좋겠어."

```
[디자인 언어 번역]

1. 요청 유형
   - 컴포넌트 수정
   - 접근성 점검

2. 사용자 원문
   - 채팅 목록에서 활성화된 채팅은 색상이 변했으면 좋겠어.

3. 의도 해석
   - 현재 열려 있거나 선택된 채팅방을 목록에서 더 명확히 구분하고 싶은 요청입니다.

4. 대상
   - 화면: 채팅 화면
   - 영역: 채팅 목록
   - 컴포넌트: ChatListItem / ConversationListItem

5. 현재 문제
   - selected 상태가 충분히 구분되지 않아 사용자가 현재 어느 채팅을 보고 있는지 즉시 인식하기 어렵습니다.

6. 관찰 가능한 근거
   - 활성 채팅의 시각적 상태가 default 또는 hover 상태와 충분히 다르지 않은 것으로 보입니다.

7. 원하는 결과
   - 사용자가 현재 선택된 채팅방을 목록에서 즉시 인식할 수 있어야 합니다.

8. 수정할 상태
   - selected / active

9. 수정 속성
   - background: selected row background-color 변경
   - typography: 필요 시 title font-weight 강화
   - border: 필요 시 left accent bar 추가
   - interaction: hover 상태와 selected 상태 구분

10. 적용 범위
    - 선택된 채팅 item의 row 전체

11. 유지할 것
    - 텍스트 색상은 기본적으로 유지
    - 아이콘 색상은 유지
    - 리스트 간격과 레이아웃은 유지

12. 접근성 고려
    - 색상만으로 선택 상태를 구분하지 않도록 left accent bar 또는 font-weight 차이를 함께 적용합니다.
    - 키보드 focus 상태와 selected 상태가 충돌하지 않도록 focus ring은 별도로 유지합니다.

13. 우선순위
    - Suggestion
    - 단, 현재 선택 상태를 거의 구분할 수 없다면 Blocker에 가까움

14. 디자이너에게 전달할 최종 문장
    - 채팅 목록에서 현재 열려 있는 채팅방이 더 명확히 보이도록 ChatListItem의 selected 상태를 추가해 주세요.
      글자색을 바꾸기보다는 선택된 row 전체의 background-color를 기본 배경보다 한 단계 강조된 색으로 변경하는 방향이 좋겠습니다.
      hover 상태와 selected 상태가 헷갈리지 않도록 selected 상태를 더 강하게 표현하고, 가능하면 왼쪽 accent bar나 제목 font-weight 차이도 함께 적용해 주세요.

15. AI 디자인 도구용 명령문
    - Update the ChatListItem selected state. Apply a subtle selected background color to the entire active row.
      Keep existing text colors, icon colors, spacing, and layout unchanged. Make the selected state visually stronger than hover.
      Add a left accent indicator or increase the title font-weight so the active conversation is recognizable without relying only on color.

16. Figma / Penpot 코멘트용 짧은 문장
    - 선택된 채팅방이 default/hover 상태와 잘 구분되지 않습니다. selected row 전체에 subtle background를 적용하고, left accent bar 또는 font-weight 차이를 추가해 주세요.

17. 개발자용 구현 힌트
    - selected 상태 클래스 예시: .chat-list-item.is-selected
    - 변경 예시: background-color는 brand primary의 8~12% tint 또는 neutral surface +1 level 사용
    - aria-selected="true" 적용 고려
    - focus-visible 스타일 유지

18. 확인 필요
    - selected 상태를 background 중심으로 표현할지, left indicator 중심으로 표현할지 확인이 필요합니다.
```

---

## Example 2
**사용자:** "애플처럼 깔끔한 대시보드 만들어줘."

```
[디자인 언어 번역]

1. 요청 유형
   - 레퍼런스 해석
   - 초기 디자인 요청
   - 스타일 조정

2. 사용자 원문
   - 애플처럼 깔끔한 대시보드 만들어줘.

3. 의도 해석
   - Apple의 특정 화면을 그대로 복제하려는 요청이 아니라, Apple 계열 디자인에서 느껴지는 절제감,
     넓은 여백, 명확한 타이포그래피, 중립적인 색감, 정돈된 정보 위계를 대시보드에 적용하려는 요청으로 해석합니다.

4. 대상
   - 화면: 데이터 대시보드
   - 영역: 전체 레이아웃
   - 컴포넌트: KPI card, chart, sidebar, filter, table

5. 현재 문제
   - 아직 구체 디자인이 없다면 문제는 없음.
   - 다만 "애플처럼"이라는 표현은 iOS 앱, macOS 앱, 제품 랜딩페이지, 설정 화면 등 여러 기준으로 해석될 수 있어 범위가 모호합니다.

6. 관찰 가능한 근거
   - 레퍼런스 브랜드만 제시되어 있고, 어떤 화면 유형의 어떤 요소를 가져올지 명시되어 있지 않습니다.

7. 원하는 결과
   - 대시보드 사용자가 핵심 지표, 차트, 필터 상태를 빠르게 이해하고 의사결정할 수 있어야 합니다.

8. 수정할 상태
   - 해당 없음

9. 수정 속성
   - layout: 넓은 여백과 명확한 섹션 구조
   - spacing: 충분한 카드 간격과 그룹 간 여백
   - typography: 숫자, 제목, 보조 설명의 위계 명확화
   - color: 중립 배경과 제한된 accent color
   - background: surface level을 활용한 카드 구분
   - border: 과한 테두리보다 은은한 구분선
   - icon: 기능 설명에 필요한 경우만 제한적으로 사용
   - shadow: 약하거나 최소화
   - information architecture: KPI → 주요 차트 → 상세 테이블 순서

10. 적용 범위
    - 대시보드 전체 UI 스타일과 정보 구조

11. 유지할 것
    - 데이터 가독성
    - 차트 해석 가능성
    - 필터와 상태의 명확성
    - 대시보드의 정보 밀도

12. 접근성 고려
    - 차트 색상은 의미 구분이 가능해야 합니다.
    - 수치 변화율은 색상뿐 아니라 +/− 기호와 라벨로 함께 표현합니다.
    - 선택된 필터와 활성 메뉴는 색상 외에 배경, border, indicator 등으로 구분합니다.

13. 우선순위
    - Question
    - 레퍼런스의 어느 층을 가져올지 확인이 필요하기 때문입니다.

14. 디자이너에게 전달할 최종 문장
    - Apple의 제품 랜딩페이지를 그대로 따라 하기보다는, Apple 계열 디자인에서 느껴지는 절제된 색상, 넓은 여백,
      가독성 높은 타이포그래피, 명확한 상태 표현을 참고해 데이터 대시보드에 맞게 적용해 주세요.
      핵심 목표는 사용자가 KPI, 차트, 필터 상태를 빠르게 이해하고 의사결정할 수 있게 만드는 것입니다.
      대형 히어로 이미지나 감성적인 스크롤 연출보다는 카드 기반 정보 구조, 명확한 숫자 위계, 중립적인 배경, 제한된 포인트 컬러를 우선해 주세요.

15. AI 디자인 도구용 명령문
    - Create a clean Apple-inspired data dashboard without copying Apple's product landing page.
      Use generous spacing, neutral surfaces, strong typographic hierarchy, subtle dividers, minimal shadows, and restrained accent colors.
      Prioritize KPI cards, readable charts, clear filters, and selected states.
      Avoid large marketing hero sections, decorative gradients, excessive motion, or visual elements that reduce data readability.

16. Figma / Penpot 코멘트용 짧은 문장
    - "Apple처럼"을 제품 랜딩페이지 복제가 아니라 절제된 색상, 넓은 여백, 타이포 위계, 중립 배경, 명확한 상태 표현으로 해석해 대시보드에 맞게 적용해 주세요.

17. 개발자용 구현 힌트
    - token 예시:
      surface.base / surface.raised / text.primary / text.secondary / accent.primary / border.subtle
    - KPI card, ChartCard, FilterBar, SidebarNav, DataTable 컴포넌트 분리 권장

18. 확인 필요
    - 참고하려는 Apple 화면이 iOS 앱인지, macOS 앱인지, 제품 랜딩페이지인지 확인하면 더 정확해집니다.
    - 그러나 대시보드 목적상 제품 랜딩페이지 요소는 제한적으로만 참고하는 것이 적절합니다.
```

---

## Example 3
**사용자:** "버튼이 좀 더 눌러보고 싶게 보였으면 좋겠어."

```
[디자인 언어 번역]

1. 요청 유형
   - 컴포넌트 수정
   - 스타일 조정

2. 사용자 원문
   - 버튼이 좀 더 눌러보고 싶게 보였으면 좋겠어.

3. 의도 해석
   - 버튼의 클릭 가능성과 CTA 주목도를 높이고 싶은 요청입니다.

4. 대상
   - 컴포넌트: Button
   - 상태: default / hover / active

5. 현재 문제
   - 버튼이 주변 요소와 충분히 구분되지 않거나, 클릭 가능한 요소처럼 보이지 않을 수 있습니다.

6. 관찰 가능한 근거
   - 버튼의 대비, 크기, 여백, hover 상태, label 위계가 약할 가능성이 있습니다.

7. 원하는 결과
   - 사용자가 버튼을 주요 행동 요소로 인식하고 클릭 가능하다고 느껴야 합니다.

8. 수정할 상태
   - default / hover / active

9. 수정 속성
   - background: CTA 배경 강조
   - typography: label font-weight 조정
   - spacing: padding 확보
   - border: 필요 시 명확한 경계
   - interaction: hover/pressed 상태 추가

10. 적용 범위
    - Primary Button 전체

11. 유지할 것
    - 버튼 label 문구
    - 버튼 위치
    - 전체 레이아웃

12. 접근성 고려
    - 배경색과 텍스트 대비 확보
    - focus-visible 상태 유지
    - hover에만 의존하지 않고 기본 상태에서도 클릭 가능성이 보여야 함

13. 우선순위
    - Suggestion

14. 디자이너에게 전달할 최종 문장
    - Primary Button이 더 명확한 행동 요소로 인식되도록 시각적 위계를 높여 주세요.
      버튼의 배경 대비, padding, label font-weight를 조정하고, hover와 pressed 상태를 추가해 클릭 가능한 느낌을 강화하면 좋겠습니다.
      단, 과한 그림자나 장식보다는 현재 디자인 시스템 안에서 자연스럽게 강조되는 방향이 좋습니다.

15. AI 디자인 도구용 명령문
    - Improve the primary button affordance. Increase visual hierarchy through stronger background contrast,
      comfortable padding, clearer label weight, and defined hover and pressed states.
      Keep the button position and label unchanged. Avoid excessive shadows or decorative effects.

16. Figma / Penpot 코멘트용 짧은 문장
    - 버튼의 클릭 가능성이 약해 보입니다. 배경 대비, padding, label weight, hover/pressed 상태를 조정해 CTA 위계를 높여 주세요.

17. 개발자용 구현 힌트
    - button.primary:hover 상태 추가
    - button.primary:active 상태 추가
    - focus-visible outline 유지
    - min-height 40px 이상 권장

18. 확인 필요
    - 이 버튼이 primary CTA인지 secondary action인지 확인 필요
```

---

## bad / good 쌍 모음
감상어가 실행 언어로 바뀌는 전형적 패턴. 번역 시 이 방향성을 유지한다.

**나쁜 요청 → 좋은 요청:**

- "좀 더 예쁘게 해주세요."
  → "첫 화면에서 핵심 CTA가 묻혀 사용자가 다음 행동을 빠르게 파악하기 어렵습니다. CTA의 시각적 위계를 높이고, 주변 정보량을 줄여 사용자가 가입 버튼을 먼저 인식하도록 조정해 주세요."

- "채팅 목록에서 활성화된 채팅 색 바꿔주세요."
  → "ChatListItem의 selected 상태가 더 명확히 보이도록 선택된 row 전체의 background-color를 변경해 주세요. 텍스트 색상은 유지하고, hover 상태보다 selected 상태가 더 강하게 구분되도록 조정해 주세요. 색상만으로 구분되지 않도록 왼쪽 accent bar 또는 font-weight 차이도 함께 적용해 주세요."

> 공통 패턴: 감상어(예쁘게/눈에 띄게)는 제거 → 구체적 속성(위계/대비/위치/속성)으로 교체 → 유지 조건·접근성 조건 추가.
