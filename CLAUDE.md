# COMMAND CENTER - Claude Code Brief

Mirror of `AGENTS.md` (Claude Code reads this file, not AGENTS.md).

## Overview

Unified control plane for Ravi's farming/proxy/ops tooling. **UI/UX RnD phase**: iterate on a Vercel/Linear-style monochrome dark ops console with anime.js motion. Static HTML demo - no backend yet.

## Commands

```bash
xdg-open demo/v0.1/index.html            # view demo
node /tmp/cc-smoke/shot.js demo/v0.1/index.html /tmp/cc-smoke/out.png   # smoke screenshot
./scripts/deploy-demo.sh                 # deploy to GitHub Pages
```

## Conventions

- Ops console dark: zinc stack `#09090b/131316/18181b`, Inter + IBM Plex Mono, cyan accent, white primary CTA, pill badges.
- Vanilla JS + anime.js v3 (vendored). No build step.
- New iteration = new `demo/v0.x/` folder. Never overwrite shipped iterations.
- Update `RND-LOG.md` with trials/errors. Keep `ROADMAP.md` current.

## Boundaries

- Demo data is synthetic mock only. No real ports/IPs/keys/credentials ever.
- No `.env`, wallet files, or secrets committed.

## Dependencies

- `anime.js v3.2.2` vendored at `demo/v0.1/lib/anime.min.js`. Pinned.

## Config / Error Handling / Troubleshooting

See `AGENTS.md` - identical content. Key gotchas: anime.js silently skips missing targets; headless shots need `page.waitForTimeout`; fonts fall back to system mono in CI.