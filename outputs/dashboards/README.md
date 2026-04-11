# Static HTML dashboards

These are **single-file, no-build** pages you open in a browser (`file://` or any static host). They mirror Cadence rituals and knowledge — **not** live calendar/email (that needs MCP + a generator or app).

| File | Purpose |
|------|---------|
| `cadence-hub.html` | Home screen: commands, links into the repo, links to other dashboards |
| `goals-scorecard.html` | 90-day goals + weekly focus (aligns with `living-brain.md`) |
| `claims-board.html` | Core claims as cards (aligns with `knowledge/03_projects/core-claims.md`) |

## How to use

1. Double-click an `.html` file, or right-click → Open with browser.
2. **Markdown links** (e.g. `../../CLAUDE.md`) open depending on your OS; use **Cursor / File Explorer** for `.md` if the browser does not render them.
3. Refresh content anytime: edit by hand, or ask Claude to **regenerate** from your latest `context/` and `knowledge/` files.

## Optional: GitHub Pages

Copy `outputs/dashboards/` into a Pages branch or `/docs` if you want a public URL. Do **not** publish `context/` or `memory/`.
