# CLAUDE.md

This file provides guidance for AI assistants working with the TerraSynchrony website repository.

## Project Overview

TerraSynchrony LLC is a company specializing in geospatial digital twin solutions for land-based operations. This repository contains the **static marketing website** — a single-page site presenting the company's mission, modular platform tiers, sector specializations, client portal login, and contact form.

**Tech stack:** Pure HTML5 + CSS3. No JavaScript frameworks, no build tools, no runtime dependencies.

## Repository Structure

```
web/
├── index.html          # Single-page website (all sections)
├── css/
│   └── styles.css      # Global stylesheet (CSS variables, grid layout, responsive)
├── assets/
│   └── hero-bg.png     # Hero section background image
├── README.md           # Project documentation
└── CLAUDE.md           # This file
```

## Development Setup

No build step required. To preview locally:

```bash
# Any static HTTP server works, e.g.:
python -m http.server 8000
# Then open http://localhost:8000
```

Or simply open `index.html` directly in a browser.

## Architecture & Key Patterns

### Single-Page Layout

`index.html` is organized into anchor-linked sections: `#home`, `#about`, `#services`, `#sectors`, `#portal`, `#contact`. Navigation uses a fixed top bar with smooth scrolling (`scroll-behavior: smooth`).

### CSS Design System

All theming is controlled via CSS custom properties in `:root` (`css/styles.css:10-17`):

| Variable | Value | Purpose |
|---|---|---|
| `--primary` | `#0f4c5c` | Deep teal — headings, labels, footer background |
| `--secondary` | `#2f8f4e` | Forest green — card headings, CTA buttons |
| `--accent` | `#a67c52` | Warm brown — hover states |
| `--light` | `#f7f6f2` | Light beige — page background |
| `--dark` | `#1b1b1b` | Near black (unused currently) |
| `--text` | `#333333` | Body text |

### Typography

- **Headings:** Lora (serif) via Google Fonts
- **Body:** Inter (sans-serif) via Google Fonts
- Both loaded from `fonts.googleapis.com` in `index.html:14`

### Responsive Layout

- Card grids use `grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))` for automatic responsive columns
- Media query at `768px` reduces hero heading and paragraph font sizes
- Navigation is fixed at `z-index: 1000` with semi-transparent background

### Forms

Two forms exist with **placeholder JavaScript** (inline `onsubmit` handlers that show `alert()` messages):
- **Client Portal** (`#portal`) — login form, currently shows "Portal functionality coming soon!"
- **Contact** (`#contact`) — contact form, currently shows "Thank you for reaching out!"

These are stubs. No backend integration exists yet.

## Conventions to Follow

### File Organization
- Keep the flat directory structure: HTML at root, styles in `css/`, media in `assets/`
- Use a single CSS file unless the stylesheet grows significantly
- Use relative paths from the CSS directory for asset references (e.g., `../assets/hero-bg.png`)

### Naming
- CSS classes: **kebab-case** (e.g., `.hero-content`, `.cta-btn`, `.nav-links`, `.form-row`)
- HTML section IDs: lowercase single words matching navigation anchors (e.g., `id="services"`)
- CSS variables: `--` prefix with short descriptive names (e.g., `--primary`, `--accent`)

### Styling
- Use CSS custom properties for colors — never hardcode color values in component rules
- Exception: `#fff`, `#ccc`, and `rgba()` values for whites, borders, and transparency are used inline
- Card components use `.card` base class; sector-specific cards add `.sector-card`
- CTA buttons use the shared `.cta-btn` class
- Transitions: `0.2s ease` for subtle interactions, `0.3s ease` for buttons

### HTML
- Use semantic HTML5 elements: `<nav>`, `<header>`, `<main>`, `<section>`, `<footer>`
- Include descriptive HTML comments before each major section
- Forms must have proper `<label>` elements with `for` attributes matching input `id`s
- New sections should follow the established pattern: `<section id="name" class="name">`

## Deployment

The site deploys via **GitHub Pages** from the `main` branch at `/ (root)`. No CI/CD pipeline or build step is involved — pushing to `main` triggers deployment automatically.

## Testing

No automated tests exist. Verify changes by:
1. Opening `index.html` in a browser (or local HTTP server)
2. Checking all navigation anchor links scroll to correct sections
3. Testing responsive layout at mobile (`< 768px`) and desktop widths
4. Validating forms display and submit handlers fire correctly

## Common Tasks

### Adding a new section
1. Add a `<section id="new-id" class="new-id">` block in `index.html` inside `<main>`
2. Add a nav link `<li><a href="#new-id">Label</a></li>` in the `<ul class="nav-links">`
3. Add corresponding styles in `css/styles.css`

### Adding a new service/sector card
Add a `<div class="card">` (or `<div class="card sector-card">`) inside the appropriate `.cards` grid container. The auto-fit grid will accommodate it automatically.

### Changing the color theme
Update the CSS custom properties in `:root` at the top of `css/styles.css`. All derived styles reference these variables.
