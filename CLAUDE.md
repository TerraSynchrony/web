# CLAUDE.md - AI Assistant Guide for TerraSynchrony Website

## Project Overview

TerraSynchrony LLC marketing website — a static, single-page site presenting the company's geospatial digital twin platform, service tiers, sector specialties, client portal login, and contact form. Built with pure HTML, CSS, and vanilla JavaScript. No build tools, frameworks, or runtime dependencies.

## Repository Structure

```
web/
├── index.html          # Single-page site with anchor-linked sections
├── css/
│   └── styles.css      # All styles; CSS variables for theming at :root
├── assets/
│   └── hero-bg.png     # Hero background image (~2.7 MB)
├── README.md           # Project overview and deployment guide
└── CLAUDE.md           # This file
```

## Technology Stack

- **HTML5** — Semantic sections with anchor navigation
- **CSS3** — CSS Grid, Flexbox, CSS custom properties (variables), media queries
- **Vanilla JavaScript** — Inline `onsubmit` handlers only (no external JS files)
- **Google Fonts (CDN)** — Inter (body text) and Lora (headings/brand)
- **No build system** — No package.json, no bundler, no transpilation

## Page Sections (index.html)

| Section ID   | Purpose                                      |
|-------------|----------------------------------------------|
| `#home`     | Hero with background image and CTA           |
| `#about`    | Company mission and problem statement         |
| `#services` | Six modular platform tiers (card grid)        |
| `#sectors`  | Five industry verticals (card grid)           |
| `#portal`   | Client login form (placeholder functionality) |
| `#contact`  | Contact form and email link                   |

## CSS Theming

All colours are defined as CSS custom properties in `css/styles.css` at `:root`:

| Variable      | Value     | Usage                     |
|--------------|-----------|---------------------------|
| `--primary`  | `#0f4c5c` | Deep teal — headings, nav |
| `--secondary`| `#2f8f4e` | Forest green — buttons, card titles |
| `--accent`   | `#a67c52` | Warm brown — hover states  |
| `--light`    | `#f7f6f2` | Light beige — page background |
| `--dark`     | `#1b1b1b` | Near black — footer, emphasis |
| `--text`     | `#333333` | Body text colour           |

When modifying colours, always update the CSS variable rather than hardcoding values.

## Development Workflow

### Running locally

No install or build step required:
```bash
open index.html   # macOS
xdg-open index.html  # Linux
```

Or use any local HTTP server (e.g., `python3 -m http.server 8000`).

### Deployment

The site is designed for **GitHub Pages**. Push to the `main` branch and enable Pages in repository settings pointing to `/ (root)`.

## Key Conventions

### HTML
- Use semantic HTML elements and descriptive comments before each section
- All sections live inside `<main>` except the nav and hero `<header>`
- Forms use inline `onsubmit="event.preventDefault(); alert('...');"` as placeholders
- Navigation uses anchor links (`#about`, `#services`, etc.) for single-page scrolling

### CSS
- Use CSS custom properties (`var(--primary)`, etc.) for all colours — never hardcode colour values
- Card layouts use `display: grid` with `repeat(auto-fit, minmax(250px, 1fr))` for responsive grids
- Navigation is `position: fixed` with semi-transparent background (`rgba(0, 0, 0, 0.5)`)
- Fonts: `'Lora', serif` for headings/brand, `'Inter', sans-serif` for body
- Responsive breakpoint at `768px` for mobile typography adjustments
- The `.cta-btn` class is shared across all call-to-action buttons (links and submit buttons)

### Assets
- Place images and static files in `assets/`
- Place stylesheets in `css/`
- Reference assets from CSS using relative paths from `css/` (e.g., `url('../assets/hero-bg.png')`)

### JavaScript
- Minimal JS only — no external scripts, no libraries
- Form handlers are placeholders; actual backend integration is not yet implemented

## Common Tasks

### Adding a new page section
1. Add a new `<section id="section-name">` inside `<main>` in `index.html`
2. Add a nav link `<li><a href="#section-name">Label</a></li>` to `.nav-links`
3. Add corresponding styles in `css/styles.css`

### Adding a new service or sector card
Add a `<div class="card">` (or `<div class="card sector-card">` for sectors) inside the relevant `.cards` container. The grid layout will automatically accommodate it.

### Changing the colour scheme
Update the CSS variables in `:root` at the top of `css/styles.css`. All components reference these variables, so changes propagate site-wide.

## Things to Watch Out For

- **No build/lint/test tooling** — validate HTML and CSS manually or with browser dev tools
- **Large hero image** — `assets/hero-bg.png` is ~2.7 MB; consider optimizing if performance is a concern
- **Forms are non-functional** — both the portal login and contact form use `event.preventDefault()` with alert placeholders
- **No `.gitignore`** — be careful not to commit editor configs, OS files, or other unintended artifacts
- **Fixed nav overlaps content** — the hero section accounts for this, but new top-level content needs appropriate top padding/margin
