<p align="center">
  <img src="assets/icon.png" width="128" alt="MaiScan Rev">
</p>

<h1 align="center">MaiScan Rev</h1>

<p align="center">
  <sub>Offline song database · Cover recognition · Collection manager</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Platform: Android 6.0+">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Language: Kotlin">
  <img src="https://img.shields.io/badge/Framework-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white" alt="Framework: Jetpack Compose">
  <img src="https://img.shields.io/badge/Purpose-maimai%20DX%20Tool-E4007F?style=flat-square" alt="Purpose: maimai DX Tool">
  <img src="https://img.shields.io/github/v/release/PojavAnge/MaiScan-Rev?style=flat-square&label=Release&color=3DDC84" alt="Latest release">
  <img src="https://img.shields.io/github/stars/PojavAnge/MaiScan-Rev?style=flat-square&label=Stars&color=E4007F" alt="Stars">
  <img src="https://img.shields.io/github/downloads/PojavAnge/MaiScan-Rev/total?style=flat-square&label=Downloads&color=2bb8c8" alt="Downloads">
</p>

<p align="center">
  <a href="README.md">简体中文</a> ｜ <b>English</b> ｜ <a href="README.ja.md">日本語</a> ｜ <a href="README.zh-TW.md">繁體中文</a>
</p>

---

> This app is a modified build of **MaiScan** — the original repository is
> **[Klta-kyo/MaiScan](https://github.com/Klta-kyo/MaiScan)**.

## About

**MaiScan Rev** is a **100% offline** local lookup tool for maimai DX:
take a photo of the jacket art on the song-select screen to look up a song, or search by text.

## Features

| Feature | Description |
| :-- | :-- |
| **Cover recognition** | Camera recognition powered by OpenCV; you can also pick an image directly<br>Matching uses **SIFT** feature points, so it stays fast and usable |
| **Song search** | Search by **title / artist / alias / chart constant / ID**<br>Aliases also cover versions, removed songs and Utage charts |
| **Collections** | File-tree style folders; nest collections just like creating new folders<br>Export **`.msrf`** collection packs to share with friends |
| **Song details** | Chart constants and difficulties, jacket, aliases and more<br>Copy text, save the jacket, and other basic offline features |
| **Plugins** | Custom plugins are supported, including jumps that carry the current song's data<br>Make and use plugins to extend what the app can do |
| **Song database** | The regular maimai catalogue, **1900+** songs, including old-cabinet Utage data, compiled by hand from public data<br>No online API is required, so it updates whenever the data does |
| **Appearance** | First launch uses the **Legacy** UI<br>Switch to the newer **Material / Miuix** UI on the About page<br>Legacy keeps the conservative, original-MaiScan look<br>It does not support advanced debugging or plugins |
| **UI languages** | Switch the interface language on the About page: **简体中文 / 繁體中文 / English / 日本語** |

## Community

- Bug reports are welcome in the QQ group or in this repository's issues; we'll reply when we see them.
- The group is also a place to share plugins and report problems. QQ group: **781038216**

## Download

| Source | Notes |
| :-- | :-- |
| Github | [Releases in this repository](../../releases/latest) |
| Lanzou Cloud | [ilk.lanzoue.com/s/MaiScan](https://ilk.lanzoue.com/s/MaiScan) · Mainland China mirror |

> Android 6.0 or newer. On Android 8.0 or older, or on 32-bit builds, the new UI is unavailable.

## Notes

- This project is an authorised second-round development by **Klta-卡**. This page is for distribution only; the source code is not open for now
- Due to the architecture and codebase, an iOS version is neither planned nor will be made
- For personal lookup and organisation only; please don't use it commercially
- This is a community project. Game names, songs, charts and jacket art belong to SEGA and their respective authors / rights holders
- Song and alias data was compiled by hand from public sources. If you want to reuse that data, please ask first and respect the authors' work
