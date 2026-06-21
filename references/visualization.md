# 체감용 시각화 (Visualization for non-designers) — 모드 5

비전문가는 텍스트 스펙으로 디자인을 판단하지 못한다. 읽는 것보다 **보는 것**으로 결정한다. 이 모드는 번역 결과(옵션이나 최종 결과)를 **실제 HTML로 렌더링**해 눈으로 비교·선택하게 한다.

## 목차
- 언제 렌더링하나
- 두 가지 패턴 (옵션 비교 / before-after)
- 렌더링 원칙 (혼란 방지)
- 접근성 메모 (필수)
- 토큰 기반 (강제)
- 산출물 형식
- 재사용 HTML 골격
- 체크리스트

---

## 언제 렌더링하나
- 사용자가 "보여줘 / 체감 / 어떻게 달라지는지 / 옵션 비교"를 원할 때
- 디자인 용어 없이 막연히 말해서, 텍스트만으로는 의도가 좁혀지지 않을 때
- 모호한 요청을 2~3 해석으로 펼쳐 **눈으로 하나를 고르게** 해야 할 때 → 옵션 비교 패턴
- 최종 방향이 정해진 뒤 **결과를 확인**시켜야 할 때 → before/after 패턴

> 텍스트 스펙(모드 1~4)과 시각화(모드 5)는 보완 관계. 시각화로 방향을 고른 뒤, 그 방향을 모드 1~4 문장으로 확정해 디자이너/개발자에게 전달한다.

---

## 두 가지 패턴

### 1. 옵션 비교 (모호성 → 범위 좁히기)
모호한 요청의 여러 해석을 나란히 렌더링 → 사용자가 눈으로 고르면 그것이 곧 명확한 요청이 된다.
- 구성: **현재(문제) + 옵션 A/B/C** 그리드
- 각 패널: 실제 요소 렌더 + "효과 / 접근성 / 비용" 한 줄 캡션
- 추천 옵션에 표시 + 왜 추천하는지(주로 접근성)

### 2. before / after (결과 확인)
사용자가 고른 방향을 적용한 모습과 현재를 나란히, 또는 적용 결과만 깔끔하게.
- 구성: **결정 요약 + 적용 결과 + 토큰 테이블(기준값) + 접근성 메모**
- "Primary 하나로 selected·버튼·뱃지를 통일"처럼 토큰 재사용을 직접 보여주면 통일성이 체감된다.

---

## 렌더링 원칙 (혼란 방지)
- **옵션은 최대 3개.** 그 이상은 오히려 혼란. (현재 상태는 옵션에서 제외)
- **옵션 간 한 가지 속성만 바꾼다.** (배경 vs 막대 vs 굵기) 여러 속성을 동시에 바꾸면 "뭘 고른 건지" 모호해진다. — 단, "추천 조합" 패널은 예외로 여러 단서를 합친 최적안을 보여줄 수 있다.
- 각 옵션에 **명확한 라벨** + 효과/접근성/비용 **한 줄 메모**.
- **추천 표시**를 붙이고 이유를 적는다.
- 모업은 **최소** — 논의 중인 요소에 집중. 전체 앱을 그리지 않는다.
- 라벨·메모는 한국어(사용자 언어)로.

---

## 접근성 메모 (필수 — 빠뜨리지 말 것)
- 색상에만 의존하는 옵션에는 **"색맹/고대비 모드에서 약해짐"** 표시.
- 각 옵션에 **색상 외 단서(막대/굵기/아이콘/위치) 유무**를 표시.
- 사용자가 "심플"을 원해 색상 단일 단서를 택하더라도, **최소 보정 옵션**(예: 제목 font-weight 1단계 up — 거의 눈에 안 띔)을 제안해 단순함을 유지하면서 안전하게 만들 수 있음을 보여준다. 결정은 사용자.

---

## 토큰 기반 (강제)
- 렌더링에 쓰는 모든 색은 **토큰**이어야 한다 (`references/rules.md` · Color Request Rules 참조).
- CSS 변수를 토큰으로 정의하고(`--c-primary` 등), 모든 요소가 그 변수를 참조하게 한다.
- 임의 hex를 직접 쓰지 않는다. (아바타 등 장식의 다양한 색도 토큰 팔레트 안에서.)
- 적용 결과 패턴에서는 **토큰 테이블**을 함께 보여줘 "기준값"을 눈으로 확인시킨다.

---

## 산출물 형식
- **단일 `.html` 파일** (CSS는 `<style>`에 인라인, 외부 의존성 최소).
- 시스템 폰트 스택(`-apple-system, "Pretendard", "Apple SD Gothic Neo", sans-serif`) — 별도 폰트 로딩 없이 어디서나 깨지지 않게.
- 저장 후 브라우저로 `open`.
- self-contained — 복사/공유 가능.

---

## 재사용 HTML 골격
아래 골격을 복사해 채운다. 토큰은 `:root`에서 한 번 정의 → 전체가 통일. 옵션 비교 패턴의 뼈대.

```html
<!DOCTYPE html>
<html lang="ko"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>im-designer 시각화</title>
<style>
  :root{
    /* 토큰(기준값) — 브랜드 토큰이 있으면 여기만 교체 */
    --c-primary:#2563eb; --c-primary-tint:#e8effd; --c-secondary:#64748b;
    --c-surface-app:#f4f6f9; --c-surface-base:#ffffff;
    --c-text:#1d1d1f; --c-text-subtle:#6e6e73; --c-border:#e5e7eb;
    --radius:12px; --shadow:0 1px 2px rgba(16,24,40,.06),0 1px 3px rgba(16,24,40,.08);
  }
  *{box-sizing:border-box;}
  body{margin:0;background:var(--c-surface-app);color:var(--c-text);
    font-family:-apple-system,BlinkMacSystemFont,"Pretendard","Apple SD Gothic Neo",sans-serif;
    -webkit-font-smoothing:antialiased;line-height:1.5;}
  .wrap{max-width:1100px;margin:0 auto;padding:40px 24px 80px;}
  .eyebrow{font-size:12px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;color:var(--c-primary);}
  h1{font-size:28px;margin:8px 0 6px;letter-spacing:-.01em;}
  .lede{color:var(--c-text-subtle);font-size:15px;max-width:720px;}
  .grid{display:grid;grid-template-columns:repeat(2,1fr);gap:20px;margin-top:24px;}
  @media(max-width:860px){.grid{grid-template-columns:1fr;}}
  .opt{background:var(--c-surface-base);border:1px solid var(--c-border);border-radius:16px;overflow:hidden;box-shadow:var(--shadow);}
  .opt .head{display:flex;align-items:center;gap:10px;padding:16px 18px 8px;}
  .opt .tag{font-size:11px;font-weight:700;padding:3px 8px;border-radius:999px;background:#eef2f7;color:var(--c-text-subtle);}
  .opt.rec .tag{background:var(--c-primary-tint);color:var(--c-primary);}
  .opt .title{font-size:16px;font-weight:700;flex:1;}
  .opt .badge{font-size:11px;font-weight:800;color:#fff;background:var(--c-primary);padding:3px 8px;border-radius:999px;}
  .opt .desc{padding:0 18px 12px;font-size:13px;color:var(--c-text-subtle);}
  /* === 여기에 실제 요소(컴포넌트) 렌더링 CSS 작성 === */
  .note{padding:12px 18px 16px;font-size:12.5px;border-top:1px dashed var(--c-border);background:#fafbfc;color:var(--c-text-subtle);}
  .note b{color:var(--c-text);}
  .ok{color:#15803d;} .warn{color:#b45309;}
</style></head>
<body><div class="wrap">
  <div class="eyebrow">im-designer · 체감용 시각화</div>
  <h1>[요청 한 줄 요약]</h1>
  <p class="lede">[모호한 요청이 N가지로 해석됨 — 눈으로 고르세요]</p>
  <div class="grid">
    <!-- 옵션 A (추천) -->
    <section class="opt rec">
      <div class="head"><span class="tag">옵션 A</span><span class="title">[방향]</span><span class="badge">추천</span></div>
      <div class="desc">[한 줄 설명]</div>
      <!-- 실제 요소 렌더 -->
      <div class="note"><span class="ok"><b>✓</b> [접근성]</span><br><b>[비용/특징]</b></div>
    </section>
    <!-- 옵션 B -->
    <section class="opt"><!-- ... --></section>
  </div>
</div></body></html>
```

---

## 체크리스트 (렌더링 전 확인)
- [ ] 옵션이 2~3개인가 (현재 상태는 별도)
- [ ] 옵션 간 한 속성만 다른가 (추천 조합 패널은 예외)
- [ ] 각 옵션에 라벨 + 효과/접근성/비용 메모가 있는가
- [ ] 색상 의존도(접근성)가 각 옵션에 표시되어 있는가
- [ ] 모든 색이 토큰인가 (임의 hex 없음)
- [ ] 추천이 표시되어 있고 이유가 적혀 있는가
- [ ] 단일 HTML 파일, 시스템 폰트, 외부 의존성 최소인가
