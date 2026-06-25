# HANDOFF — asturai-site (AsturAi "Descent" redesign) · 2026-06-25

project: /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site

## Resume in one move
Start the server, open the page, then begin the audit fixes (P0/P1 first — wire the dead form, fix mobile overflow, strengthen Proof, collapse the 7 `<h1>`s):
`cd "/Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site" && python3 -m http.server 8300`
→ open http://localhost:8300/index-descent.html

## Goal
Build a brand-new homepage for asturai.com — a scroll-driven cinematic underwater "dive" (scrolling IS a
camera descending: surface light → octopus guide → glowing "second brain" deep below). Reuse only the
text/info from the live site, none of its design. Studio "we" voice (NOTE: audit flagged this — see wires).
Desktop-first. Reference feel: elvalabs.ai (smooth camera-scroll, calm, big quiet type, loading reveal).

## State
- Done:
  - Full cinematic build lives in **index-descent.html** (separate file; the LIVE `index.html` is untouched
    and still deployed). Mechanic: tall scroll spacer + fixed visual stage; Lenis smooth scroll (CDN) drives
    a per-frame `render(p,time)` mapping scroll 0→1 to everything. Failure-proof: works without Lenis.
  - 7 beats (surface hook → pain → after → proof → why bespoke+private → free first look → stay in touch),
    EN/ES, reduced-motion, JSON-LD, depth-gauge nav (right), gold free-look bubble, loading reveal.
  - **Octopus = Evan's own art.** Earlier auto-cutouts kept leaving a glow/box on the head; gave up on
    heuristics and used Evan's clean transparent PNG `Ex/Pulpo.png` → tidied + scaled → `assets/descent/octopus.webp`
    (137K), frame ratio in CSS set to 1100/854.
  - **Living water added** (commit e7e99b0, bookmark `descent-living-water`): real underwater SURFACE at the
    top (bright band + moving caustic ripples = waves seen from below), 5 swaying/shimmering GOD-RAY beams that
    fade with depth (canvas `drawSurface()` + `drawGodRays()`), and an animated SVG displacement "current"
    (`#octoWobble` filter) that flows through the octopus so its TENTACLES DRIFT instead of sitting frozen.
    All coded/free; respects reduced-motion. Verified with a Playwright screenshot — looks atmospheric, octopus
    not melted.
  - **Full design audit done** (vs PRODUCT.md quiet-luxury brief). Score ~25/40 = "gorgeous, not yet effective".
- In flight: nothing half-edited. Tree is CLEAN and pushed (latest commit e7e99b0). We just finished saving +
  bookmarking the living-water version as a restore point, and fixed a GitHub push-auth problem (see wires).
  Evan's stated intent: NOW implement the audit fix list, starting P0/P1.
- Blocked / open: still need real content from Evan eventually — 2–3 real client quotes for Proof, and the
  email-freebie one-pager. Direction decision is settled: keep the dive, add a fast skim path (Option A).

## Next steps (the audit fix list — Evan wants to implement these)
1. **P0/P1 — breakers first:**
   - Wire the dead signup form (beat 6 throws name/email away) + the LinkedIn link (`href="#"`).
   - Fix mobile overflow: beats are locked to one screen height; the Proof beat (4 items) and Free-look beat
     (two columns + 2 buttons + reassure line) stack tall and run off a phone screen. CONFIRM on a phone view
     first (Playwright at ~390px), then fix.
   - Strengthen Proof (beat 3): only Tasador is clickable. Add more live links / a screenshot / one real quote.
   - Collapse the **7 `<h1>`s** → one h1, the rest h2 (SEO + screen-reader + AI-search; PRODUCT.md names the AI
     engine as a co-primary reader).
   - Add visible keyboard focus states (PRODUCT.md promises them; custom buttons currently show none).
2. **P2 — feel/templated tells:** stop using the same gold-italic emphasis in ALL 7 headlines; vary the
   all-centred compositions (move text off the octopus so the `.in::before` blur scrim isn't needed); bring
   Evan in (a face, "I" not "we" — the single-artisan trust signal the brief wants); depth-gauge labels always
   visible (and present on mobile, currently hidden at ≤720px).
3. **P3 — polish:** ease down octopus mouse-parallax (seasick risk: `pmx*2.4vw` + rotate); recheck dim-text
   (`--cream-dim`) contrast over the moving water.
4. Later: decide go-live (replace `index.html` → deploy = git push → Cloudflare auto-build). NOT until Evan says.

## Key files
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/index-descent.html — the new build (self-contained: CSS + JS + i18n + SVG filter inline).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/assets/descent/octopus.webp — Evan's octopus, cleaned (the hero character).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/assets/descent/brain.webp — the deep "second brain" (screen-blended glow).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/Ex/Pulpo.png — SOURCE of the octopus (Evan's original transparent art, 8.8MB).
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/PRODUCT.md — brand brief (register=brand, quiet-luxury). The audit was scored against this.
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/PROGRESS.md — current state + the full prioritised audit fix list.
- /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/index.html — the LIVE site (Cinematic Film). DO NOT touch until go-live decision.

## Don't-trip wires
- **index-descent.html is NOT live.** asturai.com still serves `index.html`. Never overwrite the live file or
  push a deploy without Evan's explicit go. (Pushing to GitHub = private backup only, safe; Cloudflare only
  rebuilds from changes to the live files, so a backup of index-descent.html does not deploy anything.)
- **Restore point:** `git checkout descent-living-water` (a tag) returns to exactly the current good version.
- **GitHub push was broken, now fixed:** the remote used HTTPS password auth (dead). Ran `gh auth setup-git`
  so git uses the `gh` token (account Evansimon77). Saves should push cleanly now.
- **Octopus cutout history (don't repeat the dead ends):** the god-rays in the original art are golden AND
  bright AND smooth, so brightness, colour, and texture tricks all FAILED to remove them cleanly. Solution was
  Evan's own clean PNG. If a new octopus is ever needed, use `rembg` (installed in a python3.13 venv at
  /private/tmp/.../scratchpad/rembg-venv — may be cleared) — it's free/local; do NOT pay Higgsfield
  remove_background (~13 credits, no price preview).
- **The brain uses `mix-blend-mode:screen`** — it MUST sit on pure black or a box reappears.
- **All motion is coded (free).** Buy the puppet (octopus/brain art), code the movement. No generated video.
  The octopus "moving tentacles" = an animated SVG `feDisplacementMap` (`#octoWobble`, scale 15) — if it's too
  strong/melty lower the scale; if a laptop fan spins up, that filter is the cost (animated turbulence).
- **Audit's #1 finding (the real design issue, not the octopus):** the 7-screen forced dive blocks the skimming
  buyer (PRODUCT.md says they're often on a phone, skimming, deciding in seconds). Decision = keep the cinema
  but add a fast skim path. This is the "why" behind the fix list above.
- Reporting to Evan: plain language, no jargon, ONE real-world picture for hard ideas, English. Divergent/ADHD —
  "still complicated" means simpler, not longer. He pushed back hard on lazy "just confirm it fits" answers —
  do the real design thinking and follow through.

## Run / verify
- Serve: `cd "/Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site" && python3 -m http.server 8300`
- Open: http://localhost:8300/index-descent.html — scroll slow AND fast (fast = particle streaks); watch the
  top waves + god-ray beams; watch the octopus tentacles drift; move the mouse (parallax).
- JS sanity after edits: extract the last `<script>` block and `node --check` it.
- Screenshot to verify visually (Python Playwright is installed): goto the URL, wait ~3s for loader, screenshot;
  to see a dive frame, `window.scrollTo(0, document.body.scrollHeight*0.10)` then screenshot. Use ~390px width
  to check the mobile-overflow bug.
