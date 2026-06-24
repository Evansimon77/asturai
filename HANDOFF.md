# HANDOFF — asturai-site (AsturAI website + Tasador demo) · 2026-06-24
project: /Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site

## Resume in one move
Nothing pending — both sites are live. If continuing, confirm they're up:
`curl -sI https://asturai.com | head -1` and `curl -sI https://tasador.asturai.com | head -1`

## Goal
Give Evan a professional portfolio presence: a company site at **asturai.com** plus a
live, clickable **Tasador** property-valuation demo, to show his work from asturai.com.

## State
- **Done:**
  - **asturai.com is LIVE** — bilingual (EN default, ES, auto-detect + toggle) one-page site on
    **Cloudflare Pages**, auto-deploys from GitHub `Evansimon77/asturai` (this folder) on push to `main`.
  - **tasador.asturai.com is LIVE** — the standalone Tasador (FastAPI) running on Evan's **Oracle
    server** as systemd service `tasador` (uvicorn 127.0.0.1:8200) behind the server's **Caddy**.
  - asturai.com's "The Tasador" card **links to** tasador.asturai.com ("Try it live →").
  - Both projects backed up via `/save` (bookmarks `asturai-com-live`, `tasador-deployed`).
  - Fixed: `ops.asturai.com` (WhatsApp ops) broke during the nameserver migration → re-added in Cloudflare DNS.
  - Fixed: Evan's Mac couldn't load asturai.com — his router served a stale Netlify IP; set Wi-Fi DNS to 1.1.1.1/8.8.8.8.
- **In flight:** none — reached a clean stopping point.
- **Blocked / open:** Alegria team-tab → live Tasador is **committed to `main` (commit 0b868f9) but NOT
  deployed**. Alegria's demo site is deliberately **frozen/locked** at a June-10 deploy; `main` is **34
  commits ahead**. Evan keeps it locked until he finishes features. Release the whole batch later, not just this.

## Next steps (all optional / future)
1. When Evan finishes Alegria features → release Alegria `main` (34 commits) as one reviewed batch; the
   Tasador team-tab connection is already in there.
2. Optional cleanup: delete unused `render.yaml` + `Procfile` from the `tasador-demo` folder.
3. Optional: make the other asturai.com project cards clickable once those tools have public homes.

## Key files
- `/Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/index.html` — the whole website (one file + `assets/` logos).
- `/Users/evansimonenko/Documents/Cursor Code/Projects/asturai-site/PROGRESS.md` — website state + hosting facts.
- `/Users/evansimonenko/Documents/Cursor Code/Projects/tasador-demo/` — the Tasador app (deployed to the server; see its PROGRESS.md).
- `/Users/evansimonenko/Documents/Cursor Code/Projects/Alegria/src/components/equipo/TasadorBox.astro` — team-tab iframe → live Tasador (on `main`, awaiting release).
- Memory: `asturai-com-hosting.md` — full hosting map (server host/SSH key, ports, DNS) in plain words.

## Don't-trip wires
- **Alegria demo is LOCKED on Netlify on purpose.** Do NOT unlock/deploy `main` without Evan's explicit
  "release everything" decision — it'd publish 34 commits (live CRM listings, etc.) at once.
- **`tasador` DNS in Cloudflare must stay "DNS only" (grey cloud)** — proxying breaks Caddy's auto SSL cert.
  Same for `ops`.
- Domain registered at **Hostinger**; nameservers point to **Cloudflare**. Netlify is fully abandoned.
- Server host/SSH-key/IP live in the `asturai-com-hosting` memory — don't hard-code secrets into committed files.
- Recurring red herring: "site can't be reached" was always **local DNS cache** (router/browser/Mac), never the live site.
- Evan's site contact (public, intentional): WhatsApp +34 613 286 809, evanastur@gmail.com.

## Run / verify
- **Edit the website:** change files here → `git push` (or `/save`) → Cloudflare rebuilds (~1 min). Local preview: `python3 -m http.server 8300`.
- **Update the Tasador:** rsync `tasador-demo/` to the server, then `sudo systemctl restart tasador` (see asturai-com-hosting memory for host).
- **Confirm live:** `curl -sI https://asturai.com | head -1` → 200; `curl -s https://tasador.asturai.com/api/places?q=Oviedo` → JSON results.
