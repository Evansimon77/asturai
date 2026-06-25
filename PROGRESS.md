# AsturAI website — PROGRESS

The public company site at **asturai.com**: done-for-you AI for businesses in Asturias.
One page, bilingual, no build step.

## NEW REDESIGN IN PROGRESS — "The Descent" (not yet live; replaces the Cinematic homepage)
A full from-scratch redesign is underway, reusing only the *text/info* from the live site, none of
its design. Full method + every locked decision live in **REDESIGN-DECISIONS.md** (the source of truth).

- **2026-06-25 — descent VISUAL CONCEPT locked** via mockup `design/sketches/descent-concept-09.png`:
  an underwater descent — surface light → an octopus guide → a glowing "second brain" deep below.
  Three locked elements: (1) octopus with golden-top / blue-teal-underside balance; (2) the bold
  glowing **Brain-set** brain as the hero "final stage" (orange-gold core, spark cascade); (3) deep
  blue water + central god-ray shaft.
- **Hero asset generated & saved:** `design/assets/octopus-hero.png` (clean complete octopus, all
  tentacles, on black) + `design/assets/octopus-hero-cutout.png` (free transparent cutout, reusable).
- **Reference images** Evan supplied live in `Ex/` (The Neural Connection, Brain set, human brain).
- **Credit note:** Higgsfield balance ~207; background-removal cost ~13 credits (no price preview) —
  new rule added to the `/website` skill: any tool without a visible price = stop and warn first.
- **2026-06-25 — CODED CINEMATIC DIVE BUILT → `index-descent.html`** (separate file; live site untouched).
  After a first slideshow attempt scored 1/10 ("no sense of diving"), Evan pointed at **elvalabs.ai**
  as the target feel and chose a **scroll-driven cinematic dive**: smooth hijacked scroll (Lenis) *is*
  the camera descending; real depth from parallax layers + motion-blur streaks on fast scroll. Setting
  stays the underwater descent (open to going more minimal/abstract later). Evan confirmed the direction
  is **good — keep refining**. Built so far (all coded/free, two WebP images only — `assets/descent/`):
  loading reveal (0→100%), darkening water, central god-ray shaft, surface caustics, rising bubbles,
  drifting depth particles that streak when scrolling fast, the octopus (emerges on entry, leans into the
  dive, mouse-parallax), the brain (grows from a pinpoint → breathing hero at the offer), staggered text
  reveals per beat, depth-gauge meter + menu (right), gold free-look bubble that blooms at the offer,
  EN/ES, reduced-motion, JSON-LD for AI search, favicon. **7 beats** = the locked journey. Studio "we" voice.
- **Next:** Evan to watch it move and give the ONE thing that bugs him most (refining was running blind);
  then keep polishing, and only later decide go-live (replace `index.html`) vs the more-minimal Elva route.
- **Skill improvement (global):** added a reference-sites step to the `/website` discovery (always ask for
  example sites + which exact parts the owner likes; re-ask when a draft misses). Style stays neutral.

## Current state (LIVE)
- **Live at https://asturai.com** (and www) — hosted on **Cloudflare Pages**, auto-deploys
  from GitHub repo `Evansimon77/asturai` on every push to `main`.
- **2026-06-25 — full visual REDESIGN shipped: "Cinematic Film" homepage.** `index.html` is now a
  dark, cinematic, photo-led design (full-screen office-photo scenes, huge type, GSAP + Lenis
  smooth scroll, custom gold cursor, intro curtain, filmic color grade, scroll-velocity motion
  blur, gold film-frame furniture). Uses Evan's pro photos (`assets/evan-portrait.jpg`,
  `assets/office-*.jpg`) + transparent gold/cream lockup (`assets/asturai-clear-cream.svg`).
  All prior copy + EN/ES toggle + JSON-LD preserved intact (109 keys, parity OK).
  - Explored 3 directions; Evan picked Cinematic. The other two drafts are kept in the repo:
    `index-kinetic.html` (kinetic editorial), `index-3d.html` (Three.js octopus). Old dark-gradient
    version saved as `index-darkgradient.html`. Design context in `PRODUCT.md` + `DESIGN.md`.
  - CDN libs (GSAP, Lenis) load from jsdelivr/cdnjs; motion is failure-proof (if a lib fails, all
    content still shows — earlier blank-sections bug was a dead Lenis CDN link, now fixed).
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
- **Keep polishing the Cinematic homepage** (Evan is iterating live): possible next steps he raised —
  full WebGL water-dissolve transitions between scenes (the big version of "liquid"), finer crop
  tuning, more photo curation. Headless screenshots hang on the CDN/animation libs, so verify in a
  real browser.
- Consider removing the unlinked draft pages (`index-3d.html`, `index-kinetic.html`,
  `index-darkgradient.html`) from the deploy once the final is locked (they're reachable by direct
  URL on the live site but not linked anywhere).
- **Close the demo gap:** get 2–3 "demo on request" pieces publicly viewable so visitors can try
  them — currently only the Tasador is clickable.
- Add an @asturai.com email inbox if ever wanted (currently none — uses Gmail).
