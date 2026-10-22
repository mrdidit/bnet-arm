# BNet installation

BNet is an experimental Battle.net compatibility tool for Linux ARM64, based on GE-Proton11-7. On 19 October 2026, Diablo II: Resurrected and Diablo III reached gameplay on KPFE (Snapdragon 8 Elite), Armada `20261018.30ef88c`, with global Default and global Custom (Fast with TSO enabled) FEX settings. Long-term stability remains untested. [Validation details](https://github.com/mrdidit/bnet-arm/blob/main/VALIDATION.md).

The build requires an ARMv8.2-A compatible CPU, Steam's ARM64 runtime (app ID `4185400`) and working graphics drivers. Other compatible ARM64 hardware and distributions are supported in principle but have not received game validation. There is no KPFE or Steam Frame restriction.

## Installation

Download the [complete BNet1 tool](https://github.com/mrdidit/bnet-arm/releases/download/BNet1/GE-Proton11-7-Bnet1-arm64.tar.gz) and its [matching checksum](https://github.com/mrdidit/bnet-arm/releases/download/BNet1/GE-Proton11-7-Bnet1-arm64.tar.gz.sha256). The source archives are only needed for rebuilding or redistribution. In the download directory:

```sh
sha256sum -c GE-Proton11-7-Bnet1-arm64.tar.gz.sha256 &&
  mkdir -p "$HOME/.local/share/Steam/compatibilitytools.d" &&
  test ! -e "$HOME/.local/share/Steam/compatibilitytools.d/GE-Proton11-7-Bnet1-arm64" &&
  tar -xzf GE-Proton11-7-Bnet1-arm64.tar.gz -C "$HOME/.local/share/Steam/compatibilitytools.d"
```

Use the corresponding `compatibilitytools.d` directory if Steam is installed elsewhere. The command stops if the destination already exists; do not merge archives into an existing tool directory.

The `.tar.gz` is a gzip-compressed tar archive. The command extracts both layers in one operation, creating `GE-Proton11-7-Bnet1-arm64/` directly inside `compatibilitytools.d/`. Some archive viewers display `././@PaxHeader`; this is metadata for long filenames and symlink targets, handled automatically by `tar`.

Back up the Battle.net shortcut's Steam `compatdata` prefix before first launch with BNet. A Proton switch may update that prefix. Fully exit and restart Steam, then open the Battle.net shortcut's Properties → Compatibility and select **GE-Proton11-7-Bnet1 (ARM64)**. Keep the existing Battle.net installation, shortcut target and launch options. Installation is archive extraction; no separate Python installer is required.

## Armada FEX settings

On affected Armada versions, per-game FEX settings may be ignored and global settings used instead. No required BNet FEX preset has been proven. Keep the known-working configuration and close Battle.net before controlled settings changes. This release does not change FEX settings or fix Armada's settings routing.

On 19 October, a running Battle.net process was observed using global Custom settings equivalent to Fast plus TSO: TSO on, Half Barrier/Vector/Memcpy TSO off, multiblock and reduced x87 precision on. That observation verifies the Battle.net process's effective settings, but does not establish the gameplay configuration or a required preset for either game.

## Optional diagnostics

Logging is disabled by default. For one failed launch, prepend these environment settings to the shortcut's existing launch options:

```text
PROTON_LOG=1 WINEDEBUG=-all,+timestamp,+pid,+tid,err+all,warn+seh
```

If launch options are empty, use the complete line:

```text
PROTON_LOG=1 WINEDEBUG=-all,+timestamp,+pid,+tid,err+all,warn+seh %command%
```

Otherwise, preserve the existing command and `%command%`. On Armada, if `/usr/libexec/armada/armada-game-launch` is already present, keep that wrapper and its arguments. Other distributions do not need to add it.

Attempt one launch and close Battle.net after failure or after two minutes, whichever comes first. Stop earlier if the log reaches 20 MiB. Restore the original launch options immediately afterward. Retain that single `steam-*.log` from the home directory and record the game version, OS/image version, selected tool, effective FEX settings if known, and failure stage. Do not leave this capture enabled during extended gameplay.

## Rollback

Select the previous compatibility tool on the Battle.net shortcut. This restores the selected runtime; it does not undo changes inside the prefix. Restore the prefix backup if necessary. Keep BNet's directory until the previous setup launches successfully.

`bnet/BUILD.json` records input checksums, pinned sources and release metadata. `bnet/SHA256SUMS` verifies regular files from the tool root. Detailed test scope and limitations are in `bnet/VALIDATION.md`; source assets and attribution are in `bnet/SOURCES.md`. Existing tools and system FEX are not replaced.

Maintained by mrdidit. Original Blizzard fixes by Dmage22; GameNative integration and additional work by tarikbc and Utkarsh Dalal. Built on GE-Proton, Wine and FEX; original authorship and licenses are retained.
