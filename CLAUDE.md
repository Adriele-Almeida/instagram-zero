# CLAUDE.md — AI Assistant Guide for instagram-zero

## Project Overview

**instagram-zero** is a Brazilian Portuguese landing page / sales funnel for an online course titled _"Instagram do Zero"_ ("Instagram From Zero"). The course teaches elderly or non-tech-savvy users how to use Instagram from the ground up.

- **Language**: Brazilian Portuguese (`pt-BR`)
- **Type**: Static single-page application (no backend, no JavaScript, no build step)
- **Stack**: Pure HTML5 + CSS3 (embedded in a single file)
- **Entry point**: `index.html` (946 lines, the entire codebase)

---

## Repository Structure

```
instagram-zero/
├── index.html       # The entire application — HTML + embedded CSS
└── CLAUDE.md        # This file
```

External image assets are **not tracked in git**. The following files are referenced in `index.html` and must be placed alongside it when serving:

| File | Usage |
|---|---|
| `topo.png` | Header logo / hero banner |
| `imagem-1.png` … `imagem-9.png` | Pain-point and benefit illustrations |
| `rodape.png` | Footer logo |

---

## Technology Stack

| Concern | Solution |
|---|---|
| Markup | HTML5 (semantic elements) |
| Styling | CSS3 — fully embedded inside `<style>` in `index.html` |
| Fonts | Google Fonts: **Orbitron** (headings) + **Rajdhani** (body) |
| JavaScript | **None** — the page is fully static |
| Build tooling | **None** — open `index.html` directly in a browser |
| Package manager | **None** |
| Testing | **None** |
| CI/CD | **None** |

---

## Design System

### Color Palette (CSS Custom Properties)

All colors are declared as CSS variables on `:root` (line 17):

```css
--bg-deep:   #060c1a          /* Deepest background */
--bg-mid:    #0a1628          /* Mid-level background */
--bg-card:   #0f1e35          /* Card / component background */
--neon:      #00d9ff          /* Primary cyan neon accent */
--neon-dim:  rgba(0,217,255,0.15)
--neon-glow: rgba(0,217,255,0.35)
--accent:    #3a86ff          /* Blue accent */
--success:   #00e5b0          /* Green (success / checkmarks) */
--warn:      #ffc340          /* Yellow (warnings / highlights) */
--text:      #e0e9f5          /* Primary text color */
--muted:     #6b85a8          /* Secondary / muted text */
--border:    rgba(0,217,255,0.12)  /* Subtle card borders */
```

**Always use these variables** — never hard-code hex values. This maintains the cyberpunk / futuristic dark-mode aesthetic consistently.

### Typography

- **Headings**: `Orbitron` — weights 400, 600, 700, 800. Use for section titles and prominent labels.
- **Body**: `Rajdhani` — weights 300, 400, 500, 600, 700. Use for all body copy, cards, and descriptions.

---

## Page Structure & Sections

Sections are separated by ASCII-art comments inside the CSS (e.g., `/* ─── HERO ─── */`). The HTML follows this order:

| # | Section | HTML anchor / class | Description |
|---|---|---|---|
| 1 | Hero | `.hero` | Full-viewport intro with CTA button → `#inscricao` |
| 2 | Pain Points | `.pain-section` | Problem cards (`pain-card`) with icons |
| 3 | Benefits | `.benefits-section` | Solution cards (`benefit-card`) |
| 4 | Curriculum | `.curriculum-section` | 10 course modules (`module-header`, `module-item`) |
| 5 | Transformation | `.transformation-section` | Before / after comparison |
| 6 | Guarantee | `.guarantee-section` | 7-day money-back guarantee |
| 7 | Bonuses | `.bonus-section` | Bonus materials |
| 8 | Inscription / Pricing | `#inscricao` | Final CTA with pricing (R$ 19,90) |
| 9 | Footer | `footer` | Contact & branding (`rodape.png`) |

---

## CSS Conventions

1. **Section delimiters**: Use `/* ─── SECTION NAME ─── */` comments to mark each major section inside `<style>`.
2. **Naming**: BEM-inspired flat class names — e.g., `pain-card`, `benefit-card`, `module-header`, `cta-primary`, `cta-final-button`.
3. **Layout**: Flexbox throughout. No CSS Grid.
4. **Responsive**: Mobile-first. Media queries adjust font sizes, padding, and column counts for larger screens.
5. **Animations**: CSS keyframe animations for glow/pulse effects (e.g., neon borders).
6. **No external CSS files** — all styles live in the embedded `<style>` block.

---

## Content & Copywriting Conventions

- All text is in **Brazilian Portuguese**.
- Price references use the **R$ (BRL)** currency format (e.g., `R$ 19,90`, `R$ 97,00`).
- Installment format: `4x de R$ 5,42 sem juros`.
- The tone is warm, encouraging, and accessible — targeting users unfamiliar with technology.
- Contact email: `arteadrielealmeida@gmail.com`

---

## Development Workflow

### Editing the Page

Since there is no build step, editing is straightforward:

1. Open `index.html` in any text editor.
2. Make changes to HTML or the embedded CSS.
3. Refresh the browser to see results.

### Serving Locally

```bash
# Python 3
python3 -m http.server 8080

# Node.js (npx)
npx serve .
```

Then open `http://localhost:8080` in a browser.

### Git Workflow

```bash
# Work on the designated feature branch
git checkout claude/claude-md-mm2r7nvxr7d9at3v-4qjRR

# Stage changes
git add index.html CLAUDE.md

# Commit with a clear message
git commit -m "feat: describe what changed"

# Push
git push -u origin claude/claude-md-mm2r7nvxr7d9at3v-4qjRR
```

---

## Key Constraints & Rules for AI Assistants

1. **Single-file discipline** — Do not split CSS or content into separate files unless explicitly asked. Keeping everything in `index.html` is intentional for simplicity of deployment.
2. **No JavaScript** — Do not add `<script>` tags or external JS libraries without explicit user approval.
3. **Preserve the design system** — Always use CSS custom properties (`var(--neon)`, etc.); never hard-code colors.
4. **Language** — All user-facing text must remain in Brazilian Portuguese (`pt-BR`).
5. **No build tools** — Do not introduce npm, bundlers, or transpilers unless the user explicitly requests a migration.
6. **Images** — Image filenames (`topo.png`, `imagem-N.png`, `rodape.png`) are fixed; do not rename or add new image references without updating the asset list in this file.
7. **Pricing accuracy** — If modifying pricing text, ensure installment math is consistent (e.g., total / number of installments).
8. **No testing infrastructure** — There are currently no tests. Do not add a test framework unless explicitly asked.

---

## Business Context

| Field | Value |
|---|---|
| Course name | Instagram do Zero |
| Target audience | Elderly / non-tech-savvy Brazilians |
| Price | R$ 19,90 (or 4x R$ 5,42) |
| Original price (crossed out) | R$ 97,00 |
| Guarantee | 7-day money-back |
| Creator | Adriele Almeida (`arteadrielealmeida@gmail.com`) |
| Curriculum | 10 modules covering Instagram basics |
