# Local Whiteboard Studio

Sketch with pen, lines, and rectangles across layers, undo edits, save projects locally, and export flattened PNG images.

[![Build and verify](https://github.com/netcodermike/local-whiteboard-studio/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/local-whiteboard-studio/actions/workflows/verify.yml)

**Language:** TypeScript · **Platform:** Windows, macOS, Linux; modern browser · **App type:** Layered drawing web app

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- 1200 × 800 drawing canvas with color/width controls and three drawing tools.
- Up to 12 layers, visibility controls, deletion/clear, and 30 undo states.
- Browser-local save/load and portable JSON import/export.
- White-background PNG export of visible layers.

## Requirements

Node.js 24.12+ and a browser. No npm dependencies. The server strips supported TypeScript syntax for browser modules.

## Quick start

```sh
git clone https://github.com/netcodermike/local-whiteboard-studio.git
cd local-whiteboard-studio
node server.ts
# Visit http://127.0.0.1:3020
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Sketch a shape on Layer 1, add another layer, and draw a rectangle. Hide/show a layer, undo and redo an edit, save in the browser, export a project, and import it again. PNG export contains only visible layers.

## Architecture, configuration, and data

`model.ts` defines and validates version-1 boards, layers, strokes, and bounded points. Edits return cloned validated state. `app.ts` owns pointer interaction, layer controls, undo/redo, canvas rendering, localStorage, and downloads. `server.ts` serves an allowlist of three assets and strips TypeScript with node:module. Modules use browser .js import paths. The listener is 127.0.0.1:3020; PORT changes it. Boards are limited to 12 layers, 10,000 strokes, and 100,000 total points; imports are capped at 10 MiB. One saved board is stored per browser origin; JSON is the portable format. Tests cover immutable edits, visibility, serialization, and invalid data.

## Verification

Build with the quick-start command where needed, then run:

```sh
node --test test.ts
```

Manual acceptance: Exercise all tools, pointer drag/cancel, layer visibility/deletion, undo/redo, browser save/load, JSON import/export, and PNG output. Confirm invalid JSON does not replace the board.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

Local single-user drawing only: no collaboration, eraser, text, layer reordering/renaming, zoom, pan, autosave, pressure, or vector export. PNGs are flattened with a white background; JSON preserves editable strokes/layers. Pointer input is required for drawing. Undo snapshots consume memory and are limited to 30. Storage quotas may reject large saves. Refreshing loses unsaved edits.

## Troubleshooting

Run the server rather than opening the HTML file directly. Node versions without native type stripping are unsupported. An occupied port can be changed with PORT. Browser saves are tied to origin/port/profile. Import validation errors leave the current board intact. Hidden layers cannot be painted until shown.

## Source map

- `app.ts`
- `model.ts`
- `package.json`
- `server.ts`
- `test.ts`
- `public/index.html`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
