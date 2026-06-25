# Design

Visual system for asturai.com. Direction: **heraldic luxury** (bright editorial palette lane,
high-contrast serif). Single fast `index.html`, no build step, EN/ES parity preserved.

## Visual Theme

Boutique private-consultancy, almost a heraldic crest brought to life. Cream paper base, deep
navy ink, gold as the one owned metallic accent. Big airy serif display against wide-tracked
small sans labels (extreme scale contrast = the luxury signal). Thin gold hairlines and a
recurring "flourish" motif echoing the octopus tentacles, used as section dividers and quiet
ornament, never as boxes. Generous whitespace, slow eased motion, restrained parallax depth.

## Color (OKLCH, tinted neutrals, ONE accent = gold)

Bright editorial lane only. Never blend with a dark-cinematic lane.

- `--navy`     `#16294D`  primary ink / dark sections
- `--navy-deep``#0F1D38`  deepest navy (contact, footer)
- `--ink`      `#27324A`  body text on cream
- `--gold`     `#C5A059`  the one owned accent (hairlines, flourish, key CTA)
- `--gold-deep``#A8843F`  gold for text/contrast on light (AA on cream)
- `--cream`    `#EFEBE2`  page base
- `--cream-soft`#F5F1E8`  alternating section base
- `--taupe`    `#6F6857`  muted secondary text
- `--line`     `rgba(22,41,77,.12)` hairline

Rules: gold is ornament + ONE primary CTA, not a fill-everything color. No second accent hue.
On navy, text is cream; gold used only for accents/labels (check AA for any gold body text).

## Typography

High-contrast serif lane (matches the ornate wordmark).
- **Display / headings:** a high-contrast editorial serif. Load **Cormorant Garamond** (or
  Fraunces as alt) via one Google Fonts call (display swap). Weights 400/500, large sizes,
  tight leading (~1.05–1.12), slight negative tracking on the biggest sizes.
- **Body + labels:** a clean neutral sans. Keep the existing system-sans stack OR load one
  light webfont (e.g. Inter) — body 16–18px, line-height ~1.6, max 65–75ch.
- **Eyebrow labels:** small (12–13px), UPPERCASE, wide tracking (~.16em), taupe/gold. These are
  the quiet counterweight to the giant serif headlines.
- Hierarchy: ≥1.25 scale ratio between steps; lean on the serif/sans + size contrast, not weight soup.

## Signature moves (the "premium" feel Evan asked for)

- **Hero:** the octopus + AsturAi wordmark lockup as the centerpiece, on cream with a soft gold
  radial aura. Big serif headline beneath. Subtle multi-layer **parallax**: the gold aura and a
  faint flourish drift slower than the text on scroll. Respect `prefers-reduced-motion`.
- **Flourish dividers:** thin gold tentacle-curl SVG between major sections instead of hard rules.
- **Services:** break the 9-identical-card grid. Editorial list / asymmetric layout, numerals set
  in serif, hairline separators, lots of air. Density demoted, one item reads at a time.
- **Work (navy section):** the one dark moment, cinematic. Larger featured project, the rest
  quieter. Gold "Live" accents. Hover = slow lift, no bounce.
- **Scroll reveals:** gentle fade/rise on section entry (choreographed, slow ease-out), not on
  every element. One considered transition over many flourishes.

## Motion

Ease-out only, long curves (ease-out-quint/expo), ~500–800ms for reveals, ~150–250ms for hovers.
No bounce, no elastic. Never animate layout properties (transform/opacity only). Parallax via
transform on scroll, throttled with rAF. All motion gated behind `prefers-reduced-motion: no-preference`.

## Layout

Max content width ~1080–1140px, but vary it: hero and work can go wider/full-bleed, text columns
stay narrow (65–75ch). Vary vertical rhythm between sections (don't pad everything equally).
Avoid wrapping everything in cards; use whitespace and hairlines to separate. Mobile: single
column, parallax reduced, nav collapses (keep language toggle + primary CTA reachable).

## Components

- **Buttons:** pill, three weights — primary gold (one per view region), navy solid, ghost
  (navy outline). Hover lifts 1px + slight bg shift, eased. Visible focus ring (gold).
- **Language toggle:** keep the EN/ES pill; restyle to match (hairline, gold "on" state ok).
- **Flourish SVG:** small reusable gold tentacle-curl, inline SVG, used as divider + ornament.
- **Eyebrow:** uppercase wide-tracked label + short gold tick, as today but refined.

## Don't

System-font headings, identical card grids, the circle-octopus symbol as hero, gradient text,
glassmorphism-by-default, side-stripe borders, second accent hue, fast/bouncy motion, any layout
that breaks the EN/ES toggle or slows first paint.
