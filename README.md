# Marça (مرصة) — Snapchat+ store

**Source of truth** for the static storefront (also synced to the user Pages site).

## Live URLs

| URL | Notes |
|-----|--------|
| https://marsaflix-eng.github.io/ | User Pages (redirects to custom domain once DNS is set) |
| https://marça.online / https://xn--mara-2oa.online | Apex custom domain (set DNS at Hostinger) |
| This repo | https://github.com/marsaflix-eng/marca-online-store — full site on `main`; project Pages API enable is blocked for Actions tokens — use user site above |

WhatsApp orders: **+222 48 65 05 85** (`22248650585`).

## Pages / security

- Serves from GitHub Pages (user site `marsaflix-eng.github.io`).
- `CNAME` = `xn--mara-2oa.online` (punycode for marça.online).
- CSP via `<meta http-equiv="Content-Security-Policy">` in `index.html` (includes `form-action` for `wa.me` / `api.whatsapp.com`). No `.htaccess`.
- `.nojekyll`, `404.html`, `robots.txt` included.

## Sync to user Pages

After editing this repo, run workflow **Sync storefront** on https://github.com/marsaflix-eng/marsaflix-eng.github.io/actions (or push triggers if configured).
