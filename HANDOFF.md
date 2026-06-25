# HANDOFF — asturai-site (AsturAI website redesign) · 2026-06-25

project: /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site

## Resume in one move
Start the local server and open the THREE candidate redesigns for Evan to pick from:
```
cd ~/Documents/"Cursor Code"/Projects/asturai-site && python3 -m http.server 8300
```
then open: index-kinetic.html, index-3d.html, index-cinematic.html (all at http://localhost:8300/).
**We are waiting for Evan to choose which of the 3 directions wins.** Once he picks, take that ONE
to truly world-class (perfection pass) and make it the real `index.html`.

## Goal
Redesign asturai.com to look genuinely **next-level / Awwwards-quality** — it's Evan's portfolio AND
his proof of web-design skill for clients. He rejected every incremental change; he wants a DRASTIC,
world-class leap. Keep all existing copy, the EN/ES toggle, and the JSON-LD search data intact.

## State
- **Done — 3 full DRASTIC candidate versions built (each a complete single file, validated):**
  - `index-kinetic.html` — "Kinetic Editorial": giant type, broken grid, custom gold cursor,
    hover-reveal photos, Lenis smooth scroll + GSAP. (95 KB)
  - `index-3d.html` — "3D Interactive Octopus": live WebGL gold octopus (Three.js) reacting to
    mouse/scroll in the hero. (85 KB)
  - `index-cinematic.html` — "Cinematic Film": full-screen office-photo scenes, GSAP/Lenis scroll
    transitions, huge type over imagery. (80 KB)
  - All 3 pass: JSON-LD valid, EN/ES key parity OK, libs present. Built by 3 parallel subagents.
- **Done — assets created:** `assets/evan-portrait.jpg` (886×1100, optimized from Desktop/Firmas),
  `assets/office-1.jpg / office-stand.jpg / office-lounge.jpg / office-server.jpg / office-atrium.jpg`,
  and `assets/asturai-clear-cream.svg` (the gold+cream octopus lockup on TRANSPARENT bg — made by
  stripping the navy `<rect>` out of asturai-reversed.svg; use this on dark backgrounds).
- **Done — design-skill context:** `PRODUCT.md` + `DESIGN.md` written at project root.
- **Current `index.html`** = the earlier "dark cinematic + WebGL mesh-gradient backdrop" version
  (Evan called it only a "small improvement" — it is NOT the target; the 3 candidates supersede it).
- **In flight:** waiting on Evan to pick the winning direction (Kinetic / 3D / Cinematic). Nothing
  half-edited. Next action is his choice, then a perfection pass on that one file.
- **Blocked / open:** none blocking. Could not auto-screenshot the 3 candidates (headless Chrome
  hangs on the CDN animation libs) — they were opened live in Evan's browser for him to judge.

## Next steps
1. Get Evan's pick of the 3 directions (or "push these one or two").
2. Open the chosen file live, fix any rough edges / bugs, then do a full world-class polish pass
   (timing, spacing, type, motion, mobile, reduced-motion, accessibility).
3. Promote the winner to `index.html` (keep the others or archive them).
4. Only then offer `/save` (GitHub) and `/publish` (Cloudflare live). NOTHING is deployed yet.

## Key files
- `index-kinetic.html`, `index-3d.html`, `index-cinematic.html` — the 3 candidate redesigns.
- `index.html` — current live-ish dark version (superseded by the candidates; don't ship as-is).
- `PRODUCT.md` / `DESIGN.md` — design-skill strategy + visual system (heraldic→dark luxury, gold accent).
- `assets/` — logos (use `asturai-clear-cream.svg` on dark), `evan-portrait.jpg`, `office-*.jpg`.
- Scratchpad (reused content cores + brief for any rebuild):
  `/private/tmp/claude-501/-Users-evansimonenko/b28d2920-94b5-4b4e-8872-ed8d99d0c61f/scratchpad/`
  → `_head_meta.html` (DOCTYPE→JSON-LD, paste verbatim), `_str_lang.html` (STR EN/ES dict + lang
  toggle JS, paste verbatim), `SHARED_BRIEF.md` (full rules), `build*.py` (past surgical builds).

## Don't-trip wires
- **Evan wants DRASTIC + premium, not incremental.** He rejected: light reskin, dark-with-cheap-line-
  tentacles, and the WebGL fog ("small improvement"). Thin SVG/line "filigree" reads CHEAP to him —
  avoid it. Aim Awwwards Site-of-the-Day (studios: Obys, Locomotive, Active Theory, Cuberto, Resn).
- **Every visible string lives in the `STR={en,es}` dictionary + has a `data-i18n` key.** EN/ES must
  stay in perfect key parity and the JSON-LD must stay valid. Validate after ANY edit:
  ```bash
  python3 -c "import re,json;h=open('index-kinetic.html').read();json.loads(re.search(r'<script type=\"application/ld\+json\">(.*?)</script>',h,re.S).group(1));k=set(re.findall(r'data-i18n=\"([^\"]+)\"',h));en=set(re.findall(r'\"([a-zA-Z0-9.]+)\":',re.search(r'en:\{(.*?)\n  \},\n  es:',h,re.S).group(1)));es=set(re.findall(r'\"([a-zA-Z0-9.]+)\":',re.search(r'es:\{(.*)\n  \}\n\};',h,re.S).group(1)));print('JSONLD ok | keys',len(k),'| parity',('OK' if not(k-en or en^es) else 'BROKEN'))"
  ```
- **Logo:** Evan LIKES the octopus + "AsturAi" wordmark lockup; he DISLIKES the plain octopus-in-a-
  circle symbol as a hero element. On dark bg use `asturai-clear-cream.svg` (transparent). The plain
  `asturai-reversed.svg` has a navy rectangle baked in — don't use it on near-black.
- **Identity locked:** name "Evan D. Simon"; title "AI Solutions Architect & Developer · Automation &
  Systems Engineer"; freelance, fully REMOTE, WORLDWIDE (never region-lock to Asturias/Spain — kills
  AI-search reach). Photo caption uses the short "AI Solutions Architect & Developer".
- The 3 candidates load **GSAP / Lenis / Three.js from CDN** → they need internet to look right, and
  **headless screenshots hang on them** — verify by opening live in a real browser, not via Chrome
  headless. Reduced-motion fallbacks are built in.
- One self-contained HTML file each, no build step (Cloudflare Pages serves static). CDN libs are OK
  for now; could inline later for the final.
- Hosting: domain at Hostinger → Cloudflare nameservers → Cloudflare Pages, repo `Evansimon77/asturai`
  (folder `asturai-site`), auto-deploys on push to `main`. Contact: WhatsApp +34 613 286 809,
  evanastur@gmail.com.

## Run / verify
- Serve locally: `cd ~/Documents/"Cursor Code"/Projects/asturai-site && python3 -m http.server 8300`
  then open `http://localhost:8300/index-kinetic.html` (and `-3d`, `-cinematic`). Judge LIVE (move the
  mouse, scroll) — the cursor, hover-reveals, 3D, and scroll transitions don't show in a screenshot.
- After any text edit, run the parity/JSON-LD validator above on that file.
- Confirm current site still live (the OLD design): `curl -sI https://asturai.com | head -1` → 200.
