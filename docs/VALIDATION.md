# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux; modern browser.

## Local result

Both model tests and Node syntax checks passed locally on Windows. Browser painting remains manual.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
node --test test.ts
node --check server.ts
node --check app.ts
```

## Manual acceptance

Exercise all tools, pointer drag/cancel, layer visibility/deletion, undo/redo, browser save/load, JSON import/export, and PNG output. Confirm invalid JSON does not replace the board.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.
