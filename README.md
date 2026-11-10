# UniXNU-sm8750-common

Shared Qualcomm SM8750 (Snapdragon 8 Elite) support for [UniXNU](https://github.com/UniXNU/UniXNU) device repositories.

**This repository is a placeholder.** The SoC-common split has not happened yet. Device-specific and still-entangled SoC work for the Xiaomi Pad 8 Pro lives in [lenzhang/UniXNU-piano](https://github.com/lenzhang/UniXNU-piano). Code will move here once that layer is stable, following the same layout as [UniXNU-sm8550-common](https://github.com/UniXNU/UniXNU-sm8550-common).

Until then, piano's *build* still pins the existing upstream SoC module [IssacL04/UniXNU-sm8750-common](https://github.com/IssacL04/UniXNU-sm8750-common) via `UniXNU-piano/feeds.toml`. Do not change that pin to this repository, and do not treat this tree as a fork or a drop-in replacement.

Project-wide conventions: [UniXNU-piano/docs/PROJECT-MAP.md](https://github.com/lenzhang/UniXNU-piano/blob/main/docs/PROJECT-MAP.md) (a copy is in [docs/PROJECT-MAP.md](docs/PROJECT-MAP.md)).

## 中文摘要

本仓库是骁龙 8 至尊版（SM8750）的公共层占位。设备专属内容以及尚未拆分的芯片代码目前都在 [`UniXNU-piano`](https://github.com/lenzhang/UniXNU-piano)。稳定后再按 UniXNU-sm8550-common 的布局迁过来。当前构建仍钉住上游 `IssacL04/UniXNU-sm8750-common`，在拆分完成前不要改 pin。

## Planned layout

| Path | Planned contents |
| --- | --- |
| `soc.toml` | SoC profile and component selection |
| `configs/` | Kernel configuration fragments shared by SM8750 boards |
| `dts/sm8750.dtsi` | Shared hardware: CPU topology, GIC, memory map, UFS/SMMU, clocks |
| `patches/xnu/series` | Ordered XNU / kernel SoC patches |
| `kits/Sm8750Platform/` | UEFI and XNU SoC drivers (CPU, interrupt controller, memory, shared peripherals) |

Board-specific material stays in the device repository: panel, touch, charging, keys, DTS overlays, ADT, boot-image packaging, and RAM-boot scripts.

## Hard rules (same as the project map)

RAM boot (`fastboot boot`) only. Never flash, erase, or otherwise write partitions. No vendor firmware blobs, partition dumps, or Apple IPSW-derived payloads in this tree. No passwords, tokens, or home-LAN inventory in files or history.
