# GP Browser

A Chromium fork aimed at two things:

- **Full Chrome Web Store support** — extensions install and update normally, with
  Manifest V3 kept intact instead of being restricted the way some Chromium builds do.
- **A disk-backed tab engine (in progress)** — idle tabs are parked as rows on disk
  rather than held by a renderer process, so very long sessions stay usable.

Status: private build, used daily. The MV3 tab-suspender work is complete and the
fork builds and passes smoke tests; the tab engine is still being written.

## What is in this repository

Only documentation. The browser itself is a Chromium build (~1.1 GB per snapshot),
so the binaries live in [Releases](../../releases) instead of git. See
[REVISIONS.md](REVISIONS.md) for all 59 local build snapshots and the build log
history.

## Why there is no Chromium source here

Chromium is ~40 GB of code; it is fetched with `depot_tools` and patched locally.
This repository documents the fork and its build configuration, not the upstream
checkout. Chromium itself remains under its own BSD 3-Clause licence — nothing here
relicenses it.

MIT licensed for the original parts — see [LICENSE](LICENSE).
