# AsturAI website — PROGRESS

The public company site at **asturai.com**: done-for-you AI for businesses in Asturias.
One page, bilingual, no build step.

## Current state (LIVE)
- **Live at https://asturai.com** (and www) — hosted on **Cloudflare Pages**, auto-deploys
  from GitHub repo `Evansimon77/asturai` on every push to `main`.
- One-page site: top bar (horizontal logo + 🇬🇧/🇪🇸 switch + "Talk to me"), hero, "what I do"
  (find → build → maintain), four project cards, "why an octopus" story, contact (WhatsApp +
  email), footer.
- **Bilingual**: English first, Spanish second — auto-detects the visitor's browser language
  and remembers their manual choice (`asturai_lang` in localStorage).
- Brand: navy `#16294D`, gold `#C5A059`, cream `#EFEBE2`, Georgia headlines. Only the
  **horizontal** AsturAI logo is used (octopus-only symbol was rejected). Logos in `assets/`.
- The **"The Tasador" card links to the live tool** at https://tasador.asturai.com ("Try it live →").
- Contact: WhatsApp +34 613 286 809, email evanastur@gmail.com.

## Hosting facts (so deploys/DNS aren't a mystery)
- Cloudflare Pages project `asturai` → `asturai.pages.dev`. Build = framework None, no build
  command, output dir `/`.
- Domain registered at **Hostinger**; nameservers point to **Cloudflare** (`carter`/`chin`.ns.cloudflare.com).
- DNS in Cloudflare: `asturai.com` + `www` → CNAME `asturai.pages.dev` (proxied);
  `ops` → A 130.110.235.41 (DNS only); `tasador` → A 130.110.235.41 (DNS only).
- Netlify is fully abandoned (old project's domain removed).

## To edit
Change files here → `git push` (or `/save`) → Cloudflare rebuilds automatically (~1 min).
Local preview: `python3 -m http.server 8300`.

## Next (optional ideas)
- Make the other project cards clickable when those tools have public homes.
- Add an @asturai.com email inbox if ever wanted (currently none — uses Gmail).
