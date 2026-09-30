# Heimdall Community Profiles

Heimdall 的官方精选 Profile 目录。这个仓库独立于 Heimdall 应用源码仓库，
只保存静态 `catalog.json`、Profile 图标、主页截图和发布说明；自包含 `.heimdall-profile`
文件通过 GitHub Releases 分发。

The official curated Profile catalog for Heimdall. This repository is independent
from the Heimdall application source repository. It contains only the static catalog,
Profile icons, home screenshots, and documentation; self-contained `.heimdall-profile` bundles are
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
| 千年家族 | RetroArch (`com.retroarch.aarch64`) | 4 macros, 5 layout modules |
| 恶魔城：月下夜想曲 | PSP | 7 macros, 6 layout modules |
| 火焰之纹章：圣魔之光石 | GBA | 4 macros, 5 layout modules |
| 星之卡比：镜之大迷宫 | GBA | 7 macros, 5 layout modules |
| 空之轨迹 1st | Game | 6 macros, 7 layout modules |
| Delta Force | Android 游戏 | 8 macros, 4 layout modules |
| PS2 通用 | PS2 | 10 macros, 5 layout modules, maps and guide |
| 燕云十六声 | Android 游戏 | 6 macros, 5 layout modules |
| PSP 通用 | PSP | 4 macros, 5 layout modules |
| GBA 通用 | RetroArch (`com.retroarch.aarch64`) | Translation, 3 macros, 5 layout modules |

## Repository layout

```text
catalog.json
icons/
  gba.png
  ...
previews/
  gba-sennen-kazoku.jpg
  ...
screenshots/
  gba-sennen-kazoku.png
  ...
```

`icon` is the Profile's own `iconUri` asset extracted unchanged from its bundle and
is the only remote image used by the compact navigation list. When it is missing,
Heimdall uses a local initial fallback; it never substitutes `preview` or another
image from the Profile. `screenshot` provides the separately curated complete
Heimdall Profile home-page image. `preview` remains optional legacy discovery
metadata. Assets may declare exact byte size and SHA-256 metadata; Profile ZIP
contents and import behavior remain independent.

Profile bundles are attached to Releases and are intentionally not committed to the
default branch.

## 自行维护 Catalog

维护者可以直接在 GitHub 网页或本地编辑 `catalog.json`。只修改名称、作者、
类别、副标题或描述等展示信息时，不需要重新打包 Profile，也不需要发布新版
Heimdall；保存后在 Heimdall 中刷新目录即可获取更新。

- 保持 `id` 稳定，避免同一条目被识别为新的 Profile。
- `minVersionCode` 是实际兼容性门槛；`minHeimdallVersion` 是展示给用户的版本文字。
- 修改图标、主页截图或 Profile 文件时，先上传新文件，再同步更新对应 URL、
  字节大小和 SHA-256。
- Profile 文件应先发布为 Release asset，再让 catalog 引用；不要静默覆盖同名
  Release asset。

## Integrity

The first bundle passed a structural audit before publication: schema 1, one Profile,
six content-addressed assets, matching manifest and entry hashes, and no external HTTP,
`content://`, `file://`, `/storage/`, or email references in `profiles.json`.

The repository does not grant a blanket license for third-party game names, artwork,
logos, or other bundled media. Their respective rights remain with their owners.
