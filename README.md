# Diginext Scandinavia — Full Website

**Live preview:** https://ginigeashan-alt.github.io/diginext/

Complete multi-page industrial B2B site for a Nordic digital infrastructure company. Six HTML pages sharing a common stylesheet, header, footer and the real Diginext logo.

## Pages

1. **`index.html`** — Homepage. Hero with live rack monitoring card, services grid, stats band, industries tiles, Nordic reach map with city table, CTA band.
2. **`about.html`** — Mission & vision split, 12 company values in a grid, team section with stats band.
3. **`services.html`** — Six deep-dive service sections with images, descriptions, feature lists, per-service CTAs (Structured Cabling, Fibre Optic, Installation, Network, Labelling & Documentation, 24/7 Support).
4. **`industries.html`** — Six industry verticals with alternating image+copy rows (Hyperscale, Colocation, Cloud, Enterprise, AI/HPC, Telecom).
5. **`careers.html`** — **With interactive location modal.** Four location cards (Stockholm, Kristiansand, Falun, Warsaw) that open detailed project modals with specs, shift patterns, and roles. Plus an open-roles list with 6 live positions.
6. **`contact.html`** — 7-field contact form, three office cards (Sweden HQ, Norway, 24/7 NOC), and a "not sure who to ask for" secondary CTA.

## File structure

```
diginext-site/
├── index.html
├── about.html
├── services.html
├── industries.html
├── careers.html
├── contact.html
├── assets/
│   └── logo.svg          ← the real Diginext Scandinavia logo
├── css/
│   └── styles.css        ← shared across all pages (~2,000 lines)
├── build_pages.py        ← generator script (optional — only needed to regenerate)
├── _partials.py          ← header/footer/layout templates (used by build script)
└── README.md
```

## How to preview

Open any `.html` file in a modern browser. Internet connection required for:
- Google Fonts (Inter, JetBrains Mono)
- Unsplash CDN imagery

## How to host

Easiest options:
- **Netlify Drop** → https://app.netlify.com/drop (drag the whole folder, get a public URL in ~10 seconds)
- **Vercel** → `vercel --prod` from the folder
- **Cloudflare Pages** → push to Git and connect
- **Any static web host** → all files are self-contained static HTML/CSS/SVG

## Logo

The real Diginext logo (`assets/logo.svg`) is used on all pages:
- **Nav:** displayed as-is (blue wordmark on white bg)
- **Footer:** inverted to white via CSS `filter: brightness(0) invert(1)` on the dark navy background

If the client wants to swap the logo later (for a proper vector version or a new variant), just replace `assets/logo.svg` — every page picks it up automatically.

## Regenerating pages

If you want to edit copy across all pages at once (header, footer, nav links):

```bash
python3 build_pages.py
```

This regenerates all six HTML files with fresh shared header/footer from `_partials.py`. Edit the body content in `build_pages.py` and rerun.

For simple copy edits on a single page, just edit the `.html` file directly — you don't need to run the build script.

## Design system

**Palette**
- `#0A1B3D` navy-900 (darkest — footer, hero, dark bands)
- `#0F2451` navy-800 (primary — buttons, headlines)
- `#1E3A8A` navy-700 (brand blue)
- `#00B4D8` cyan (accent — CTAs, status pills, highlights)
- `#F8FAFC` alt bg (alternating section bands)
- `#0F172A` ink (body text)

**Typography**
- Inter (400/500/600/700/800) — everything
- JetBrains Mono — technical labels, metadata, coordinates

**Imagery**
- All data center photography loaded from Unsplash's free CDN
- Free for commercial use, no attribution required
- To swap: find the `<img src="https://images.unsplash.com/...">` tags and replace

## Interactivity

- **Homepage hero:** live-looking rack monitoring card with blinking port LEDs (CSS animation)
- **Stats band:** scroll-triggered fade-in via IntersectionObserver
- **Careers location modals:** click any location card → full-screen modal with project details; close via X, ESC key, or backdrop click
- **Contact form:** submit shows confirmation and disables fields (client-side only — a real backend is needed for actual delivery)

## Browser support

Tested on modern Chromium-based browsers. Uses CSS Grid, Flexbox, custom properties, `backdrop-filter`, `aspect-ratio`, and `clamp()`. Works in current Safari, Chrome, Edge, Firefox. No IE11.

## If the client wants changes

Common edits (all via find/replace in the HTML files):
- **Swap images:** change any `images.unsplash.com` URL to a hosted asset
- **Change phone/email:** search `+46 73 576 75 20` and `info@diginext.se`
- **Update addresses:** search `Musseronvägen 20` and `Vallentuna`
- **Add/remove a service:** edit `services.html` and the service card block in `index.html`
- **Add a new career location:** copy a `.location-card` block and matching `.modal` block in `careers.html`

For bigger structural changes across all pages (header menu, footer links), edit `_partials.py` and rerun `python3 build_pages.py`.
