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

## Deploy to Cloudflare Pages (Git)

1. Push this repo to GitHub (already set up).
2. In the Cloudflare dashboard: **Workers & Pages -> Create -> Pages -> Connect to Git**.
3. Pick this repository. Build settings:
   - **Framework preset:** None
   - **Build command:** leave blank
   - **Build output directory:** `/` (the repo root is the site)
4. Click **Save and Deploy**. You get a `*.pages.dev` URL.
5. **Custom domain:** Pages project -> **Custom domains -> Set up a domain** -> enter your
   domain. Cloudflare adds the DNS record and provisions HTTPS automatically.

From then on: edit -> commit -> push, and Cloudflare auto-deploys. `_headers` applies the
security + cache rules (Cloudflare reads it natively; `netlify.toml` is ignored here and
kept only as a Netlify fallback).

## The opening-list form (Web3Forms)

The form posts to **Web3Forms** (host-agnostic, free, ~250 submissions/month), so it works
on Cloudflare, Netlify, or anywhere.
- Get a free access key at https://web3forms.com (enter the destination email; the key is
  emailed to you instantly, no account required).
- In `index.html`, replace `YOUR_WEB3FORMS_ACCESS_KEY` with that key.
- Replace `REPLACE-WITH-YOUR-DOMAIN` in the form's `redirect` field with your live domain so
  successful submissions land on `thank-you.html`.
- Spam is filtered by the hidden `botcheck` honeypot.
- Submissions are emailed to the address tied to your access key (currently intended for
  thegymsfc.tx@gmail.com).

## Security

`_headers` ships hardened headers on every route (Cloudflare Pages reads this file; `netlify.toml` mirrors it for Netlify):
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
