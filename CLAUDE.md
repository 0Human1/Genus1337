# GENUS1337 — Claude Code Project Brief

## What This Is
A personal creative website at **genus1337.com** with three distinct sections that each feel like a different site. Built with plain HTML/CSS/JS. No framework, no build step.

## Live Infrastructure
- **Domain:** genus1337.com (registered at Spaceship)
- **DNS/CDN/SSL:** Cloudflare (free)
- **Hosting:** Cloudflare Workers (free) — static asset serving
- **Repo:** github.com/0Human1/Genus1337
- **Auto-deploy:** Every push to `main` triggers a live deploy via Cloudflare Workers CI

## How Deploys Work
Push to `main` → Cloudflare detects the change → runs `npx wrangler deploy` → live at genus1337.com within ~60 seconds. No manual steps needed.

## Repo Structure (current)
```
/
├── index.html        ← Portal homepage (the hub)
├── wrangler.toml     ← Cloudflare Workers config (do not delete)
├── README.md
├── /rave/
│   └── index.html    ← 3D rave environment (to be built)
├── /log/
│   └── index.html    ← Blog/essays (to be built)
└── /fund/
    └── index.html    ← Finance/hedge fund exploration (to be built)
```
The `/rave/`, `/log/`, `/fund/` subdirectories don't exist yet — create them when building those sections.

## wrangler.toml (do not modify unless you know what you're doing)
```toml
name = "genus1337"
compatibility_date = "2025-01-01"

[assets]
directory = "."
```

## Design System

### Palette
| Name | Hex | Used For |
|---|---|---|
| Void | `#050508` | Global background |
| Rave BG | `#06001A` | Rave section background |
| Rave Violet | `#9B00FF` | Rave primary accent |
| Rave Green | `#00FF41` | Rave secondary accent |
| Blog BG | `#F4F2EC` | Blog section background |
| Blog Text | `#111111` | Blog text |
| Fund BG | `#030D1A` | Fund section background |
| Fund Teal | `#4DFFB4` | Fund accent / data up |
| Fund Red | `#FF4D6D` | Fund data down |
| Fund Muted | `rgba(168,196,212,0.88)` | Fund headings |

### Typography
- **Display:** `Space Grotesk` (Google Fonts) — headings, portal names
- **Mono:** `JetBrains Mono` (Google Fonts) — UI labels, data, eyebrows, code
- Load both via: `https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&family=JetBrains+Mono:wght@300;400&display=swap`

### Visual Tone per Section
| Section | Vibe | Key traits |
|---|---|---|
| **RAVE** | Dark cyberpunk, neon | Particle systems, glitch effects, purple/green glow, Three.js |
| **LOG** | Minimal, clean | Off-white paper feel, serif or clean sans, calm |
| **FUND** | Cold terminal | Monospace data, navy dark bg, teal accent, ticker animations |

## Current Homepage (index.html) — What It Does
- Three full-height panels side by side (flexbox)
- Hover a panel → it expands (flex: 1.7), others compress (flex: 0.65)
- **RAVE panel:** Canvas particle system (purple/green particles rising), glitch animation on hover
- **LOG panel:** Ghost blog post titles fading in/out, paper-white background
- **FUND panel:** Live price ticker with jittering fake market data
- UTC clock in top-right header
- Clicking a panel links to `/rave/`, `/log/`, `/fund/`

## Section Goals

### /rave/ — 3D Environment
- Immersive 3D audiovisual experience using **Three.js**
- Dark, full-screen, music-forward
- Target feel: standing inside a rave, looking up at the stage
- Ideas: particle field, geometric shapes reacting to audio, camera fly-through
- Import Three.js via CDN: `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js`

### /log/ — Blog
- Clean reading experience, stark contrast to the rave section
- Blog posts as static HTML pages (no CMS needed to start)
- Minimal nav, large typography, generous whitespace
- Background: `#F4F2EC`, text: `#111`

### /fund/ — Finance Exploration
- Research/analysis on hedge funds, market structure, systematic strategies
- Terminal/data aesthetic — feels like a Bloomberg terminal but designed
- Monospace throughout, cold color palette
- Could include: essay-style posts, data visualizations, reading lists

## Git Workflow
```bash
# Make changes to files
git add .
git commit -m "description of what you changed"
git push origin main
# → auto-deploys to genus1337.com in ~60 seconds
```

## Things to Avoid
- Don't delete `wrangler.toml` — the site won't deploy without it
- Don't add large video/audio files to the repo — use external CDN links instead
- Keep Three.js imported via CDN, not bundled
- Don't add a package.json or node_modules — no build step exists

## Add a .gitignore (recommended)
Create a `.gitignore` file with:
```
.wrangler/
node_modules/
.DS_Store
```
This stops internal Cloudflare/system files from being uploaded as site assets.

## Owner
James Scott — `jnickscott@gmail.com` — GitHub: `0Human1`
