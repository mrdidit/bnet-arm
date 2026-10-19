# BNet1 experimental validation — 19 October 2026

BNet is a Linux ARM64 compatibility tool based on GE-Proton11-7. The release refresh preserves the runtime payload tested on 18 October; documentation, provenance and their checksums are updated. The stable tool identity is `GE-Proton11-7-Bnet1-arm64`, displayed as **GE-Proton11-7-Bnet1 (ARM64)**.

## Device test scope

D2R gameplay was reported on 18 October 2026 on KPFE (Snapdragon 8 Elite) running Armada `20261018.30ef88c`, boot `cca7b910-ae32-4eb8-a473-5539dac97abd`. Steam's saved selection identifies BNet. Launcher logs record D2R launching and `gameRunning=1` at 19:55 UTC. The earlier D2R process was not captured, so its loaded binaries, effective FEX configuration and gameplay duration were not independently measured. A later Battle.net setup process loaded the expected patched Wine ntdll and matching WOW64 FEX DLL/UnixLib hashes.

This is a reported gameplay milestone with separate launcher/runtime verification. Long-term stability, other Battle.net games and other hardware/distributions have not received game validation. The package does not impose a KPFE or Steam Frame restriction. The build requires an ARMv8.2-A compatible CPU, compatible Steam ARM64 runtime (app ID `4185400`) and working graphics support.

## FEX preset routing

On the affected Armada build, `armada-game-launch` selected `STEAM_COMPAT_APP_ID=0` before valid `SteamAppId=3609908584`. It therefore generated global FEX settings instead of the shortcut's per-game settings. The reported UI selection of Default, and the reported launcher failures with Fast/Custom, do not establish an effective working preset or isolate a TSO toggle. The earlier D2R launch's exact environment was not captured.

Per-game FEX settings may be ignored on affected Armada versions; global settings are used. No BNet FEX preset has been proven. Keep the known-working configuration and close Battle.net before controlled changes. This release does not alter settings or repair Armada's routing.

A read-only check on 19 October, on the same Armada image, found the Battle.net background `Agent.exe` using the generated global configuration: TSO on, Half Barrier TSO off, Vector/Memcpy TSO off, multiblock on and reduced x87 precision on. This matches global Custom configured as Fast plus TSO. The shortcut still had Default saved. The running agent loaded the BNet Wine/WOW64 FEX libraries. No D2R process was captured in this check; these current agent settings do not establish the earlier gameplay configuration or a required preset.

## Console integration and retained limitations

Fresh-prefix x64 and x86 console fixtures passed on the local Steam Frame build host on 18 October: executable-section aliases returned `42 then 43` after the direct ntdll `NtFlushInstructionCache` callback, with exit code 0. The same standalone fixture crashed on first execution with the clean stock GE control. Prefix ntdll/FEX hashes and links matched the built components.

The Win32 `FlushInstructionCache` fixture returned stale `42 then 42` on BNet; the exercised local Wine route is a no-op. The passing direct-callback test does not resolve that limitation. An earlier ordinary Steam-helper console startup timed out without fixture output; standalone console testing passed. These fixture results have their own scope and do not establish universal Steam or game compatibility.

## Package and source integrity

The tested 18 October runtime archive has SHA256 `3d454142e4f8fde0803a5f16633459b2603cba595ce2e0b870abaf9d24b8f904` and size 648,170,861 bytes. Its extracted checks verified 7,888 listed regular files and 1,884 symlinks; installation on KPFE repeated the file and link-boundary checks before activation.

The refreshed release is compared member by member with that archive. Permitted changes are `bnet/BUILD.json`, `bnet/INSTALL.md`, `bnet/SOURCES.md`, `bnet/SHA256SUMS`, and the addition of `bnet/VALIDATION.md`. Runtime bytes, modes, symlink targets, tool identity and ARM64 runtime metadata must remain identical. The five replacement component hashes remain:

| File under `files/lib/wine/` | SHA256 |
| --- | --- |
| `aarch64-windows/ntdll.dll` | `e28f25f21ecf34a32ee2ce24672f023e436da08a88a01c6d4e93757633c9ba47` |
| `aarch64-windows/libarm64ecfex.dll` | `27e2b27b7c11e847ac4687614ebcedc02854938427b43eefb5e64b099bad2733` |
| `aarch64-windows/libwow64fex.dll` | `6ea8765fdc9436e44020fba1af2b389bafaab0cbd542939ca43f0cc4171b8d51` |
| `aarch64-unix/libarm64ecfex.so` | `fa41dfc7857d6cfe3cc07e3aa948ee710a3a771b59c2deaab81931298e287b11` |
| `aarch64-unix/libwow64fex.so` | `df8e7e0da785421714faf9d7b75346536643afc768ac905f457c33b9ebfde216` |

The component-source archive includes actual prepared Wine/FEX trees, the three unchanged Wine ntdll patches and four unchanged FEX patches, build recipes, release metadata, records and license notices. The optional sechost workaround is included but unapplied. Two unchanged GE source archives accompany it. Original component build records retain their historical validation scope; this document records later testing. Archive checksums are supplied in `SHA256SUMS`. Independent byte-for-byte reproduction of binary builds has not been tested.
