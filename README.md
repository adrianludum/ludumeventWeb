# ludumevents.com — marketing site

The public marketing landing page for Ludum Events. Single static HTML
file, self-contained CSS, no build step. Lives at
[ludumevents.com](https://ludumevents.com); the app itself lives on the
`app.` subdomain.

## Files

- `index.html` — the landing page
- `assets/logo-mark.png` — brand mark (transparent PNG, used in nav and footer)
- `assets/logo.jpg` — original full Ludum logo (with wordmark, kept for off-web use)
- `assets/coach-app.png` — iPhone screenshot used in the Coach persona panel
- `.do/app.yaml` — Digital Ocean App Platform deployment spec

Cleanup candidates (safe to delete): `assets/coach-app2.PNG`,
`assets/logo-icon.png` — leftovers from earlier iterations.

## Local preview

Open `index.html` in any browser, or:

```bash
python3 -m http.server 4000
# http://localhost:4000
```

## Outbound links

- "Get set up" CTAs → `mailto:adrian@ludum.com` with subject prefilled
- "Talk to us first" → Calendly: `https://calendly.com/adrian-cassidy/demo`
- "Sign in" → currently `app.ludumevents.com/auth/login` (placeholder until
  the app subdomain is pointed at the Vercel deployment)

If the app moves, find-and-replace those URLs in `index.html`.

## Deploying to Digital Ocean App Platform

The repo is set up to auto-deploy via `.do/app.yaml`.

### First-time setup

1. Push this repo to GitHub: `adrianludum/ludumeventWeb`.
2. Digital Ocean → **Create → Apps → GitHub** → pick the repo.
3. DO will detect `.do/app.yaml` and pre-fill the static-site config.
   Confirm: build command empty, output directory `/`, index document
   `index.html`. Free tier is sufficient.
4. **Create Resources** — first deploy takes ~60 seconds. Site goes
   live at a temporary `ludumevents-xxx.ondigitalocean.app` URL.

### Custom domain

After the first deploy:

1. **App → Settings → Domains → Add Domain**:
   - `ludumevents.com` (PRIMARY)
   - `www.ludumevents.com` (ALIAS, will redirect to apex)
2. DO will display the DNS records to add at your registrar.
   For an external registrar (Namecheap, GoDaddy, etc.) you'll get
   either A records or CNAMEs to add.
3. Wait for DNS propagation (5–30 min), at which point DO auto-issues a
   Let's Encrypt certificate.

### DNS note

The `app.ludumevents.com` subdomain is independent — it points at Vercel
where the actual Ludum app lives. Adding `ludumevents.com` and
`www.ludumevents.com` to DO does not affect it. Just don't touch the
`app` record.

### Subsequent deploys

Push to `main`. DO rebuilds and deploys automatically (`deploy_on_push:
true` in `.do/app.yaml`). Each deploy takes about a minute.

## Editing copy

The page is one file — open `index.html` and edit text. Sections are
clearly commented (`<!-- ──── HERO ──── -->`, etc.). External
dependencies are Google Fonts only.

A commented-out **testimonial slot** sits just before the final CTA
section. Uncomment it after 26 May 2026 once the NSR director's quote
lands, and drop the quote in.
