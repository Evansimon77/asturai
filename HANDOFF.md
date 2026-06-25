# HANDOFF — asturai-site (AsturAi "Descent" redesign) · 2026-06-25
project: /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site

## Resume in one move
Start the local server, hard-refresh the page, and ask Evan for the ONE next thing that's off:
`cd "/Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site" && python3 -m http.server 8300`
→ open http://localhost:8300/index-descent.html

## Goal
Build a brand-new homepage for asturai.com — a **scroll-driven cinematic underwater "dive"** where
scrolling IS a camera descending: surface light → octopus guide → a glowing "second brain" deep below.
Reuse only the *text/info* from the live site, none of its design. Studio "we" voice. Desktop-first.
Reference feel Evan picked: **elvalabs.ai** (smooth camera-scroll, calm/minimal, big quiet type, loading reveal).

## State
- Done:
  - Full cinematic build lives in **index-descent.html** (a SEPARATE file — the LIVE `index.html`
    "Cinematic Film" homepage is untouched and still deployed).
  - Mechanic: tall scroll spacer + fixed visual stage; smooth scroll via **Lenis** (CDN); a per-frame
    `render(p,time)` maps scroll progress 0→1 to everything. Failure-proof: if Lenis dies, native scroll
    + self-computed velocity still drive it.
  - Coded/free effects: loading reveal (0→100%), darkening water, central god-ray **shaft**, surface
    caustics, rising bubbles, depth particles that **streak on fast scroll** (the "diving" cue),
    octopus (emerges on entry, leans into the dive, mouse-parallax), brain (grows from a pinpoint →
    breathing hero), staggered text reveals per beat, depth-gauge meter+menu (right), gold free-look
    bubble (blooms at offer), EN/ES, reduced-motion, JSON-LD for AI search, SVG favicon.
  - **7 beats** = the locked journey (surface hook → pain → after → proof → why bespoke+private → free
    first look → stay in touch). Real facts reused (Tasador live link, Verter, AI Ops, Ask-Your-Docs;
    WhatsApp +34 613 286 809; email evanastur@gmail.com).
  - Two hero images only, cleaned & tiny (`assets/descent/`): octopus.webp (160K) + brain.webp (128K).
  - **Just fixed (uncommitted):** (1) octopus "blurry stuff" — removed the attached top light-fan by
    fading the image top to transparent + keeping the largest connected shape; (2) brain "square" —
    subtracted its navy background to true black + feathered edges so the screen-blend box is gone;
    (3) brain "too big" — cut ~half (CSS width min(46vh,330px), JS bScale 0.12+bp*0.95) and sits lower.
- In flight: the three image fixes above are applied to files and the HTML but **NOT yet committed**
  (git shows brain.webp, octopus.webp/png, index-descent.html modified). Waiting on Evan to eyeball.
- Blocked / open: Evan has mostly been saying "go on" without watching it move — needs a real look and
  ONE concrete reaction to aim the next round. Direction confirmed "good — keep refining."

## Next steps
1. Get Evan's look at the 3 fixes (octopus haze, brain box, brain size). Adjust if still off.
2. `/save` to commit the image fixes (they're currently uncommitted).
3. Keep refining per his ONE piece of feedback. Possible later fork (his words): may go MORE minimal/
   abstract like Elva (less literal water) — not now.
4. Eventually decide go-live: replace `index.html` with the descent build (deploy = git push →
   Cloudflare Pages auto-build). NOT until Evan says so.
5. Still-open content TODOs: 2–3 real client quotes for Proof; the email-freebie one-pager.

## Key files
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/index-descent.html — the new build (self-contained: CSS + JS + i18n inline).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/assets/descent/octopus.webp — cleaned transparent octopus (reusable character).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/assets/descent/brain.webp — cleaned brain (screen-blended glow).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/REDESIGN-DECISIONS.md — source of truth: all locked rounds + the descent concept.
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/PROGRESS.md — current state (live site facts + the new build).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/index.html — the LIVE site (Cinematic Film). DO NOT touch until go-live decision.
- Source/originals: design/assets/octopus-hero.png (octopus on black), Ex/Brain set.png (brain source).

## Don't-trip wires
- **index-descent.html is NOT live.** asturai.com still serves `index.html`. Never overwrite the live
  file or push a deploy without Evan's explicit go.
- The brain uses CSS `mix-blend-mode:screen` — it MUST sit on pure black or a box reappears. If you
  re-export it, subtract the navy background again (it was ~[15,31,43]).
- Octopus haze can't be split by brightness/saturation (it's equally bright AND colorful) — only by
  SHAPE (top-fade + largest connected component). Don't waste time on threshold tricks.
- Higgsfield credits ~207, shared across projects. `remove_background` has NO price preview and cost
  ~13 credits last time. Rule: any tool with no visible price = STOP and warn before running it. All
  the image cleanup here was done FREE with Python PIL+numpy+scipy — keep it that way.
- All motion is coded (free). Buy the puppet (octopus/brain), code the movement. No generated video.
- Reporting to Evan: plain language, no jargon, ONE real-world picture for hard ideas, English. He's
  divergent/ADHD — "still complicated" means simpler, not longer.
- `/website` skill was improved this session (global, not project): discovery now always asks for
  reference sites + which exact parts the owner likes, and re-asks when a draft misses. Style stays neutral.

## Run / verify
- Serve: `cd "/Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site" && python3 -m http.server 8300`
- Open: http://localhost:8300/index-descent.html — scroll slow AND fast (fast = particle streaks), move mouse (parallax).
- JS sanity check after edits: extract the last `<script>` block and `node --check` it (done routinely this session).
- Verify it FEELS like diving: water darkens, light shaft recedes up, brain grows + breathes, octopus leans on fast scroll.
