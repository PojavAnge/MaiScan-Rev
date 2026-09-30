<p align="center">
  <img src="assets/icon.png" width="128" alt="MaiScan Rev">
</p>

<h1 align="center">MaiScan Rev</h1>

<p align="center">
  <sub>Local offline song database · Cover recognition · Collection manager</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Platform: Android 6.0+">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Language: Kotlin">
  <img src="https://img.shields.io/badge/Framework-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white" alt="Framework: Jetpack Compose">
  <img src="https://img.shields.io/badge/Purpose-maimai%20DX%20Tool-E4007F?style=flat-square" alt="Purpose: maimai DX Tool">
</p>

<p align="center">
  <a href="README.md">简体中文</a> ｜ <b>English</b> ｜ <a href="README.ja.md">日本語</a> ｜ <a href="README.zh-TW.md">繁體中文</a>
</p>

---

> This app is a modified build of **MaiScan** — the original repository is
> **[Klta-kyo/MaiScan](https://github.com/Klta-kyo/MaiScan)**.

## What this is

**MaiScan Rev** is a **local, offline song database tool for maimai DX**, produced as a second-round
build on top of MaiScan. It currently supports:

| Feature | Description |
| :-- | :-- |
| **Cover recognition** | Photograph the jacket art on the **song-select screen** to identify a track<br>Save the jacket, copy its text, and jump straight to more information |
| **Song search** | Search by **title / artist / alias / chart constant / ID**<br>**Special aliases** also cover versions, removed songs, Utage charts and theme songs |
| **Collections** | Collect favourite songs in a folder tree that **nests as deep as you like**<br>Import and export **`.msrf`** files, with **read-only** and **force-restore** options<br>Players are encouraged to build and share **collection packs** |
| **Song database** | Nearly every maimai track, **compiled by hand from public data**<br>Includes **精文舞萌独占曲**, **removed songs** and **old-cabinet Utage charts**<br>**Over 1900** in total |
| **Appearance** | The original MaiScan interface (**Legacy**) for low-end devices<br>Plus new **Material** and **Miuix** UIs with **custom theming** |
| **UI languages** | **简体中文 / 繁體中文 / English / 日本語**<br>Switch any time from the About page |

## Search syntax

The search box understands a few "type-it-in" forms — **no buttons involved**:

| Input | What it does | Example |
| :-- | :-- | :-- |
| `keyword` | Fuzzy match (the default) | `舞萌` |
| `"keyword"` | **Exact match** (alias category only) | `"universe"` won't bring up `universe+` |
| `13.5` | Chart constant **equals** | `13.5` |
| `13.4-14.5` | Chart constant **range** (any difficulty inside it) | `13.4-14.5` |
| `query&[param]` | **Sort** the results; stacks with everything above | `你好&[ds4+]` |

**Sort parameters** (inside `&[…]` — right after the query, after a space, or even in front):

| Param | Meaning |
| :-- | :-- |
| `ds+` / `ds-` | by the song's **highest** chart constant, ascending / descending |
| `ds1+` … `ds5+` | by a specific slot: 1=Basic　2=Advanced　3=Expert　4=Master　5=Re:Master |
| `az+` / `az-` | by the **romaji** of the first character, a→z (pinyin for Chinese, romaji for kana) |
| `id+` / `id-` | by song ID, ascending / descending (`id-` puts the newest first) |

- The `+` is optional: no sign means ascending
- Besides the ASCII `-`, full-width separators such as `～` `－` `−` also work
- Combinations: `"universe"&[ds-]`　`13.4-14.5&[az]`　`你好 &[ds2+]`

## Download

| Source | Notes |
| :-- | :-- |
| Github | [Releases in this repository](../../releases/latest) |
| Lanzou Cloud | Mainland China mirror · link: TBD |
| Google Drive | International mirror · link: TBD |

> Android 6.0 or newer. On Android 8.0 or older, or on 32-bit builds, the new UI is unavailable.
