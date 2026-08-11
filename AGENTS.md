# AGENTS.md — Semi Hub

## Project purpose
Semi Hub is a public AI hardware and semiconductor research atlas hosted on GitHub Pages.
The SuperNode module is a beginner-readable but investor-useful map of AI rack-scale / supernode infrastructure.

## Non-negotiable rules
1. Preserve the existing public URL `diagram002.html`; do not break old shared links.
2. The site remains static HTML + JSON + Markdown and must work on GitHub Pages without a build step unless explicitly approved.
3. Keep public and private research layers separate:
   - S1 = official vendor / standards / primary-source facts: may be published.
   - S2 = expert calls / channel checks / supply-chain interviews: do NOT publish exact sensitive claims by default.
   - S3 = DaisyPKU's own BOM, value, exposure and investment inference: publish only high-level framing, not proprietary assumptions.
4. Never assert an undisclosed supplier/customer relationship from inference alone.
5. Do not convert protocol maxima or generic accelerator counts (e.g. “1024”) into a fixed BOM without a named implementation.
6. When comparing FLOPS/PFLOPS, state precision and dense/sparse basis where relevant.
7. For SuperNode work, distinguish Scale-up from Scale-out. NVLink, RoCE, InfiniBand and UALink are not interchangeable.
8. Company nationality is not the same thing as supply-chain exposure. Use architecture/exposure labels rather than country-only labels.
9. Maintain source provenance. Public factual claims should link to primary sources whenever practical.
10. Before changing public research content, read `docs/CODEX_HANDOFF.md`.

## Current public structure
- `/README.md` — repository navigation and live-map links
- `/diagram002.html` — legacy CCL / PCB / packaging / optics map; preserve URL
- `/supernode/index.html` — SuperNode Hub
- `/supernode/data/topologies.json` — public topology facts + qualitative research framing
- `/supernode/data/companies.json` — public company passports
- `/supernode/data/value_map.json` — public 1–5 structural value-intensity framework

## Current version
SuperNode Hub v0.4 (2026-08-11).

## Validation
For changes to `/supernode/`:
- Validate JSON syntax for every changed JSON file.
- Serve the repository root with a local static HTTP server.
- Confirm `/supernode/` and all JSON fetches return HTTP 200.
- Check mobile layout as well as desktop.
- Do not merge placeholder or demo data into main.

## Working style
Prefer small, reviewable commits. For meaningful revisions, update the visible version number and the handoff changelog.

