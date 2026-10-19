# BNet1 — experimental

Standalone GE-Proton11-7 ARM64 compatibility tool for Battle.net games on Linux. Includes matching GameNative Wine/FEX changes rebuilt for Linux ARM64, alongside the unchanged GE-Proton runtime components.

Diablo II: Resurrected and Diablo III reached gameplay on KONKR Pocket FIT Elite (Snapdragon 8 Elite / SM8750), running Armada `20261018.30ef88c`. Both games reached gameplay with Armada's global Default and global Custom (Fast with TSO enabled) settings. These were global setting changes, not per-game preset changes; each gameplay process's effective configuration was not captured. Longer-term stability, other Battle.net games and other devices remain unverified.

## Install

Download `GE-Proton11-7-Bnet1-arm64.tar.gz` and its matching `.sha256`, verify the checksum, and extract the archive into `~/.local/share/Steam/compatibilitytools.d/`. Restart Steam and select **GE-Proton11-7-Bnet1 (ARM64)** for the Battle.net shortcut. No Python installer is needed.

[Installation and rollback](https://github.com/mrdidit/bnet-arm/blob/BNet1/INSTALL.md) · [Validation and limitations](https://github.com/mrdidit/bnet-arm/blob/BNet1/VALIDATION.md)

## Known limitation

Affected Armada versions may use global FEX settings instead of a non-Steam shortcut's selected preset. This separate Armada issue is not patched by BNet1. No required BNet-specific preset has been established.

## Credits and source

Original Blizzard compatibility fixes by **Dmage22**, integrated by **GameNative** with contributions from **tarikbc** and **Utkarsh Dalal**. Based on **GloriousEggroll's GE-Proton11-7**, Wine and FEX. [Source pins and attribution](https://github.com/mrdidit/bnet-arm/blob/BNet1/SOURCES.md).

The runtime, three source archives, checksums and current installation/validation notes are attached. Source archives are for rebuilding and redistribution; normal installation only needs the runtime archive and its checksum.
