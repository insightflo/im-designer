# Changelog

## v1.2.0 — 2026-06-21 (first public release)

- **English instructions, Korean output.** Instructions / rules / format labels rewritten in English to save tokens (~half the token cost vs Korean, since Korean is ~2–3× more tokens per character). Runtime output stays Korean via a top-of-file `LANGUAGE NOTE`. Korean is retained only where it is essential domain data (taste-word keys, Korean→component mappings, user quotes, output examples).
- **Mode 5 — visualization for feel.** When a non-designer can't judge from a text spec, render options or the result as actual HTML so they compare and pick by seeing. Two patterns: option-compare (narrow ambiguity) and before/after (confirm result). Reusable token-based HTML skeleton included.
- **Token-first color (enforced).** Every color from a defined token only (`color.primary` / `color.secondary` / `surface.app`·`base`·`raised` / `text.primary`·`secondary`·`subtle` / `border.subtle`); arbitrary hex forbidden; `color.primary` is the accent token.
- **Concrete skip clause.** Description now names precise design/system terminology (tokens, states, aria, WCAG contrast) that bypasses the skill, so it triggers only on impression-based / brand-comparative feedback.
- **Release-readiness audit applied.** Multi-dimensional audit + adversarial verification: 0 blockers; 9 fixes folded in (token-name drift resolved, before/after skeleton gap closed, README staleness fixed, "2–3 options" wording unified).
- Distributed as a `.skill` bundle and a tagged GitHub release.

## v1.1.0 — 2026-06-21 (internal)

- Added Mode 5 (visualization) and the token-first color principle, driven by real-use dogfooding (rendering HTML options let a non-designer pick a direction by seeing, which pure text specs could not).

## v1.0.0 — 2026-06-21 (internal)

- Initial skill: translates a non-designer's vague design language ("예쁘게", "깔끔하게", "애플처럼", "이 색 말고 다른 색") into an 18-section executable UI/UX request, across 5 request types and 4 output modes.
