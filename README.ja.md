<p align="center">
  <img src="assets/icon.png" width="128" alt="MaiScan Rev">
</p>

<h1 align="center">MaiScan Rev</h1>

<p align="center">
  <sub>ローカル・オフライン楽曲データ · ジャケット認識 · コレクション整理</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Platform: Android 6.0+">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Language: Kotlin">
  <img src="https://img.shields.io/badge/Framework-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white" alt="Framework: Jetpack Compose">
  <img src="https://img.shields.io/badge/Purpose-maimai%20DX%20Tool-E4007F?style=flat-square" alt="Purpose: maimai DX Tool">
</p>

<p align="center">
  <a href="README.md">简体中文</a> ｜ <a href="README.en.md">English</a> ｜ <b>日本語</b> ｜ <a href="README.zh-TW.md">繁體中文</a>
</p>

---

> 本アプリは **MaiScan** の改造版です。オリジナルのリポジトリは
> **[Klta-kyo/MaiScan](https://github.com/Klta-kyo/MaiScan)** をご覧ください。

## これは何か

**MaiScan Rev** は MaiScan をベースに二次制作した **maimai DX のローカル・オフライン楽曲データツール**です。
現在は以下に対応しています：

| 機能 | 説明 |
| :-- | :-- |
| **ジャケット認識** | **選曲画面**でジャケットを撮影して楽曲を識別<br>データの一部を表示し、**ジャケット保存**や**コピー**にも対応 |
| **楽曲検索** | **曲名 / アーティスト / 別名 / 定数 / ID** で検索<br>**特殊な別名**を使えば、**バージョン番号**や**削除曲**も検索可能 |
| **コレクション** | お気に入りを**何階層でも重ねられる**フォルダで整理<br>**`.msrf`** の入出力、**読み取り専用**・**強制復元**に対応<br>**まとめて共有**することも歓迎します |
| **楽曲データ** | maimai のほぼ全曲を収録し、公開データから手作業で整理<br>**精文舞萌独占曲**・**削除曲**・**旧筐体の宴会场**などを含め<br>合計**1900 曲以上** |
| **外観** | 低スペック端末向けのオリジナル MaiScan 画面（**Legacy**）<br>**Material** / **Miuix** の新しい UI と**テーマのカスタマイズ** |

## ダウンロード

| 入手先 | 説明 |
| :-- | :-- |
| Github | [このリポジトリの Release](../../releases/latest) |
| Lanzou Cloud（藍奏雲） | 中国本土向けミラー · URL：未定 |
| Google Drive | 海外向けミラー · URL：未定 |

> Android 6.0 以上。Android 8.0 未満、または 32bit では新しい UI を使用できません。

## 検索構文

検索ボックスは「入力するだけ」の書き方に対応しています —— **ボタンは一切不要** です：

| 入力 | 内容 | 例 |
| :-- | :-- | :-- |
| `キーワード` | 部分一致（既定） | `舞萌` |
| `"キーワード"` | **完全一致**（別名カテゴリのみ） | `"universe"` は `universe+` を拾いません |
| `13.5` | 定数が**一致** | `13.5` |
| `13.4-14.5` | 定数の**範囲**（いずれかの難易度が範囲内） | `13.4-14.5` |
| `検索語&[パラメータ]` | 結果を**並べ替え**（上の書き方と併用可） | `你好&[ds4+]` |

**並べ替えパラメータ**（`&[…]` の中。検索語の直後でも、空白を挟んでも、先頭でも可）：

| パラメータ | 意味 |
| :-- | :-- |
| `ds+` / `ds-` | その曲の**最高定数**で昇順 / 降順 |
| `ds1+` … `ds5+` | 難易度スロット指定：1=Basic　2=Advanced　3=Expert　4=Master　5=Re:Master |
| `az+` / `az-` | 曲名の頭文字の**ローマ字**で a→z（中国語はピンイン、仮名はローマ字） |
| `id+` / `id-` | 曲 ID で昇順 / 降順（`id-` は新しい曲が先） |

- `+` は省略可：記号なしは昇順
- 範囲の区切りは半角 `-` のほか、全角 `～` `－` `−` なども可
- 組み合わせ例：`"universe"&[ds-]`　`13.4-14.5&[az]`　`你好 &[ds2+]`

## フィードバック

- **QQ グループ**：[こちらから参加](https://qm.qq.com/q/LnWS4cxjQy) —— 不具合報告・提案・別名の追加依頼など歓迎です
- **GitHub Issues**：このリポジトリの [Issues](../../issues)

楽曲データと別名はプレイヤーが手作業でまとめています。抜けを見つけたら、グループで気軽に教えてください。
