# BNet

A custom **GE-Proton11-7 ARM64** compatibility tool for Battle.net games on Linux, using matching Wine and FEX changes from GameNative. It installs alongside other Steam compatibility tools.

**[Download BNet1 for Linux ARM64](https://github.com/mrdidit/bnet-arm/releases/download/BNet1/GE-Proton11-7-Bnet1-arm64.tar.gz)** · [Download checksum](https://github.com/mrdidit/bnet-arm/releases/download/BNet1/GE-Proton11-7-Bnet1-arm64.tar.gz.sha256) · [Experimental release notes](https://github.com/mrdidit/bnet-arm/releases/tag/BNet1)

## Status

**Diablo II: Resurrected and Diablo III** reached gameplay on a **KONKR Pocket FIT Elite, Snapdragon 8 Elite (SM8750)** running Armada `20261018.30ef88c`. Longer-term stability and other games or devices remain unverified. The tool has no KPFE-specific installation restriction; it requires a compatible Linux ARM64 Steam environment.

See [validation and known limitations](VALIDATION.md) for the scope of testing.

Both games reached gameplay with Armada's **global Default** and **global Custom (Fast with TSO enabled)** settings. These were global setting changes, not per-game preset changes.

## Installation

1. Download the complete tool and its checksum using the links above.
2. Verify the checksum and extract the archive into `~/.local/share/Steam/compatibilitytools.d/`.
3. Restart Steam and select **GE-Proton11-7-Bnet1 (ARM64)** in the Battle.net shortcut's compatibility settings.

Keep the existing Battle.net installation and prefix. No Python installer is needed. [Full installation, requirements and rollback](INSTALL.md).

The `.tar.gz` extracts to one `GE-Proton11-7-Bnet1-arm64` folder. Source archives are developer downloads for rebuilding and redistribution; they are not needed to install the tool.

### Armada FEX settings

Affected Armada versions can ignore a non-Steam shortcut's FEX preset and apply the global settings instead. BNet1 does not fix that separate routing issue. Keep a known-working configuration; a required BNet-specific preset has not been established. [Details](INSTALL.md#armada-fex-settings).

## Credits and sources

The original Blizzard compatibility fixes are by **Dmage22**. **GameNative** integrates those fixes with contributions from **tarikbc** and **Utkarsh Dalal**. BNet rebuilds the matching components for Linux ARM64 on **GloriousEggroll's GE-Proton**, retaining Wine, FEX and other upstream notices.

[Source pins and attribution](SOURCES.md) · [Build information](BUILD.md) · [Licenses](LICENSES.md)

Maintained by **mrdidit**.
