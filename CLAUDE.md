# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Aurelia Craft is a static e-commerce website for women's traditional clothing (three-piece sets and sarees) targeting Bangladesh. All content is in Bengali. The site uses WhatsApp for order processing — there is no cart or payment gateway.

**Live site:** https://faisalnabil.github.io/aurelia-craft/

## Commands

```bash
npm run dev       # Start Astro dev server
npm run build     # Production build to dist/
npm run preview   # Preview production build locally
```

There are no tests or linting configured.

## Architecture

**Framework:** Astro 4.x (static site generation, no client-side framework)

### Key Files

- `src/data/products.js` — Single source of truth for all product data, categories, and WhatsApp contact number. Products are plain JS objects with slug, name, price, image, fabric, design, occasion, description, details array, and related slugs.
- `src/layouts/Base.astro` — Shared layout with fixed navbar, footer, meta tags (OG/Twitter), and scroll-reveal IntersectionObserver script.
- `src/pages/index.astro` — Homepage with hero, product catalog, and order form. The order form uses vanilla JS to encode form data into a WhatsApp message URL.
- `src/pages/products/[slug].astro` — Dynamic product detail pages using `getStaticPaths()` from the products data.
- `src/components/ProductCard.astro` — Reusable product card with image, badge, price, and order link.
- `src/styles/global.css` — Design tokens as CSS custom properties (colors, fonts, spacing).
- `astro.config.mjs` — Configured with `base: '/aurelia-craft'` for GitHub Pages and `output: 'static'`.

### URL/Asset Paths

All internal links and asset references must use the `/aurelia-craft/` base path prefix (configured in `astro.config.mjs`). Product images live in `public/images/` and are referenced by filename in `products.js`.

### Design System

- **Colors:** `--cream` (#F7F3ED), `--dark` (#1C1510), `--brown` (#6B4C2A), `--gold` (#C4A265), `--warm` (#9B7A52)
- **Fonts:** Hind Siliguri (body/Bengali text), Cormorant Garamond (display headings) — loaded from Google Fonts
- **Styling:** Scoped CSS within `.astro` components + global CSS variables. No Tailwind or CSS framework.

### Adding Products

Add a new object to the `products` array in `src/data/products.js` following the existing schema. Place the product image in `public/images/`. The product page is auto-generated via the dynamic `[slug].astro` route.

## Deployment

Automated via GitHub Actions (`.github/workflows/deploy.yml`). Every push to `main` triggers: `npm ci` → `npm run build` → deploy `dist/` to GitHub Pages. Uses Node.js 20.
