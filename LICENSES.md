# Licenses

BNet retains each component's upstream license. The MIT grant for original BNet build scripts is limited to the files listed in [BUILD-LICENSE.md](BUILD-LICENSE.md).

| Material | License and notices |
| --- | --- |
| Wine patch copies under `patches/wine/` | [LGPL-2.1-or-later](LICENSES/Wine-LGPL-2.1.txt); original patch authorship is retained |
| FEX patch copies under `patches/fex/` | [FEX MIT license and copyright notice](LICENSES/FEX-MIT.txt); original patch authorship is retained |
| GE-Proton build material, including the derived `wine-port/prepare-ge-wine.sh` in the source archive | [GE-Proton notice](LICENSES/GE-Proton-NOTICE.txt) and [BSD-3-Clause terms](LICENSES/GE-Proton-BSD-3-Clause.txt) |
| Ten original BNet build/packaging scripts | [MIT license](LICENSES/BNet-build-MIT.txt), with the exact [file scope](BUILD-LICENSE.md) |

The upstream texts are copied verbatim from the pinned Wine, FEX and GE-Proton source trees identified in [source-pins.json](source-pins.json). Component dependencies retain their separate licenses; the table does not relicense third-party code.

The runtime archive contains the base tool's licenses plus collected notices under `bnet/licenses/`. The release's three source archives contain the corresponding prepared component sources, unchanged GE sources, build recipes and license files. [Source information](SOURCES.md).

Redistribution must preserve the applicable notices and source obligations.
