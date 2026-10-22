# GP Browser

A Chromium fork aimed at two things:

- **Full Chrome Web Store support** — extensions install and update normally, with
  Manifest V3 kept intact instead of being restricted the way some Chromium builds do.
- **A disk-backed tab engine (in progress)** — idle tabs are parked as rows on disk
  rather than held by a renderer process, so very long sessions stay usable.

Status: private build, used daily. The MV3 tab-suspender work is complete and the
fork builds and passes smoke tests; the tab engine is still being written.

## What is in this repository

Only documentation. The browser itself is a Chromium build (~1.1 GB per snapshot), so it is
**not** hosted as a download. See [REVISIONS.md](REVISIONS.md) for all 59 local build snapshots,
the 9 Chromium manifests and the build log history.

## Rebuild it locally

The engine comes from Chromium itself; this project supplies the patches on top.

1. Install `depot_tools` and add it to `PATH` — the official instructions live on the
   [Chromium "Get the Code" page](https://chromium.googlesource.com/chromium/src/+/main/docs/get_the_code.md).
2. Fetch the source at the pinned stable tag: `fetch --nohooks --no-history chromium`,
   then `gclient runhooks`. The tags used by the local builds are `150.0.7871.182` …
   `150.0.7871.190`, listed in [REVISIONS.md](REVISIONS.md).
3. Apply the GP patches, keep `enable_extensions = true` in the GN args, then
   `gn gen out/Dev` and `autoninja -C out/Dev chrome`.

If you only need a prebuilt Chromium binary rather than building one, Google publishes those
on the [Chrome for Testing download page](https://googlechromelabs.github.io/chrome-for-testing/).

## Why there is no Chromium source here

Chromium is ~40 GB of code; it is fetched with `depot_tools` and patched locally.
This repository documents the fork and its build configuration, not the upstream
checkout. Chromium itself remains under its own BSD 3-Clause licence — nothing here
relicenses it.

MIT licensed for the original parts — see [LICENSE](LICENSE).
