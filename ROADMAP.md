# COMMAND CENTER - Roadmap

Status: **Phase 0 (UI/UX RnD)** - iterating demo v0.1

## Phase 0 - UI/UX RnD (current)

**Goal:** Lock the visual language & interaction model so Ravi can say "sreg" before any backend work.

- [x] 0.1 Brainstorm - reference hunting (Vercel/Linear/dark ops galleries), defined the vibe
- [x] 0.2 Build demo v0.1 - monochrome mission-control mock with anime.js (bento cards, side nav, event feed, command palette)
- [ ] 0.3 Ravi reviews v0.1 -> feedback loop (update demo, iterate)
- [ ] 0.4 Lock tokens (colors/type/spacing/motion) in DESIGN-NOTES as the source of truth
- [ ] 0.5 Decide layout paradigm: A) bento overview, B) sidebar+detail, C) event-centric, or combo -> fix in demo

**Exit criteria:** Ravi picks a layout direction and says the aesthetic "sreg". DESIGN-NOTES frozen at v1.0.

## Phase 1 - Specification (SPEC.md)

**Goal:** Translate the approved demo into a buildable spec (SDD workflow).

- [ ] 1.1 Inventory every tool/system to be controlled (farms, proxies, gateways, VPS, shop tools)
- [ ] 1.2 Define data sources per tool (health endpoints, APIs, SSH, scrapers, files)
- [ ] 1.3 Define action model (restart service, run script, toggle, deploy) + auth model
- [ ] 1.4 Write SPEC.md + TASKS.md (English, per ravi-spec-driven-development)

**Exit criteria:** Ravi approves SPEC.md v1.0.

## Phase 2 - MVP skeleton (functional shell)

**Goal:** Working app shell with real navigation, mock data behind an API layer.

- [ ] 2.1 Tech stack decision (FastAPI/uvicorn + static, or Node) based on ops-console-ui patterns
- [ ] 2.2 API contract for status aggregation (per-tool health probe endpoints)
- [ ] 2.3 Real nav/routing, command palette wired to real navigation
- [ ] 2.4 Login/auth (Ravi preference: Google OAuth or simple token gate)

**Exit criteria:** Demo renders real per-tool status pulled from live endpoints.

## Phase 3 - Read-only control plane

**Goal:** See everything, everywhere, one pane of glass.

- [ ] 3.1 Per-tool status cards with real data (9router, farms, proxy pool, VPS fleet, shop tools)
- [ ] 3.2 Event feed aggregating real logs/notifications
- [ ] 3.3 Live metrics (keys, quota, egress IP, job progress) via SSE/websocket

**Exit criteria:** Every tracked tool has a live status card + event stream.

## Phase 4 - Full control plane (v1)

**Goal:** Act from the console: restart, run scripts, toggle, deploy, cron view.

- [ ] 4.1 Action execution with confirmation + audit log
- [ ] 4.2 Cron/job scheduler view
- [ ] 4.3 Deploy hooks (cloudflare workers, tunnel restarts)
- [ ] 4.4 Alerting to Telegram notification topic on failures

**Exit criteria:** Ravi can run his daily ops from one URL.

## Phase 5 - Polish

- [ ] 5.1 Mobile responsive pass
- [ ] 5.2 Performance pass (bundle, animation throttle, reduced-motion)
- [ ] 5.3 Theme variants (light mode?) if wanted

---

## Decisions log (why)

| Date | Decision | Reason |
|------|----------|--------|
| 2026-08-24 | Full control plane (option 3), not just monitoring | Ravi chose; scope = monitor + act |
| 2026-08-24 | High-tech modern monochrome aesthetic | Ravi's stated taste: monochrome + modern font |
| 2026-08-24 | anime.js as motion layer | Ravi explicitly requested anime.js |
| 2026-08-25 | Demo-first, static HTML, no backend yet | UI/UX RnD phase; iterate visuals before stack |