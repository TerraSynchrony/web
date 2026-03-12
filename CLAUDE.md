# CLAUDE.md - AI Assistant Guide for TerraSynchrony Website

## Project Overview

TerraSynchrony LLC is a company specializing in geospatial digital twin solutions for land-based operations. This repository contains the **static marketing website** — a single-page site presenting the company's mission, modular platform tiers, sector specializations, client portal login, and contact form.

**Tech stack:** Static HTML5 + CSS3 with minimal inline JavaScript (no JS frameworks, no build tools, no runtime dependencies).

## Repository Structure

```
.
├── README.md           # Project documentation
├── CLAUDE.md           # This file
└── web/
    ├── index.html      # Single-page website (all sections)
    ├── css/
    │   └── styles.css  # Global stylesheet (CSS variables, grid layout, responsive)
    └── assets/
        └── hero-bg.png # Hero section background image
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
- Use semantic HTML5 elements: `<nav>`, `<header>`, `<main>`, `<section>`, `<footer>`
- Include descriptive HTML comments before each major section
- Forms must have proper `<label>` elements with `for` attributes matching input `id`s
- New sections should follow the established pattern: `<section id="name" class="name">`

## Deployment

The site is hosted via **GitHub Pages**, configured to serve from the `main` branch at `/ (root)`. You must first enable GitHub Pages in the repository settings (select `main` as the source and `/ (root)` as the folder) as described in `README.md`. After GitHub Pages is configured, pushes to `main` will deploy the site automatically; there is no separate CI/CD pipeline or build step.

## Testing

No automated tests exist. Verify changes by:
1. Opening `index.html` in a browser (or local HTTP server)
2. Checking all navigation anchor links scroll to correct sections
3. Testing responsive layout at mobile (`< 768px`) and desktop widths
4. Validating forms display and submit handlers fire correctly

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
