# Heimdall Community Profiles

Heimdall 的官方精选 Profile 目录。这个仓库独立于 Heimdall 应用源码仓库，
只保存静态 `catalog.json`、预览图和发布说明；自包含 `.heimdall-profile`
文件通过 GitHub Releases 分发。

The official curated Profile catalog for Heimdall. This repository is independent
from the Heimdall application source repository. It contains only the static catalog,
preview images, and documentation; self-contained `.heimdall-profile` bundles are
distributed through GitHub Releases.

## 当前范围 / Current scope

- 由 Heimdall 维护者审核和发布，暂不开放应用内上传。
- 不需要账号、后端服务器、数据库、点赞、评论或在线编辑。
- 每个下载项包含准确的字节大小与 SHA-256；Heimdall 校验后才调用现有
  Profile importer。
- 一个 Profile 可以按顺序声明多个镜像，所有镜像必须提供完全相同的文件。
- Catalog 获取失败时，Heimdall 可以继续显示上次成功获取的本地缓存。

## Profiles

| Profile | Platform | Notes |
| --- | --- | --- |
| GBA - 千年家族 | RetroArch (`com.retroarch.aarch64`) | 4 macros, 5 layout modules |

## Repository layout

```text
catalog.json
previews/
  gba-sennen-kazoku.jpg
```

Profile bundles are attached to Releases and are intentionally not committed to the
default branch.

## Integrity

The first bundle passed a structural audit before publication: schema 1, one Profile,
six content-addressed assets, matching manifest and entry hashes, and no external HTTP,
`content://`, `file://`, `/storage/`, or email references in `profiles.json`.

The repository does not grant a blanket license for third-party game names, artwork,
logos, or other bundled media. Their respective rights remain with their owners.
