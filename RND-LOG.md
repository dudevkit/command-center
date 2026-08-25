# COMMAND CENTER - RnD Trial & Error Log

Fase UI/UX RnD. Semua percobaan, error, dan keputusan dicatat di sini (English untuk konsistensi file).

## 2026-08-24 - Brainstorm & direction

### What happened
- Ravi: mau bikin "pusat dari segala pusat" - satu kontrol panel untuk semua tools/sistem.
- Bingung istilah UI/UX ("ada di kepala tapi susah dituangkan").
- Alice gave vocabulary: command center, single pane of glass, control plane, homelab dashboard.
- Presented 3 layout paradigms: A) bento overview, B) sidebar+detail, C) event-centric.
- Clarify result: **full control plane** (monitor + act), **monochrome high-tech** aesthetic.

### Decisions
- Phase 0 = UI/UX RnD standalone, no tech stack discussion yet.
- Reference set: Vercel Geist, Linear, Railway, Resend, Unkey, Coolify, Komodo, Beszel, Axiom, Grafana playground.
- Font direction: Geist / Inter + mono (IBM Plex Mono, Geist Mono, JetBrains Mono).

## 2026-08-25 - Demo v0.1 build

### Environment facts
- Project location: `/mnt/alice-workspace/command-center/` (SMB -> F:\AliceWorkspace\command-center on PC).
- anime.js v3.2.2 vendored locally (17KB) - deliberately NOT v4 (API changed; v3 stable UMD works with plain `<script>`).
- Wrangler NOT authenticated on gateway -> deploy via GitHub Pages instead.
- Playwright chromium headless for smoke screenshots (installed in /tmp/cc-smoke).

### Build approach
- Single-file demo (`demo/v0.1/index.html`) + vendored anime lib. No build step, opens directly from disk.
- Layout: topbar -> left side nav -> bento stats grid + event feed + command palette overlay.
- Motion spec: entrance stagger (easeOutExpo), number tickers, pulse on live dots, feed slide-in, palette scale/fade.

### Trial / errors
1. **anime v4 vs v3**: v4 changed API to ESM + new syntax. Pinned v3.2.2 UMD for stability. (No error hit, proactive decision.)
2. **Headless fonts**: headless chromium has no Google Fonts by default -> screenshot uses fallback system mono. Acceptable for smoke shots; real browser renders Inter correctly.
3. **Deploy auth**: `wrangler whoami` -> not authenticated. Pivoted to GitHub Pages deploy (gh CLI authed as dudevkit).

### Feedback loop (next)
- v0.1 deployed to GitHub Pages: https://dudevkit.github.io/command-center/demo/v0.1/
- Waiting on Ravi's visual comments. Then adjust layout/tokens/motion/content. Bump to v0.2 in new folder.
- Headless browser smoke test NOT possible on gateway (storage policy bans Playwright/Chromium install without approval, and there's no browser binary). Used `node --check` for JS syntax + curl HTTP 200 + anime lib parse instead. Ravi evaluates visually in real browser.

### Gateway cleanup (unrelated, same session)
- Root was 90% full (699M free). Cleaned caches (apt/npm/uv/journal), stale /tmp, rotated Hermes logs + /var/log.hdd, stale backup mounts (~110M). With Ravi approval removed: /DATA/AppData (n8n/pihole/gowa), /opt/obscura, hcaptcha-practice/.venv. Now 83% (1.2G free).

---

## Template for future entries

## YYYY-MM-DD - <what>
### What happened
### Decisions
### Trial / errors
### Feedback loop