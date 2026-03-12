# TerraSynchrony Website

This repository contains the source code for the **TerraSynchrony LLC** static website.  
The site introduces TerraSynchrony’s mission, modular platform tiers, sector specialities, a client portal login prompt, and a contact form.  
Its clean layout and earth‑toned styling align with the company’s branding.

## Project structure

The repository uses a simple, flat directory structure that works seamlessly on GitHub Pages and other static site hosts:

| Path | Description |
|---|---|
| `index.html` | Main landing page of the website with SEO, accessibility, and social sharing meta tags. |
| `404.html` | Custom error page for handling 404 errors. |
| `css/styles.css` | Global stylesheet providing the colour palette, layout and responsive design. |
| `assets/hero-bg.png` | Abstract earth‑tone background image used in the hero section. |
| `assets/favicon.svg` | Website favicon (browser tab icon). |
| `manifest.json` | Progressive Web App manifest for mobile support. |
| `robots.txt` | Search engine crawler directives. |
| `sitemap.xml` | XML sitemap for improved SEO. |
| `.gitignore` | Git ignore file for excluding temporary and build files. |

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
## Production Readiness

This website is production-ready with the following features:

- **SEO Optimization**: Meta descriptions, keywords, and structured headings for search engines
- **Social Sharing**: Open Graph and Twitter Card meta tags for rich previews on social media
- **Accessibility**: ARIA labels, semantic HTML, skip-to-content link for keyboard navigation
- **Security**: Security-related meta headers (X-Content-Type-Options, X-Frame-Options, Referrer-Policy)
- **PWA Support**: Manifest file for progressive web app functionality on mobile devices
- **Error Handling**: Custom 404 page for better user experience
- **Mobile Responsive**: Fully responsive design that works on all device sizes
- **Form Feedback**: User-friendly form submission messages (note: forms require backend integration for actual email delivery)

## Important Notes for Deployment

1. **Update URLs**: If deploying to a custom domain, update the URLs in:
   - `index.html` (Open Graph and Twitter meta tags)
   - `robots.txt` (sitemap location)
   - `sitemap.xml` (all URL locations)

2. **Forms**: The contact and portal login forms currently show success messages but do not send emails. To enable email functionality:
   - Integrate with a form service (e.g., Formspree, Netlify Forms, or custom backend)
   - Replace the JavaScript form handlers in `index.html` with your service endpoint

3. **Analytics**: Consider adding analytics (e.g., Google Analytics, Plausible) to track visitor engagement

4. **Content Security**: Review and update the security meta headers based on your specific deployment requirements
