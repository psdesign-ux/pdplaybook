# pdplaybook

Single-page presentation deck in Spanish: **"El futuro agéntico del product design"**.

## Repository structure

- `index.html` — production entrypoint for the presentation (Cloudflare-ready).
- `El futuro agéntico del product design.html` — original exported snapshot kept for reference.
- `El futuro agéntico del product design_files/css2` — locally saved Google Fonts stylesheet snapshot from the export.
- `_redirects` — Cloudflare Pages redirect rules so every path resolves to the presentation.
- `wrangler.toml` — minimal Wrangler config pointing to this repo root as static asset output.

## What the presentation contains

- **5 slides total** rendered in a lightweight custom deck engine.
- Navigation by:
  - on-screen next/prev controls,
  - clickable progress dots,
  - keyboard arrows,
  - mobile swipe gestures.
- Responsive behavior:
  - Desktop: animated horizontal slide transitions.
  - Mobile (`<=768px`): one-active-slide mode with vertical-friendly layout.
- Fully static implementation (HTML + CSS + vanilla JavaScript), so no build step is required.

## Deploying to Cloudflare Pages

This repository is now set up so `/` goes directly to the presentation.

### Option A (recommended): Cloudflare Pages via Git

1. Push this repo to GitHub/GitLab.
2. In Cloudflare Dashboard → **Pages** → **Create project** → connect your repo.
3. Use these settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `.`
4. Deploy.

Because `index.html` is at the repository root, the site root (`/`) loads the deck immediately.

### Option B: Wrangler CLI deploy

```bash
npm i -g wrangler
wrangler pages deploy .
```

## Routing behavior

`_redirects` contains:

```text
/* /index.html 200
```

This ensures deep links (for example `/foo`) still serve the presentation shell.
