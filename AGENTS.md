# Base44 Dev Environment

## Project Overview
Static HTML website — a collection of standalone tools (PDF converters, image compressor, notes app, QR code generator, TicTacToe, currency exchange, contact form). No backend, no framework, no build step required.

## Tech Stack
- Plain HTML/CSS/JS (no framework)
- Tailwind CSS via CDN (`https://cdn.tailwindcss.com`) + pre-built `src/output.css`
- `src/output.css` is already committed; no build needed to serve

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Served by `live-server` (Node) on port 3000 with live-reload on file changes
- No secrets or external credentials required
- The contact form posts to web3forms.com using a key hardcoded in `index.html`

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return 200
- Container healthcheck probes `http://localhost:3000/`

## Notes
- All tool pages are standalone `.html` files at the repo root
- `cc/` contains a currency exchange sub-app (its own index.html + script.js)
- `images/` contains static assets (SVGs, PNGs, logos)
