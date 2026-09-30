<p align="center">
  <img src="assets/icon.png" width="128" alt="MaiScan Rev">
</p>

<h1 align="center">MaiScan Rev</h1>

<p align="center">
  <sub>本地离线曲库 · 封面识曲 · 收藏整理</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Platform: Android 6.0+">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Language: Kotlin">
  <img src="https://img.shields.io/badge/Framework-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white" alt="Framework: Jetpack Compose">
  <img src="https://img.shields.io/badge/Purpose-maimai%20DX%20Tool-E4007F?style=flat-square" alt="Purpose: maimai DX Tool">
</p>

<p align="center">
  <b>简体中文</b> ｜ <a href="README.en.md">English</a> ｜ <a href="README.ja.md">日本語</a> ｜ <a href="README.zh-TW.md">繁體中文</a>
</p>

---

> 此 App 是基于 **MaiScan** 的修改版，原仓库见 **[Klta-kyo/MaiScan](https://github.com/Klta-kyo/MaiScan)**。

## 这是什么

**MaiScan Rev** 是基于 MaiScan 二次制作的 **maimai DX（舞萌 DX）本地离线曲库工具**，已支持以下功能：

| 功能 | 说明 |
| :-- | :-- |
| **封面识曲** | 在**歌曲选择阶段**拍摄曲绘识别歌曲，查看部分乐曲数据<br>支持**曲绘保存**、**文本内容复制**，以及快速搜寻更多信息 |
| **歌曲搜索** | 支持以**曲名 / 曲师 / 别名 / 定数 / ID** 搜索歌曲<br>借助**特殊别名**，还可搜索**版本号**、**删除曲**、**宴会场**、主题曲等 |
| **收藏系统** | 将喜欢的乐曲进行收藏，收藏夹支持**层级叠加**<br>可导入导出 **`.msrf`** 文件，设置**只读**与**暴力恢复**<br>也鼓励玩家制作**收藏整合包**进行分享 |
| **曲库方面** | 收录几乎所有 maimai 的歌曲<br>包括**精文舞萌独占曲**、**删除曲**、**旧框体宴会场**等<br>合计**超过 1900 首**，通过公开数据手动整理 |
| **外观设置** | 既有为低性能设备准备的原生 MaiScan 界面（**Legacy**）<br>也有基于 **Material** 与 **Miuix** 的新 UI，支持**自定义主题**界面 |

## 下载

| 渠道 | 说明 |
| :-- | :-- |
| Github | [本仓库 Release](../../releases/latest) |
| 蓝奏云 | 国内分流 · 链接：待补 |
| Google Drive | 国际分流 · 链接：待补 |

> Android 6.0 及以上。Android 8.0 以下、或 32 位将无法使用新 UI 界面。

## 搜索语法

搜索框支持几种「输入即用法」的写法 —— **不需要任何按钮**，直接打进去就行：

| 写法 | 作用 | 例子 |
| :-- | :-- | :-- |
| `关键词` | 模糊包含（默认行为） | `舞萌` |
| `"关键词"` | **精确匹配**（仅「别名」类别） | `"universe"` 不会带出 `universe+` |
| `13.5` | 定数**精确**等于 | `13.5` |
| `13.4-14.5` | 定数**区间**（任一难度落在区间内即命中） | `13.4-14.5` |
| `查询词&[参数]` | 在结果上**排序**，可与上面任意写法叠加 | `你好&[ds4+]` |

**排序参数**（写在 `&[…]` 里；紧贴查询词、留空格、放在最前面都行）：

| 参数 | 含义 |
| :-- | :-- |
| `ds+` / `ds-` | 按该曲**最高定数**升序 / 降序 |
| `ds1+` … `ds5+` | 按指定难度位：1=Basic　2=Advanced　3=Expert　4=Master　5=Re:Master |
| `az+` / `az-` | 按曲名首字的**罗马音** a→z（中文按拼音、日文假名按罗马音） |
| `id+` / `id-` | 按乐曲 ID 升 / 降（`id-` 就是新曲在前） |

- `+` 可以省略：不写符号就是**正序**
- 区间分隔符除了半角 `-`，也认全角 `～` `－` `−` 等
- 组合示例：`"universe"&[ds-]`　`13.4-14.5&[az]`　`你好 &[ds2+]`

## 反馈与交流

- **QQ 群**：[点此加入](https://qm.qq.com/q/LnWS4cxjQy) —— 反馈问题、提建议、提交新别名都欢迎
- **GitHub Issues**：本仓库的 [Issues](../../issues)

曲库与别名由玩家手工整理，发现缺漏或想补充，欢迎进群说一声。
