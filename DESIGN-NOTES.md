# COMMAND CENTER - Design Notes (v0.1 draft)

Working design tokens for the control plane UI. **Not frozen yet** - evolves with Ravi feedback.

## Vibe

High-tech modern monochrome dark ops console. Brutally minimal, data-dense, calm. Inspired by Vercel/Linear dark + mission-control telemetry. NOT a landing page (no hero, no marketing copy, no glassmorphism blobs).

## Tokens

| Token | Value | Notes |
|-------|-------|-------|
| bg base | `#09090b` | page background |
| surface 1 | `#131316` | cards/panels |
| surface 2 | `#18181b` | nested/hover |
| border | `rgba(255,255,255,0.07)` | 1px hairlines |
| text primary | `#fafafa` | |
| text secondary | `#a1a1aa` | |
| text muted | `#52525b` | |
| accent | `#22d3ee` | cyan - sparingly (selection, active, live pulse) |
| ok | `#34d399` | status ok |
| warn | `#f59e0b` | status warn |
| danger | `#f87171` | status error |

## Type

- UI: Inter (400/500/600/700), fallback system-ui.
- Data/mono: IBM Plex Mono (400/500/600) for ports, numbers, IDs, timestamps, nav labels.
- Scale (desktop): 10-11px labels (tracking 0.08em), 13px body, 20-28px metrics.

## Spacing & shape

- 8px grid. Card radius 10px. Panel padding 14-18px.
- Cards = bordered surfaces, NOT heavy shadows. Elevation via border + subtle bg shift.

## Layout (v0.1)

```
+--------------------------------------------------------------+
| topbar: logo mark | COMMAND CENTER | clock | [ctrl k] refresh |
+--------+-----------------------------------------------------+
|        | KPI strip: 4 stat tiles (live count, keys, jobs, ....)|
| side   +-----------------------------------------------------+
| nav    | bento grid: per-tool cards (status pill, metric,     |
|        | sparkline, last event, mini-actions)                 |
| farms  +-----------------------------------------------------+
| proxy  | event feed (streaming rows) | active jobs (progress) |
| vps    |                                                      |
| shop   +-----------------------------------------------------+
+--------+                                                      |
| command palette overlay (ctrl+k)                              |
+--------------------------------------------------------------+
```

### Aesthetic pillars
1. Monochrome first - color ONLY for semantic state (ok/warn/danger/live).
2. Mono type for data = the "high-tech" signal. Proportional type only for labels/headings.
3. Hairlines over fills. The page should read as layered hairlines on near-black, not as colored boxes.
4. Motion: entrance stagger + live pulse + feed streaming. Motivated only. Reduced-motion respected.

## Motion spec (anime.js)

| Moment | Spec |
|--------|------|
| Page entrance | cards stagger translateY(14px)->0, opacity 0->1, duration 500-700ms, easeOutExpo, stagger 35ms |
| Number tickers | counter 0 -> N, duration 900ms, easeOutQuart, once on load |
| Live dot | scale 1->1.6 + opacity, loop 1.6s, only on 'live' dots |
| Event feed row | translateY(8px)->0 + fade, 400ms, easeOutQuad, on insert |
| Command palette | backdrop fade 150ms, panel scale 0.98->1 + translateY(-6px)->0, 250ms easeOutExpo;
| Progress bar | scaleX 0->N, 800ms easeInOutQuad on change |
| Hover (CSS transition) | card: border rgba(255,255,255,.07)->.14, 150ms; ghost button bg shift |

### Rules
- Animate ONLY transform + opacity (GPU-composited). Never top/left/width/height/box-shadow.
- `prefers-reduced-motion: reduce` -> disable entrance/loops, keep static layout.

## Interactions (v0.1)

- Ctrl+K (or button) opens command palette - searchable action list (navigate, run script, toggle).
- Cards hover -> border brighten + ghost action buttons appear.
- Side nav sections filter/suggest focus (mock in v0.1).
- Status pill: live / starting / error / stopped (reuse ops-console-ui semantics).

## Out of scope for v0.1

- Mobile responsive (desktop-first; min width ~1100px target).
- Real data integration (all numbers synthetic).
- Real actions (buttons are visual only).
- Light mode.