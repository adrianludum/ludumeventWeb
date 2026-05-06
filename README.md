# ludumevents.com — marketing site

The public marketing landing page for Ludum Events. Single static HTML file,
self-contained CSS, no build step.

## Files

- `index.html` — the landing page
- `assets/logo.jpg` — the brand mark (raster, kept for off-web use)
- `assets/coach-app.png` — **(add this)** screenshot of the coach app, used inside the iPhone frame on the page. Until this file exists, the device shows a blue placeholder with a hint. Drag any iPhone screenshot into `assets/` and rename it to `coach-app.png`.

## Local preview

Open `index.html` in any browser, or:

```bash
python3 -m http.server 4000
# http://localhost:4000
```

## CTAs

All "Create event" / "Sign in" links point at the app subdomain:

- `https://app.ludumevents.com/get-started`
- `https://app.ludumevents.com/auth/login`

If the app moves, find-and-replace those two URLs.

## Deploying

Drop the folder on any static host. Recommended: a separate Vercel project.

1. New Vercel project → import this folder (or its own GitHub repo).
2. Framework preset: **Other** (no build command, output directory `.`).
3. Domains: add `ludumevents.com` and `www.ludumevents.com`.
4. At the registrar: A record for the apex pointing at Vercel's IP, CNAME for
   `www` pointing at `cname.vercel-dns.com`.

The Next.js app stays on its own Vercel project at `app.ludumevents.com`.

## Editing copy

The page is one file — just open `index.html` and edit the text. Sections are
clearly commented (`<!-- ──── HERO ──── -->` etc.). External dependencies are
Google Fonts only.
