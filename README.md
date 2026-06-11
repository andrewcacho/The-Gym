# The Gym Landing Page

A faith-based, veteran-owned gym. Static, single-page landing site built to the brand
persona (Faith · Strength · Community), ready to deploy on Netlify.

## What's inside

```
landing-page/
├── index.html          # The landing page (all sections + embedded CSS)
├── thank-you.html      # Form success page (Netlify redirects here on submit)
├── 404.html            # Branded not-found page
├── netlify.toml        # Deploy config + security headers + caching
├── robots.txt          # Crawl rules
├── sitemap.xml         # Sitemap
└── assets/
    ├── logo.svg        # The v1 badge logo (standalone, scalable)
    ├── favicon.svg     # Browser tab icon
    └── script.js       # Mobile nav + reveal-on-scroll (no external JS libs)
```

## Deploy to Netlify

**Option A: drag & drop (fastest)**
1. Go to https://app.netlify.com/drop
2. Drag the entire `landing-page` folder onto the page.
3. Done. Netlify gives you a live URL. Rename the site under Site settings if you like.

**Option B: Git (recommended for ongoing edits)**
1. Push this folder to a GitHub repo.
2. In Netlify: **Add new site → Import an existing project** → pick the repo.
3. Set **Publish directory** to `landing-page` (or the repo root if that's where these files live).
   Build command: leave blank. Click **Deploy**.

After deploy, point your custom domain under **Domain settings** and Netlify will
provision HTTPS automatically (the security headers already assume HTTPS).

## The opening-list form (Netlify Forms)

The "Join the Opening List" form uses **Netlify Forms**, no backend needed.
- Submissions appear in your Netlify dashboard under **Forms → opening-list**.
- A hidden honeypot field (`bot-field`) filters basic spam.
- On success, visitors are sent to `thank-you.html`.
- To get email notifications: **Forms → Settings → Form notifications → Add email notification**.
- Want stronger spam protection? Enable reCAPTCHA in the same settings panel.

## Security

`netlify.toml` ships hardened headers on every route:
- **Content-Security-Policy**: scripts restricted to same-origin (no inline JS);
  styles + Google Fonts allowlisted.
- **Strict-Transport-Security** (HSTS, 2-year, preload-ready)
- **X-Frame-Options: DENY** + `frame-ancestors 'none'` (no clickjacking)
- **X-Content-Type-Options: nosniff**
- **Referrer-Policy: strict-origin-when-cross-origin**
- **Permissions-Policy**: geolocation/camera/mic/payment all disabled
- `object-src 'none'`, `base-uri 'self'`

## Editing notes

- All copy and color is pulled straight from the brand persona blueprint.
  Palette lives in the `:root` CSS variables near the top of `index.html`
  (orange `#C4622C`, cream `#EFE4D0`, matte black `#0E0D0C`).
- Fonts: **Anton** (display), **Oswald** (headings/labels), **Inter** (body),
  **Caveat** (faith/script accents).
- Replace the `#` placeholders on the footer Instagram/Facebook links with the
  real profile URLs when they're live.
- Update the opening date if July 2026 firms up or shifts.
