<p align="center">
  <img src="assets/icon.png" width="128" alt="MaiScan Rev">
</p>

<h1 align="center">MaiScan Rev</h1>

<p align="center">
  <sub>オフライン楽曲データベース · ジャケット認識 · コレクション整理</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Platform: Android 6.0+">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Language: Kotlin">
  <img src="https://img.shields.io/badge/Framework-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white" alt="Framework: Jetpack Compose">
  <img src="https://img.shields.io/badge/Purpose-maimai%20DX%20Tool-E4007F?style=flat-square" alt="Purpose: maimai DX Tool">
  <img src="https://img.shields.io/github/v/release/PojavAnge/MaiScan-Rev?style=flat-square&label=%E6%9C%80%E6%96%B0%E3%83%AA%E3%83%AA%E3%83%BC%E3%82%B9&color=3DDC84" alt="Latest release">
  <img src="https://img.shields.io/github/stars/PojavAnge/MaiScan-Rev?style=flat-square&label=%E3%82%B9%E3%82%BF%E3%83%BC&color=E4007F" alt="Stars">
  <img src="https://img.shields.io/github/downloads/PojavAnge/MaiScan-Rev/total?style=flat-square&label=%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89&color=2bb8c8" alt="Downloads">
</p>

<p align="center">
  <a href="README.md">简体中文</a> ｜ <a href="README.en.md">English</a> ｜ <b>日本語</b> ｜ <a href="README.zh-TW.md">繁體中文</a>
</p>

---

> 本アプリは **MaiScan** の改造版です。オリジナルのリポジトリは
> **[Klta-kyo/MaiScan](https://github.com/Klta-kyo/MaiScan)** をご覧ください。

## 概要

**MaiScan Rev** は、maimai DX 向けの **100% オフライン**なローカル楽曲検索ツールです。
選曲画面でジャケットを撮影して検索でき、テキスト検索にも対応しています。

## 主な機能

| 機能 | 説明 |
| :-- | :-- |
| **ジャケット認識** | OpenCV による撮影認識。画像を直接選んで認識させることもできます<br>照合には **SIFT** 特徴点を使うため、高速に動作します |
| **楽曲検索** | **曲名 / アーティスト / 別名 / 定数 / ID** で検索<br>別名からバージョン・削除曲・宴会场などを探せます |
| **コレクション** | ファイルツリー式のフォルダで整理。新しいフォルダを作るのと同じように階層を重ねられます<br>**`.msrf`** コレクションパックでまとめて共有できます |
| **楽曲情報** | 定数・難易度・ジャケット・別名など<br>テキストのコピー、ジャケットの保存といった基本的なオフライン機能に対応 |
| **プラグイン** | 独自プラグインに対応。現在の楽曲データを持ったままジャンプできます<br>プラグインの制作・利用でアプリの幅が広がります |
| **楽曲データ** | 通常の maimai 楽曲を **1900 曲以上**収録。旧筐体の宴会场データも含み、公開データから手作業で整理<br>オンライン API に依存しないため、データがあれば更新されます |
| **外観** | 初回起動時は **Legacy** 画面<br>アプリについてのページから新しい **Material / Miuix** 画面に切り替えられます<br>Legacy は MaiScan オリジナルに近い保守的な画面です<br>高度なデバッグやプラグインには対応していません |
| **UI 言語** | 「アプリについて」から切り替え可能：**简体中文 / 繁體中文 / English / 日本語** |

## コミュニティ

- 不具合の報告は QQ グループまたはこのリポジトリの issues まで。確認でき次第返信します。
- グループではプラグインの共有や問題の報告も歓迎です。QQ グループ：**781038216**

## ダウンロード

| 入手先 | 説明 |
| :-- | :-- |
| Github | [このリポジトリの Release](../../releases/latest) |
| Lanzou Cloud（藍奏雲） | [ilk.lanzoue.com/s/MaiScan](https://ilk.lanzoue.com/s/MaiScan) · 中国本土向けミラー |

> Android 6.0 以上。Android 8.0 未満、または 32bit では新しい UI を使用できません。

## ご注意

- 本プロジェクトは **Klta-卡** 氏の許諾を得た二次開発です。このページは配布用で、ソースコードは現在公開していません
- アーキテクチャとコードの制約により、iOS 版は今後も制作する予定はありません
- 個人での検索・整理用です。商用利用はご遠慮ください
- 本プロジェクトはコミュニティによるものです。ゲーム名・楽曲・譜面・ジャケットの著作権は SEGA および各作者・権利者に帰属します
- 楽曲データと別名は公開情報から手作業で整理したものです。再利用する場合は事前にご連絡いただき、開発者の労力にご配慮ください
