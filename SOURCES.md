# BNet source distribution and attribution

BNet is maintained by mrdidit as a Linux ARM64 build and packaging project. The original Blizzard Wine fixes are by [Dmage22 in Wine PR #47](https://github.com/GameNative/proton-wine/pull/47). The [pinned GameNative FEX series](https://github.com/GameNative/FEX/blob/ae5b5a79d1ce63b9a7f2d624e38db8232d071865/gamenative/README.md#series) credits patch `0001` to eleven squashed commits from `Dmage22/FEX-D2`, branch `d2r/clean`; patches `0002` and `0003` are by tarikbc, and `0004` is by Utkarsh Dalal. [GameNative Wine PR #67](https://github.com/GameNative/proton-wine/pull/67) integrates the Wine fixes and gates non-image notifications on emulator support. GE-Proton, Wine, FEX and their dependency authors retain their respective authorship and licenses.

The runtime uses the clean official GE-Proton11-7 AArch64 archive, release asset `566991622`, SHA256 `b77ac906186568c2f3c66674b85c712b145ccf73ff2718a50dd7bf6248b67ba3`. `upstream-release.json` records that asset identity; `base-inspection.json` records its original tool and runtime metadata. The Steam tool identity remains `GE-Proton11-7-Bnet1-arm64`, displayed as **GE-Proton11-7-Bnet1 (ARM64)**.

## Required source assets

The [BNet1 release](https://github.com/mrdidit/bnet-arm/releases/tag/BNet1) accompanies the runtime with these actual source archives:

| Asset | Contents |
| --- | --- |
| `GE-Proton11-7-upstream-sources.tar.zst` | Exact GE source, non-FEX submodules, upstream component preparation, Wine-Mono and Gecko sources |
| `GE-Proton11-7-extras-sources.tar.zst` | Pinned extra component sources and locked Rust crates used by GE |
| `Bnet1-component-sources.tar.gz` | Prepared modified Wine/FEX source, required dependency sources, original patches, local build scripts, build records, release metadata and license notices |

The two GE archives contain the unchanged GE-Proton base and dependencies. Their SHA256 values are:

```text
62700f9eedaf153705193f2d72964f986eb56f45672ec86033a945cd4e89599f  GE-Proton11-7-upstream-sources.tar.zst
8a972f75e4ebc9eea5a874d69988d5a33a30265a2b7efa147c914762dde1f142  GE-Proton11-7-extras-sources.tar.zst
```

Wine preparation retains GE's patch order and applies the three central ntdll patches from GameNative PR #67 unchanged. The optional sechost workaround is retained as unapplied source. FEX uses the pinned GameNative `0001`–`0004` series unchanged on FEX-2610, with both translation DLLs and their matching Linux UnixLib pair. Component build records identify exact source revisions, ordered patch hashes, toolchains and outputs. This release refresh changes documentation and provenance only; it preserves the tested runtime payload.

## Build and license materials

Build the included prepared trees with `wine-port/build-components.py` and `fex-port/build.sh`. Source preparation scripts also reproduce the upstream pins and ordered patches. `package/README.md` describes packaging, including the release metadata arguments. Historical component records describe the checks at build time; `VALIDATION.md` gives the subsequent device-test scope. Independent byte-for-byte reproduction of the binary builds has not been tested.

The pinned [llvm-mingw 20260616 AArch64 toolchain](https://github.com/mstorsjo/llvm-mingw/releases/download/20260616/llvm-mingw-20260616-ucrt-ubuntu-22.04-aarch64.tar.xz) is an external build prerequisite with SHA256 `e7e5d135d93d3f2a3beaaea633a5b0e66ac75391a53feae654391913dd76102b`. `toolchain-release.json` records verified upstream asset metadata.

The runtime retains upstream GE notices and `bnet/licenses/` for replacement components and linked dependencies, including Wine, FEX and LLVM runtime notices. The source archives preserve their original license files and copyright headers. Redistribute these source and notice assets with the binary; unspecified branch links do not replace them.

The original BNet build and packaging scripts use the [MIT License with explicit file scope](BUILD-LICENSE.md). The 22 October 2026 component-source refresh adds licensing and provenance documentation only; all pre-existing archive entries remain unchanged. The runtime and both GE source archives retain their original checksums.
