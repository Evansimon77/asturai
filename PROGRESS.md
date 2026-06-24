# AsturAI website — PROGRESS

The public company site at **asturai.com**: done-for-you AI for businesses in Asturias.
One page, bilingual, no build step.

## Current state (LIVE)
- **Live at https://asturai.com** (and www) — hosted on **Cloudflare Pages**, auto-deploys
  from GitHub repo `Evansimon77/asturai` on every push to `main`.
- **2026-06-24 — big content + SEO expansion** (after a full scan of every project Evan has built):
  - Sections now: top bar (logo + 🇬🇧/🇪🇸 + "Talk to me"), hero, trust strip (5 badges),
    **9 service cards** ("What I build"), how-it-works (3 steps), **8 portfolio cards** with
    honest status tags (Live / Demo on request / Case study), "why an octopus" story,
    **7-question FAQ**, contact, footer.
  - **Identity/title (locked):** display name **Evan D. Simon**; title
    **"AI Solutions Architect & Developer · Automation & Systems Engineer"**.
  - **Positioning = freelance, fully remote, worldwide** (Canadian citizen, Spanish residency,
    Asturias = home base only). `areaServed` in the data is Worldwide + Europe + Americas +
    Spain + Canada — deliberately NOT region-locked, so AI search doesn't treat him as local-only.
  - **Search/AI-visibility plumbing added:** JSON-LD business card (ProfessionalService + Person
    + WebSite + FAQPage with 8 Q&As), full meta/OG/Twitter tags, `sitemap.xml`, `robots.txt`
    (explicitly welcomes GPTBot/ClaudeBot/PerplexityBot/Google).
  - Visual design/layout unchanged on purpose — Evan will redesign the layout next; this pass
    was content + invisible SEO only (both design-independent).
- **Bilingual**: English first, Spanish second — auto-detect + manual choice (`asturai_lang`).
  All 109 text pieces have matching EN + ES; JSON-LD validates.
- The **"The Tasador" card links to the live tool** at https://tasador.asturai.com ("Try it live →").
  Only public clickable demo so far; other pieces marked "demo on request" (live on Evan's machine).
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
- **Redesign the layout** (Evan's next step — content is now all in place to design around).
- **Close the demo gap:** get 2–3 "demo on request" pieces publicly viewable (host them, or short
  screen-recordings) so visitors can actually try them — currently only the Tasador is clickable.
- Make the other portfolio cards clickable once those tools have public homes.
- Add an @asturai.com email inbox if ever wanted (currently none — uses Gmail).
