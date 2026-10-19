# Building BNet

The release includes the actual prepared component sources, build scripts and original patch files. Download these assets and verify them against the release's `SHA256SUMS`:

- `Bnet1-component-sources.tar.gz`
- `GE-Proton11-7-upstream-sources.tar.zst`
- `GE-Proton11-7-extras-sources.tar.zst`

The first archive contains the modified Wine/FEX sources and component build recipes. The other two preserve the sources for the unchanged GE-Proton components.

Extract the component archive into a build directory:

```sh
tar -xzf Bnet1-component-sources.tar.gz
cd Bnet1-component-sources
```

Follow `wine-port/README.md`, `fex-port/README.md` and `package/README.md` inside that directory. The prepared Wine tree already contains GE's patch preparation and the three selected GameNative ntdll patches; do not apply them twice. The FEX tree contains the four pinned GameNative patches.

The component builds used Linux ARM64 and llvm-mingw `20260616`, Clang `22.1.8`. The exact toolchain release and checksum are in `package/toolchain-release.json`. Build dependencies and commands are documented in each component recipe. Python is a build dependency; installing the completed compatibility tool only requires extracting its archive.

Packaging requires the clean upstream `GE-Proton11-7-aarch64.tar.gz` and the five newly built Wine/FEX files. `package/inputs.json` records the original input hashes; regenerate paths, component hashes and build records for a new build rather than reusing stale values. The supplied build records retain the original build-machine paths as historical provenance, not required installation paths.

The patch copies under this repository's `patches/` are for review. Source revisions, ordering and the optional, unapplied sechost workaround are described in [SOURCES.md](SOURCES.md).

Archive metadata is normalized by the packaging recipes. Independent byte-for-byte reproduction of the binaries has not been established. Rebuilt outputs require their own validation.
