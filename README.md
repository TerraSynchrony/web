# TerraSynchrony Website

This repository contains the source code for the **TerraSynchrony LLC** static website.  
The site introduces TerraSynchrony’s mission, modular platform tiers, sector specialities, a client portal login prompt, and a contact form.  
Its clean layout and earth‑toned styling align with the company’s branding.

## Project structure

The repository uses a simple, flat directory structure that works seamlessly on GitHub Pages and other static site hosts:

| Path | Description |
|---|---|
| `index.html` | Main landing page of the website. |
| `css/styles.css` | Global stylesheet providing the colour palette, layout and responsive design. |
| `assets/hero-bg.png` | Abstract earth‑tone background image used in the hero section. |
| `assets/` | Folder for images and other static assets. |
| `css/` | Folder for CSS stylesheets. |

## Usage

No build step or runtime dependencies are required.  Clone or download the repository and open `index.html` in a web browser to view the site:

```bash
git clone <repository-url>
cd <repository-name>
open index.html  # or double‑click the file in your file manager
```

## Deployment

To publish the site on GitHub Pages:

1. Push this repository to GitHub.
2. Go to your repository **Settings** → **Pages**.
3. Under “Source,” select the `main` branch and, if available, the `/ (root)` folder.
4. Save the settings.  GitHub will deploy your site at `https://<your‑username>.github.io/<repository‑name>/`.

For changes, edit the HTML and CSS files.  Feel free to add new assets to the `assets` folder or additional stylesheets to the `css` folder as your project evolves.