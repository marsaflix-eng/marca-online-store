# Marça

Static storefront for **Marça** (`marça.online`).

Payment: **Bankily only** via WhatsApp — no card processing on-site.

## Structure
```
index.html
assets/logo-m-3d.png          # 3D M mark (favicon/header)
assets/products/snapchat.png  # Snapchat ghost product image
css/base.css + products.css + checkout.css
css/styles.css                # combined (Pages/Hostinger)
js/config.js
js/app.js
```

## Flow (Snapchat Plus)
Home → Snapchat Plus (brand logo) → plans (3m 170 / 6m 330 / 1y 630 MRU) → يوزر سنابشات → follow Snap → Bankily agree → WhatsApp `wa.me/22248650585`.

## Config
Edit `js/config.js`: WhatsApp, Snap follow URL, `PRODUCTS[]` (use each brand’s official logo as `image`).
