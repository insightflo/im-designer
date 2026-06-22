# Visualization for non-designers — Mode 5

A non-designer cannot judge a design from a text spec. They decide by **seeing**, not reading. This mode renders the translation result (options or final result) as **actual HTML** so the user can compare and pick visually.

## Contents
- When to render
- Two patterns (option-compare / before-after)
- Rendering principles (prevent confusion)
- Accessibility notes (required)
- Token-based (enforced)
- Deliverable format
- Reusable HTML skeleton
- Checklist

---

## When to render
- The user asks to "보여줘 / 체감 / 어떻게 달라지는지 / 옵션 비교" (show me / feel it / how it changes / compare options)
- The user speaks vaguely without design vocabulary, so text alone can't narrow the intent
- An ambiguous request needs to be split into 2–3 interpretations and the user must **pick one by seeing** → option-compare pattern
- After the final direction is chosen, the result needs confirming → before/after pattern

> Text spec (modes 1–4) and visualization (mode 5) are complementary. Narrow the direction visually, then confirm it as modes-1–4 sentences for the designer/developer.

---

## The render → reaction → refine loop

A render is a **conversation surface**, not a one-shot answer. The highest-signal design feedback often comes from the user reacting to a concrete render — not from your own aesthetic judgment.

```
render options (mode 5)
   → elicit reaction ("어느 쪽? 왜? 거슬리는 거?")
   → read the reaction as a constraint (often a flaw you missed)
   → re-render with the constraint applied (before/after)
   → confirm by seeing
   ↻ repeat until the direction is locked
```

Why this matters:
- A non-designer can spot a **structural** problem on a render that token-level analysis misses — e.g. "두 테두리가 겹쳐 보인다" (nested borders), "여백이 너무 넓다", "강조가 안 된다". That reaction is data; fold it back into the next render.
- Treat the user's rendered-output feedback as the **top-priority signal**, not noise to defend against. If it contradicts a judge/score or your recommendation, the reaction usually wins — re-render with it applied and show before/after.
- After the direction locks, **then** write the modes-1–4 sentences (designer/dev/AI-tool) so the chosen direction is hand-offable.

Do NOT: render once → "pick one" → jump to the final prose request. If the reaction surfaces a new constraint, re-render before finalizing.

---

## Two patterns

### 1. Option-compare (ambiguity → scope-narrowing)
Render the interpretations of an ambiguous request side by side; the user picks one by seeing, which becomes the clear request.
- Layout: **current(problem) + option A/B/C** grid
- Each panel: the actual element rendered + a one-line "effect / accessibility / cost" caption
- Mark the recommended option + why (usually accessibility)

### 2. Before / After (result confirmation)
Show the chosen direction applied, next to current — or just the applied result cleanly.
- Layout: **decision summary + applied result + token table (baseline values) + accessibility note**
- Showing "one Primary token unifies selected/button/badge" makes consistency tangible.
- Reuse the option-compare skeleton below — replace the multi-option `.grid` with a single applied-result panel, and append a token `<table>` listing the baseline values (per the Deliverable format). A minimal token-table fragment:

```html
<table class="tokens">
  <tr><th>Token</th><th>Value</th><th>Use</th></tr>
  <tr><td><span class="swatch" style="background:var(--c-primary)"></span>color.primary</td><td><code>#2563eb</code></td><td>primary action / accent</td></tr>
  <tr><td><span class="swatch" style="background:var(--c-primary-tint)"></span>color.primary.tint</td><td><code>Primary @10%</code></td><td>selected background</td></tr>
</table>
```

---

## Rendering principles (prevent confusion)
- **Render 2–3 options (never 1, never 4+).** More causes confusion. (Current state is separate, not an option.)
- **Vary only one property between options** (background vs bar vs weight). Changing several at once makes "which did I pick?" ambiguous. — Exception: a "recommended combo" panel may combine multiple cues as the optimal answer.
- Each option gets a **clear label** + one-line effect/accessibility/cost **note**.
- **Mark the recommendation** and explain why.
- **Minimal mockups** — focus on the element under discussion; don't draw the whole app.
- Labels and notes in the user's language (Korean by default).

---

## Accessibility notes (required — don't skip)
- Mark color-only-reliant options as **"weakens in color-blind/high-contrast mode"**.
- For each option, note whether a **non-color cue** (bar/weight/icon/position) is present.
- Even if the user picks a single color cue for "simplicity", show a **minimal-reinforcement option** (e.g., bump title font-weight one step — barely visible) that preserves simplicity while staying safe. The user decides.

---

## Token-based (enforced)
- Every color in the render must be a **token** (see `rules.md` · Color Request Rules).
- Define CSS variables as tokens (`--c-primary`, etc.); every element references the variable.
- No arbitrary hex directly (even decorative avatar colors stay within the token palette).
- In the applied-result pattern, show a **token table** so the "baseline values" are visible.

---

## Deliverable format
- **A single `.html` file** (CSS inline in `<style>`; minimal external dependencies).
- System font stack (`-apple-system, "Pretendard", "Apple SD Gothic Neo", sans-serif`) — renders everywhere without font loading.
- Save then `open` in the browser.
- Self-contained — copyable and shareable.

---

## Reusable HTML skeleton
Copy and fill this skeleton. Tokens are defined once in `:root` → everything stays unified. Backbone of the option-compare pattern.

```html
<!DOCTYPE html>
<html lang="ko"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>im-designer visualization</title>
<style>
  :root{
    /* tokens (baseline values) — replace here if brand tokens exist */
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
  /* === write the actual element (component) render CSS here === */
  .note{padding:12px 18px 16px;font-size:12.5px;border-top:1px dashed var(--c-border);background:#fafbfc;color:var(--c-text-subtle);}
  .note b{color:var(--c-text);}
  .ok{color:#15803d;} .warn{color:#b45309;}
</style></head>
<body><div class="wrap">
  <div class="eyebrow">im-designer · visualization</div>
  <h1>[one-line request summary]</h1>
  <p class="lede">[ambiguous request has N interpretations — pick by seeing]</p>
  <div class="grid">
    <!-- Option A (recommended) -->
    <section class="opt rec">
      <div class="head"><span class="tag">옵션 A</span><span class="title">[direction]</span><span class="badge">추천</span></div>
      <div class="desc">[one-line description]</div>
      <!-- actual element render -->
      <div class="note"><span class="ok"><b>✓</b> [accessibility]</span><br><b>[cost/feature]</b></div>
    </section>
    <!-- Option B -->
    <section class="opt"><!-- ... --></section>
  </div>
</div></body></html>
```

---

## Checklist (before rendering)
- [ ] 2–3 options (current state separate)
- [ ] only one property varies between options (recommended-combo panel excepted)
- [ ] each option has a label + effect/accessibility/cost note
- [ ] color-reliance (accessibility) marked per option
- [ ] all colors are tokens (no arbitrary hex)
- [ ] recommendation marked with reason
- [ ] single HTML file, system font, minimal dependencies
- [ ] **anti-generic gate** — every decorative element answers "제품 목적/사용자 행동을 어떻게 돕는가?"; no baseless gradient / card overuse / oversized hero / fake stats / glow (see `anti-generic.md`)
- [ ] **self-check gate** — render passes this skill's own rules: token-first, no color-only state, focus ring kept, WCAG AA contrast, clear hierarchy. If you can see it's wrong, fix before output
