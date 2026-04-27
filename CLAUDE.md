# CLAUDE.md — myCV_web

## Project overview
One-page personal CV / portfolio site for **Dmitry Togulev** (alias DIMBO), Senior Product Designer.
Pure HTML + CSS + minimal JS. Single file: `index.html`.

The design source is a Figma file (`user_input/Design/my CV.fig`).
The canvas is fixed at **1728px wide**; all layout coordinates are relative to that canvas.

## Stack
- HTML5, CSS (all in `<style>` inside `index.html`), minimal JS (clipboard copy, at bottom of `<body>`)
- Font: **Fixel Display** (otf, loaded from `fonts/`) — weights 400, 500, 600, 700
- No preprocessors, no bundler

## File structure
```
index.html          ← single source of truth
assets/             ← images used in the page (e.g. photo.png)
fonts/              ← Fixel Display otf files (Regular, Medium, SemiBold, Bold)
uploads/            ← scratch/staging area for extra assets (fonts, images)
user_input/         ← READ-ONLY reference files: Figma exports, raw photos, design
CLAUDE.md           ← this file
.gitignore
```

## Working rules

### `user_input/` is off-limits
- **Never reference `user_input/` in any `src`, `href`, or `url()` in the page.**
- The folder exists only as a reference drop zone for the developer.
- To use something from `user_input/`, copy it to `assets/` or `fonts/` first, then reference the copy.

### Design fidelity
- Follow the Figma design exactly unless instructed otherwise.
- Do not invent layout, spacing, or visual behaviour that is not in the design.
- When a detail is ambiguous, ask rather than guess.

### Code style
- Keep all styles in the single `<style>` block inside `index.html`.
- Preserve the existing CSS comment structure (section headers with `/* ─── … ─── */`).
- No inline `style=""` attributes except for CSS custom-property overrides (e.g. `--c`, `--r` on tiles).
- No comments explaining *what* the code does; only add a comment when the *why* is non-obvious.

### Scope discipline
- Fix only what is asked. Do not refactor surrounding code.
- Do not add features not requested.

---

## Design tokens (from Figma)
| Token | Value |
|---|---|
| Canvas width | 1728px |
| Base color | `rgb(42, 36, 40)` |
| Background | `rgb(234, 232, 234)` |
| Divider color | `rgba(42, 36, 40, 0.14)` |
| Font family | Fixel Display |
| Font weights | 400 Regular · 500 Medium · 600 SemiBold · 700 Bold |

---

## Key layout anchors
- Page container: `width: 1728px; margin: 0 auto`
- Left margin / padding: `123px`
- Grid padding: `44px`
- Headers fixed to canvas edges via `calc(50% ± 864px)`
- Section titles: `text-transform: uppercase`, `font-size: 20px`, `gap: 9px` between key/val, `margin-bottom: 71px`
- Bottom padding: `232px`

---

## Canonical UI state @ 1728px — header left

- Container: `left: calc(50% - 864px)`, `width: 587px`, `height: 143px`
- Decorative plate: `width: 780px`, `height: 160.415px`, `transform: matrix(0.979, -0.202, 0.202, 0.979, -32.434, -14.307)` — bottom-right corner intentionally clips above viewport top
- Text: `left: 44px`, `top: 42px`, `font-size: 20px`, `font-weight: 700/400`, `gap: 9px`, `text-transform: uppercase`, `letter-spacing: -0.08em`

---

## Canonical UI state @ 1728px — header right (mini → max on hover)

### Container
- Mini: `right: calc(50% - 864px + 22px)`, `top: 14px`, `width: 590px`, `height: 112px`, `border-radius: 12px`
- Max (hover): `width: 1308px`, `height: 580px`
- All transitions: `840ms cubic-bezier(0.32, 0.72, 0, 1)`

### Photo
- Mini: `left: 32px`, `top: 24px`, `width: 62px`, `height: 64px`, `border-radius: 5px`
- Max: `width: 516px`, `height: 532px`, `border-radius: 14px`

### Name + role block (single element, transitions position + font-size)
- Mini: `left: 112px` (18px from photo right edge), `top: 28px`
- Max: `left: 584px`, `top: 37px`
- Name: `font-weight: 700`, mini `26px` → max `39px`, `letter-spacing: 0.02em`
- Role: `font-weight: 400`, mini `18px` → max `23px`, `text-transform: uppercase`, `letter-spacing: -0.01em`
- Gap between name and role: `0`

### Divider (stays in place)
- `right: 210px`, `top: 24px`, `width: 1.5px`, `height: 64px`, `z-index: 10`

### Mini links (Instagram / Telegram / Resume — stays in place)
- `right: 35px`, `top: 33px`, `z-index: 10`
- Grid: `auto auto`, `column-gap: 17px`, `row-gap: 9px`
- `font-size: 14px`, `font-weight: 500`
- Hover underline: full-width 1px line, `opacity 0→0.4`, `translateY(-2px → 0)`, `200ms ease`; disappear reverses upward

### Max content (appears on hover)
- `left: 580px`, `top: 24px`, `right: 32px`, `bottom: 24px`, `padding-top: 137px`
- Appear: `opacity 480ms ease 240ms` + `translateX(120px→0) 480ms cubic-bezier 100ms delay`
- Disappear: `opacity 140ms` + `translateX(0→120px) 180ms` (fast)
- Description text: `font-weight: 500`, `font-size: 32px`, `line-height: 1.16`, `letter-spacing: -0.03em`
- Tags: `margin-top: 29px`, `font-size: 19px`, `font-weight: 400`, `letter-spacing: -0.03em`, `gap: 4px`; company names in `font-weight: 500`

---

## Canonical UI state @ 1728px — experience section

- Row padding: `26px 0`
- Grid columns: `206px` (period) + `1fr` (content)
- Period text: `font-size: 16px`, `font-weight: 400`, `color: rgb(42, 36, 40)` (no opacity), line break before em-dash
- First row has no period (intentional offset)
- Role: `font-weight: 700`, `font-size: 23px`
- Company: `font-weight: 400`, `font-size: 16px`, `color: rgb(42, 36, 40)`; company name wrapped in `<b>` with `font-weight: 500`
- Gap between role and company: `3px`
- No dividers between rows

### Row order (right side)
1. Founding Product Designer — MythHand
2. Lead Product Designer — Uzum (period: май 2024 — декабрь 2024)
3. Senior Product Designer — KazanExpress (период: май 2021 — май 2024)
4. UX Designer — Direct Line (период: февраль 2020 — апрель 2021)
5. UX/UI Designer — Invite taxi (период: сентябрь 2019 — февраль 2020)
6. Motion Designer — AIRA Lab
7. Content Designer — AdEcoSystem
8. Web Designer — Rudnik Top
9. Web Designer — TripAggregator
10. Designer — Freelance

---

## Canonical UI state @ 1728px — contact section

- Grid: `repeat(5, 1fr)`, `column-gap: 40px`, `padding-left: 123px`
- Label: `font-weight: 700`, `font-size: 23px`
- Value: `font-weight: 400`, `font-size: 16px`, `color: rgba(42, 36, 40, 0.8)`
- Gap between label and value: `3px`
- Instagram and Telegram: label is `<a>` + value is `<a>`, both `target="_blank"`
- Email: label div + value `<a>` both trigger clipboard copy via `copyEmail()`; toast notification "Почта скопирована" appears bottom-center for 2s
- 5th column intentionally empty
