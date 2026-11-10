<p align="center">
  <img src="assets/icon.png" width="128" alt="MaiScan Rev">
</p>

<h1 align="center">MaiScan Rev</h1>

<p align="center">
  <sub>本地离线曲库 · 封面识曲 · 收藏整理</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Language: Kotlin">
  <img src="https://img.shields.io/badge/Framework-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white" alt="Framework: Jetpack Compose">
  <img src="https://img.shields.io/github/stars/PojavAnge/MaiScan-Rev?style=flat-square&logo=github&label=Star&color=E4007F" alt="Stars">
  <img src="https://img.shields.io/github/downloads/PojavAnge/MaiScan-Rev/total?style=flat-square&logo=github&label=Downloads&color=2bb8c8" alt="Downloads">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Platform: Android 6.0+">
  <img src="https://img.shields.io/badge/Purpose-maimai%20DX%20Tool-E4007F?style=flat-square" alt="Purpose: maimai DX Tool">
  <img src="https://img.shields.io/github/v/release/PojavAnge/MaiScan-Rev?style=flat-square&logo=github&label=Release&color=3DDC84" alt="Latest release">
</p>

<p align="center">
  <b>简体中文</b> ｜ <a href="README.en.md">English</a> ｜ <a href="README.ja.md">日本語</a> ｜ <a href="README.zh-TW.md">繁體中文</a>
</p>

---

> 此 App 是基于 **MaiScan** 的修改版，原仓库见 **[Klta-kyo/MaiScan](https://github.com/Klta-kyo/MaiScan)**。

## 简介

**MaiScan Rev** 是一个面向 maimai DX（舞萌 DX）的**100% 离线**的本地查曲工具：
在选歌画面拍下曲绘进行查询，也可文字搜索。

## 主要功能

| 功能 | 说明 |
| :-- | :-- |
| **封面识曲** | 使用 OpenCV 进行拍摄识图，也可直接选择图片进行识别<br>比对用的是 **SIFT** 特征点，保证快速可用 |
| **歌曲搜索** | 支持按 **曲名 / 曲师 / 别名 / 定数 / ID** 搜索<br>别名可以查找版本、删除曲、宴会场等 |
| **收藏管理** | 文件树式收藏夹，支持像新建文件夹那样叠加收藏夹<br>使用 **`.msrf`** 收藏包，可快速打包分享给好友 |
| **曲目信息** | 定数与谱面、曲绘、别名等信息<br>可以复制文本内容、保存曲绘等基础离线功能 |
| **拓展插件** | 支持自定义插件，支持携带当前曲目数据跳转<br>制作与使用插件，可用来拓展 App 可玩性 |
| **曲库数据** | 收录常规 maimai 曲目，**1900+**，含有 maimai 旧框体的宴会场数据，由公开数据手动整理<br>不依赖联网的 API，所以有数据便会更新 |
| **界面外观** | 首次启动默认为 **Legacy** 界面<br>在关于页可切换 **Material / Miuix** 的新版页面<br>Legacy 是偏保守与 MaiScan 原版怀旧保留<br>Legacy不支持高级调试与插件等功能 |
| **界面语言** | 可在「关于」页切换界面语言，支持 **简体中文 / 繁體中文 / English / 日本語** |

## 交流

- Bug 反馈可在 QQ 群聊 / 本仓库 issues 提交，看到便会回复。
- 交流群内可互相分享插件、反馈问题。交流群号：**781038216**

## 下载

| 渠道 | 说明 |
| :-- | :-- |
| Github | [本仓库 Release](../../releases/latest) |
| 蓝奏云 | [ilk.lanzoue.com/s/MaiScan](https://ilk.lanzoue.com/s/MaiScan) · 国内分流 |

> Android 6.0 及以上。Android 8.0 以下、或 32 位将无法使用新 UI 界面。

## 说明

- 本项目为 **Klta-卡** 授权二次开发，本页面仅作发行，代码等暂不开源
- 受限于架构与代码，本项目将来不计划也不会制作 iOS 版本
- App 仅供个人查询与整理使用，勿用于商业用途
- 本项目是社区项目，游戏名称、曲目、谱面与曲绘版权归 SEGA 及各原作者 / 版权方所有
- 曲目与别名数据来自公开渠道手动整理，如需使用这些数据请提前说明，尊重开发者的劳动成果
