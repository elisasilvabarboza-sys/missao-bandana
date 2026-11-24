# Repository Guidelines

## Project Structure & Module Organization

This repository contains a small browser game with no package manager or build system. `index.html` holds the game interface, styles, and JavaScript gameplay code. `manifest.webmanifest` defines its installable web app metadata. `sw.js` handles offline caching, and `icons/` contains app artwork. There is no separate test directory; keep new assets in a clearly named subdirectory.

## Build, Test, and Development Commands

There is no compile or bundle step. Serve the repository root locally so the service worker and manifest work as intended:

- `python3 -m http.server 8000` — start a local server at `http://localhost:8000`.
- `node -e "const fs=require('fs');new Function(fs.readFileSync('index.html','utf8').match(/<script>([\\s\\S]*)<\\/script>/)[1])"` — check the inline JavaScript parses.

Open the local URL in a browser and exercise keyboard and touch controls after gameplay changes. HTTPS is required for installation outside localhost.

## Coding Style & Naming Conventions

Use four-space indentation for new JavaScript and CSS, descriptive camelCase names for variables and functions, and lowercase kebab-case for new asset filenames. The current game is intentionally self-contained in `index.html`; keep edits focused and avoid adding dependencies or build tooling for small changes. Preserve Portuguese (Brazil) for player-facing text and `lang="pt-BR"` in the document.

## Testing Guidelines

No automated test framework or coverage requirement is configured. For changes to gameplay, verify movement, jumping, obstacle collisions, level transitions, win/loss overlays, and mobile controls in a browser. For manifest or service-worker changes, reload the page and confirm the app shell and icon load. Do not claim automated coverage unless a test suite is added.

## Commit & Pull Request Guidelines

No Git history is available here to establish existing commit conventions. Use short, imperative commit subjects (for example, `Add park level decorations`). Pull requests should describe the player-visible change, list manual checks performed, and include screenshots for visual updates. Mention any changes to offline behavior or installation metadata.

## Security & Configuration

Do not add credentials, private URLs, or user-specific data to the repository. Keep service-worker cache entries aligned with the files the game actually uses, and update its cache version when cached assets change.
