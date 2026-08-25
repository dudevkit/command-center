# COMMAND CENTER - Control Plane Project

## Overview

Unified control plane ("pusat dari segala pusat") for Ravi's tooling: farms, proxy pools, gateways, VPS fleet, shop tools. Currently in **UI/UX RnD phase** - iterating on a high-tech monochrome dark console aesthetic (Vercel/Linear-style) before any backend decisions. Static HTML demo with anime.js motion layer.

Stack (demo only): vanilla HTML/CSS/JS + anime.js v3.2.2 (vendored at `demo/v0.1/lib/anime.min.js`).

## Commands

```bash
# Open demo locally
xdg-open demo/v0.1/index.html            # or just open in browser

# Smoke test (headless, requires playwright in /tmp/cc-smoke)
node /tmp/cc-smoke/shot.js demo/v0.1/index.html /tmp/cc-smoke/out.png

# Deploy demo to GitHub Pages
./scripts/deploy-demo.sh                 # pushes demo/v0.1 to gh-pages branch
```

## Conventions

- **UI direction locked**: ops console dark, zinc stack (`#09090b/131316/18181b`), Inter + IBM Plex Mono, cyan accent sparing, white primary CTA, pill status badges.
- Plain vanilla JS, no build step for the demo. Anime.js v3 syntax (`anime.timeline`, `stagger`, `easeOutExpo`).
- Every demo iteration bumps `v0.x/` folder - never overwrite a shipped iteration (RnD history matters).
- Log every trial/error/decision in `RND-LOG.md`. Keep `ROADMAP.md` current.
- Motion must be motivated (entrance, ticker, state change, feedback). No decorative animation loops.

## Boundaries

- **NEVER** write real infra details into the demo HTML (ports, IPs, keys). Demo data is synthetic mock.
- **NEVER** commit `.env`, credentials, or wallet files. See `RND-LOG.md` for sanitization rules.
- **IMPORTANT** README/AGENTS stay English. Chat with Ravi stays Bahasa Indonesia.

## Dependencies

- `anime.js v3.2.2` (vendored, MIT) - the only external lib in the demo. Deliberately pinned; do not bump without smoke-testing.

## Config

- None required. Demo is fully static, zero env vars.

## Error Handling

- Anime.js silently skips missing targets - if an animation doesn't fire, check the selector exists in the DOM before the call, and that the script runs after `</body>`.
- Headless screenshot drops WebGL/animations by timing: use `--virtual-time-budget` or `page.waitForTimeout` in the shot script.

## Troubleshooting

1. **Animations don't run** -> anime.min.js missing/wrong path. Verify `demo/v0.1/lib/anime.min.js` exists (17KB).
2. **Fonts look wrong in screenshot** -> headless has no Google Fonts; fallback to system mono is expected in CI shots.
3. **Page layout broken at width < 1100px** -> demo targets desktop-first; mobile is out of scope for v0.1 (noted in DESIGN-NOTES).
4. **Screenshot shows blank** -> headless `--with-deps` missing; re-run `npx playwright install chromium --with-deps`.