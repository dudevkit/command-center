# Command Center

Unified control plane concept ("pusat dari segala pusat") for a farming/proxy/ops toolchain. Currently in **UI/UX RnD phase** - a high-tech monochrome dark ops console with an anime.js motion layer, before any backend decisions.

Live demo: **[v0.1](https://dudevkit.github.io/command-center/demo/v0.1/)**

## Structure

- `demo/v0.1/` - static HTML/CSS/JS demo (anime.js vendored). Open directly or run `python3 -m http.server`.
- `ROADMAP.md` - phased plan (UI RnD -> spec -> MVP skeleton -> control plane).
- `RND-LOG.md` - trial-and-error log of the RnD process.
- `DESIGN-NOTES.md` - design tokens, layout, motion spec (source of truth for the look).

## Direction

Brutally minimal monochrome ops console. Linear/Vercel dark reference. Zinc stack, Inter + IBM Plex Mono, cyan accent used sparingly, pill status badges, mono type for all data. Motion via anime.js (entrance stagger, number tickers, live pulse, feed streaming) - motivated only.

All mock data is synthetic. No real infra values.
