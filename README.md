# Marça — Digital Boutique

Elegant static storefront for **Marça** (`marça.online`). Multi-product boutique; Snapchat Plus is one product with nested plans.

Payment: **Bankily only** via WhatsApp — no card processing on-site.

## Flow (Snapchat Plus)
Home product grid → Snapchat Plus → plans (3m 170 / 6m 330 / 1y 630 MRU) → Snap username → follow Snap → Bankily agree → WhatsApp `wa.me/22248650585`.

## Config
Edit `js/config.js`: `WHATSAPP_E164`, `SNAP_FOLLOW_URL`, `STORE_NAME`, `DOMAIN`, `PRODUCTS[]` with nested `plans`.

## Security
CSP strict self, no CDNs, `textContent` only, `encodeURIComponent` for WhatsApp.
