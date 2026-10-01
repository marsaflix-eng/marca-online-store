# REPORT — Marça Snap Store

**Date:** 2026-10-01 (Europe/Paris)  
**Path:** `/workspace/marça-snap-store/`  
**Deploy zip:** `/workspace/marça-snap-store-deploy.zip`

## File list

| Path | Role |
|------|------|
| `index.html` | RTL Arabic SPA shell (plans → WhatsApp) |
| `css/styles.css` | Dark elegant mobile-first UI |
| `js/config.js` | Live config: WhatsApp, Snap URL, products, store name |
| `js/config.json` | Same config as JSON reference (keep in sync) |
| `js/app.js` | Checkout logic, validation, WhatsApp URL builder |
| `.htaccess` | HTTPS redirect, deny sensitive files, security headers |
| `robots.txt` | Allow all crawlers |
| `README.md` | Deploy guide AR + EN |
| `REPORT.md` | This file |

## How the flow works

1. **Landing** — Hero + three plan cards (3m / 170 MRU, 6m / 330 MRU, 1y / 630 MRU).
2. **Username** — Strip `@`; validate 3–15 chars `[A-Za-z0-9._-]`; reject empty / XSS-like chars; show errors via `textContent`.
3. **Follow Snap** — Button opens `SNAP_FOLLOW_URL` (`https://snapchat.com/t/7BEXzDEV`) in a new tab; checkbox «تابعت حسابك» required before continue.
4. **Payment policy** — States Bankily-only; no Gimtel; no third-party. Checkbox agreement required.
5. **WhatsApp** — Builds `https://wa.me/22248650585?text=` + `encodeURIComponent(Arabic message)` including plan, price MRU, Snap username, follow confirm, Bankily confirm. Opens in new tab. No cards / no on-site payment.

Steps use CSS panel swaps (no full reloads) with a progress indicator.

## Security measures («محصن»)

- Static-only for Hostinger `public_html`; no server-side payment code.
- External JS/CSS only (`script-src 'self'`; `style-src 'self'`); no remote CDNs; no `eval`.
- CSP: `default-src 'self'`; `img-src 'self' data:`; `form-action` allows `wa.me` / `api.whatsapp.com`; `frame-ancestors 'none'`; `object-src 'none'`.
- Headers: `X-Content-Type-Options nosniff`, `X-Frame-Options DENY`, `Referrer-Policy no-referrer`, restrictive `Permissions-Policy`, HSTS max-age=31536000; includeSubDomains.
- `.htaccess`: force HTTPS, `-Indexes`, deny dotfiles and common secret/backup extensions; block serving `README.md` / `REPORT.md` / lockfiles.
- User input never assigned with `innerHTML`; WhatsApp query uses `encodeURIComponent`.
- No secrets in repo; privacy note on payment step.

## What remains (for the owner)

1. **Domain linking** — Point A/CNAME to Hostinger; enable SSL; optional `DOMAIN_PLACEHOLDER` in config.
2. **Upload** — Extract zip into `public_html`.
3. **Smoke-test** on live HTTPS: plan → username → follow → agree → WhatsApp message correctness.
4. Optionally sync product prices later in `js/config.js` (+ `config.json`).

## WhatsApp link contract

- E.164 digits: `22248650585`
- Base: `https://wa.me/22248650585?text=<urlencoded>`
- Message includes: store name مرصة, plan AR/EN, price with أوقية (MRU), `@username`, follow ✓, Bankily-only ✓.
