# Ironbridge — landing page prototype

Working hero: it loads in through the dither (dots building up), the raw video
scrubs as you scroll, then it dissolves back out through the dither before the
content below. Also included: the scroll-linked forge-heat background gradient
and the pixel-trail cursor. The sections under the hero are placeholders until
the Figma exports arrive.

## Preview it locally

Do NOT open index.html straight off disk (file://). The dither effect reads
pixels from a canvas, and browsers block that on file:// for security, so the
intro will look blank. Run a tiny local server instead:

    cd ironbridge-site
    python3 -m http.server 8000

then open http://localhost:8000 . Use Chrome for the smoothest scrubbing.

## Deploy to GitHub Pages

From inside this folder, point it at your repo and push:

    git init            # already done if you got this as a repo
    git add -A
    git commit -m "Ironbridge landing prototype"
    git branch -M main
    git remote add origin https://github.com/<you>/<repo>.git
    git push -u origin main

Then in the repo: Settings → Pages → Build from branch → main → root. The URL
appears a minute later. Because the assets are all relative, it works as-is.

Alternative: drag this folder onto https://app.netlify.com/drop for an instant
link, no account needed.

## Files

- index.html — the whole page (self-contained apart from Google Fonts + the assets)
- assets/river_scrub.mp4 — the hero video, re-encoded so every frame is a keyframe (smooth scrubbing)
- assets/frame_first.jpg, frame_last.jpg — stills for the dither in/out and the video poster

## Knobs to tweak (top of the <script> and CSS)

- Scrub length: `.hero-scroll { height: 520vh }` — taller means slower scrub.
- Phase timing: `T1..T4` set when the dither-in, scrub and dither-out happen.
- Dither look: `AMP` (texture) and `CW`/`CH` (grain, currently 160×90 ≈ 8px cells).
- Cursor: `MAXAGE` (trail length) and `SIZE` (dot size).
- Palette lives in `PAL`, matching the six-colour set.

## Placeholder / next

- Real sections below the hero, once you send the Figma exports.
- Scroll-velocity logo marquee (needs the logo set).
- Optional live dither control panel for the demo.
- The headline font is a stand-in serif (Instrument Serif); swap in your display face.
