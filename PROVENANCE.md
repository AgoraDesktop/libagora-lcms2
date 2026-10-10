# Provenance

This repository is an extraction of little CMS (lcms2) — the colour-management engine — at a pinned
revision. `libagora-drawing` (Core Graphics) uses it for `CGColorSpace` and the colour-conversion
paths.

| | |
|---|---|
| Upstream repository | https://github.com/mm2/Little-CMS |
| Upstream revision | `lcms2.19.1` |
| Upstream commit | `21c582a594fe5279f90c0b93437c398f93bf62b0` |
| Upstream commit date | 2026-05-06 |
| Extraction | the upstream repository root, placed at this repository's root |
| Extraction date | 2026-10-10 |
| Source changes by Agora | none |

## What was copied

The whole upstream tree at the pinned revision (335 files) — `src/`, `include/`, `cmake/`, `utils/`,
`plugins/`, `Projects/`, `testbed/`, `doc/`, `fuzzers/`, `Lib/`, the autotools files, `meson.build`,
`CMakeLists.txt`, `lcms2.pc.in`, `LICENSE` and `README.md`.

Dropped: only VCS and CI metadata — `.git/`, `.github/`, `.gitignore`, `.gitmodules`, `.mailmap`.
Agora supplies its own `.gitignore`, and upstream's `README.md` is kept as `UPSTREAM-README.md` so
this repository can carry its own `README.md`.

Upstream already installs a CMake package (`cmake/lcms2-config.cmake.in` → `lcms2-config.cmake`) and a
pkg-config file (`lcms2.pc`), so `find_package(lcms2 CONFIG)` works without changes.

## Why this revision

`lcms2.19.1` is the exact revision the Fiwix tree vendors — the same commit — so the Core Graphics
that `libagora-drawing` imports is built against the version it was written against. (`LCMS_VERSION`
is `2190` in that tree.)

## Licence and attribution

MIT, © 2023 Marti Maria Saguer. Upstream's `LICENSE` is retained verbatim and the per-file headers are
untouched. Agora's own additions to this repository fall under the project licence (see the top-level
project README).

## Keeping in sync

Updates re-extract from a newer upstream revision and record it in the table above. Because the tree
sits at the repository root, `git diff` against a fresh upstream checkout shows local divergence
directly.
