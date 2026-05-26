# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Active Files

- **`index.html`** — Main portfolio. Single file, all CSS/JS inline. Deploys to GitHub Pages.
- **`archive.html`** — Project archive page (`/archive`). Still uses the old dark amber theme — do not apply the new design system to it without being asked.

Legacy (do not edit): `index.old.html`, `v2.html`, `v3.html`, `v4.html`, `assets/css/`, `assets/js/`, `assets/sass/`, `images/`, `fonts/`.

## Local Dev

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

Hard-refresh (Cmd+Shift+R) after edits — browser caches CSS aggressively.

## Deploy

```bash
git add index.html archive.html
git commit -m "..."
git push origin main
```

GitHub Actions (`.github/workflows/jekyll-gh-pages.yml`) auto-deploys on push to `main`.

Live: https://charanteja25.github.io/Portfolio/

## Design System

Editorial / newspaper-inspired light theme. All tokens at top of `index.html` `<style>` block:

```css
--bg:      #F7F6F3   /* warm off-white page background */
--paper:   #FDFCFA   /* card / surface background */
--ink:     #1C2B3A   /* primary text — NOT pure black */
--ink-mid: #3D5166   /* body text */
--ink-lt:  #6B7E90   /* secondary / meta text */
--rule:    #C8D3DC   /* borders, dividers */
--rule-lt: #DDE5EB   /* lighter dividers */
--acc:     #4338ca   /* deep indigo — the ONLY accent color, 10% usage max */
```

Fonts: **Playfair Display** (headings, serif, editorial weight) + **IBM Plex Sans** (body, weight 300–500) + **IBM Plex Mono** (labels, tags, meta) via Google Fonts.

### 60-30-10 Rule
- **60%** `--bg` / `--paper` — backgrounds
- **30%** `--ink` / `--ink-mid` / `--rule` — text and structure
- **10%** `--acc` — strictly: key links, hover underlines, metric numbers, CTA button fill

Never use `--acc` for decorative purposes or section labels. Never use pure `#000` or `#fff` for text.

## Layout Patterns

`index.html` uses a strict editorial grid. Key structural patterns:

- **Masthead** — newspaper-style. `mast-top` metadata strip (3px rule above, 1px below), giant `mast-name` in Playfair Display, `mast-rule` `<hr>` below name (separate element — do not put `border-bottom` on the name itself, descenders will clip), `mast-sub` two-column strip with descriptor + CTAs.
- **Section headers** — `.sec-head` grid (180px label col + 1fr title col), bordered top and bottom. `.sec-tag` is the mono label, `.sec-title` is the serif heading.
- **Projects** — `.bento` grid using `gap:1px; background:var(--rule)` as the border system (not individual card borders). Cells: `.bc-feat` (7col), `.bc-sm` (5col), `.bc-third` (4col).
- **Experience** — `<table class="exp-table">` on desktop, `.exp-card` flex stack on mobile (table hides via `display:none` at 960px breakpoint, cards show via `display:flex`).
- **Skills** — plain text rows, no icons. `.sk-row` grid (180px cat + 1fr items).
- **Writing** — numbered list `.w-item` with arrow that appears on hover only.

## JS

Minimal. Three systems only:

1. **Nav shadow** — adds `box-shadow` on scroll past 40px.
2. **Hamburger menu** — `#burger` toggles `.open` on `#drawer`. Drawer closes on outside click and on nav link tap (`closeMenu()`).
3. **Ink blob** — on `click` and `touchstart`, spawns an indigo circle that scales and fades via `@keyframes inkSpread`. Works on both mouse and touch.

No scroll reveal, no stat counters, no role cycling. The theme is intentionally static.

## Content Rules

- **OctoNexus Power** — founding team, path to CTO. Frame forward-looking and leadership-oriented.
- **Fennex award** — the *company* Fennex won the Digital Innovation Award. Phrase as "Part of the team recognised with a Digital Innovation Award." Never attribute it personally to Charan.
- **Aamrutham** — live agri e-commerce, actively trading this mango season. Co-Founder + Tech Lead.
- **Skills** — text only, no icons. The icon grid was deliberately removed; do not add it back.
- **No sponsorship wording** anywhere on the site.
- **No GitHub contribution calendar** — removed deliberately (sparse activity hurts senior profile optics).

## Assets

- `assets/Charan_Gunisetty_DataScientist_CV.pdf` — linked from "Download CV" button.
- `profile.jpg` (root) — headshot, not currently used. Needs background removal before enabling.
