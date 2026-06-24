# AsturAI — company website

The public website for **AsturAI** (asturai.com): done-for-you AI systems for
businesses in Asturias.

- One page, no build step — plain HTML/CSS/JS.
- Bilingual: English first, Spanish second, with automatic browser-language
  detection and a manual 🇬🇧/🇪🇸 toggle (saved per visitor).
- Brand: navy `#16294D` · gold `#C5A059` · cream `#EFEBE2`, Georgia headlines.
  Logos live in `assets/` (horizontal AsturAI logo + icons).

## Edit / preview locally
```bash
python3 -m http.server 8300   # then open http://localhost:8300
```

## Hosting
Served by **Cloudflare Pages** from this repo. Settings:
- Framework preset: **None**
- Build command: *(empty)*
- Build output directory: **/**

Every push to `main` triggers an automatic rebuild and deploy.
