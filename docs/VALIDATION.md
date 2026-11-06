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

A local HTTP smoke check also passed for HTML, both stripped JavaScript modules, syntax, and the asset allowlist.

## Observed CI result

Passed: [target-platform build/check](https://github.com/netcodermike/local-whiteboard-studio/actions/runs/42204015675). Source commit: `12f044f453793d8fa4a114e33e16af0a003f429c`. Later documentation-only changes do not alter the tested implementation. The reproducible commands above identify test scope; native GUI/audio/permissions are not implied by compilation.
