# Repository audit — 2026-10-10

## Baseline

The checked-out `arena/85974831-ash` branch and `origin/main` contain a single tracked file, `README.md` (`# ASH`). The expected Next.js, Tauri, Rust, API, provider, storage, test, and packaging files are not present. The remote has no other branch or tag containing application source. No `.env` or database contents were inspected.

| Area | Behavior reproducible from this checkout | Risk / blocker | Safe next action |
|---|---|---|---|
| Chat, Cowork, Computer UI and APIs | No application code or `package.json` exists, so none can be launched or tested. | A desktop build would have no application to package; adding a mock would misrepresent Cowork as working. | Restore/push the actual application source before implementing or validating these flows. |
| Task workspace, tools, streaming, persistence and export | No task store, tool adapters, routes, tests, or export code exists. | Cannot establish task/file safety, cancellation, checkpointing, or valid artifacts. | Audit the real implementations and add focused tests once present. |
| Local PC access, Tauri IPC and shell | No `src-tauri` directory or native code exists. | Cannot verify workspace-boundary enforcement, command confirmation, IPC permissions, or process cancellation. | Do not ship or claim native computer/shell capabilities until audited and tested. |
| Providers, voice, memory and settings | No provider, voice, learning, or settings modules exist. | No real model configuration or Cowork capability is available to the user. | Restore source; keep keys out of source and installer. |
| Windows packaging and downloads | No package manifest, Tauri configuration, workflow, or build guide exists. | No setup executable can be produced from this checkout; there is no release artifact to download. | Add packaging only after the actual app is restored; build from a clean checkout and publish the installer as a private release/artifact if access must be restricted. |
| Repository privacy and local data | GitHub metadata currently reports this repository as public; this checkout contains no `.gitignore`. | A public repository is not a private download channel, and future local keys/databases could be staged accidentally without ignore rules. | Add conservative local-secret/database/build ignores. Repository visibility is not changed here. |

## Baseline commands

- `npm ci` — failed (exit 1): no `package-lock.json` or `npm-shrinkwrap.json`.
- `npm run typecheck` — failed (exit 254): no `package.json`.
- `npm run lint` — failed (exit 254): no `package.json`.
- `npm run build` — failed (exit 254): no `package.json`.

These are repository-content blockers, not application test failures. No application behavior, Windows packaging, or installer has been claimed as tested.
