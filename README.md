# libagora-lcms2

**little CMS for Agora** — the colour-management engine (ICC profiles, colour transforms) that
`libagora-drawing` (Core Graphics) uses for `CGColorSpace` and the colour-conversion paths.

Agora is an installable desktop environment for Linux and BSD; see the project README in the parent
directory (`../README.md`).

## Provenance

Extracted from [Little CMS](https://github.com/mm2/Little-CMS). Upstream's own README is kept as
[`UPSTREAM-README.md`](UPSTREAM-README.md); the full record is in [`PROVENANCE.md`](PROVENANCE.md).

## Licence

MIT, © 2023 Marti Maria Saguer — see [`LICENSE`](LICENSE).

## Build

Build into `build/`:

```sh
cmake -S . -B build -DCMAKE_C_COMPILER=clang -DCMAKE_INSTALL_PREFIX=<prefix>
cmake --build build
cmake --install build
```

The build installs a CMake package (`lcms2-config.cmake`) and a pkg-config file, so a consumer uses
`find_package(lcms2 CONFIG)` with `-DCMAKE_PREFIX_PATH=<prefix>` — including `libagora-drawing`.
