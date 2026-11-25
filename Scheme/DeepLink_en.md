<p align="center">
<a href="DeepLink_zh.md">简体中文</a> ｜ <b>English</b> ｜ <a href="DeepLink_ja.md">日本語</a> ｜ <a href="DeepLink_zh-TW.md">繁體中文</a>
</p>

# MaiScan Rev Deep Link (`maiscan://`) Specification

**Version**: 1.0　**Applies to**: MaiScan Rev `build.20261126` and later　**Platform**: Android 6.0+ (`run` / `play` require the new UI, see Section 11)

This document is for developers and advanced users who want to trigger MaiScan Rev from other apps, NFC tags, QR codes, or automation tools.

---

## Table of Contents

1. [Overview](#1-overview)
2. [Link Structure](#2-link-structure)
3. [Parameters](#3-parameters)
4. [Action `action`](#4-action-action)
5. [Silent Execution `execution`](#5-silent-execution-execution)
6. [Random Pick `songID=random`](#6-random-pick-songidrandom)
7. [Running Target `sweep`](#7-running-target-sweep)
8. [Failure Behavior](#8-failure-behavior)
9. [NFC Tags](#9-nfc-tags)
10. [Full Examples](#10-full-examples)
11. [Compatibility and Limitations](#11-compatibility-and-limitations)
12. [FAQ](#12-faq)
13. [Changelog](#13-changelog)

---

## 1. Overview

`maiscan://` lets an external caller make MaiScan Rev perform one of the following:

- Open the main screen
- Open the detail page of a specific song
- Hand the file of a specific song to the target app declared by a plugin
- Send a specific song to the built-in player of MaiScan

---

## 2. Link Structure

```
maiscan://info/songID=<song ID or random>{parameter list}
```

| Link | Behavior |
|---|---|
| `maiscan://` | Opens the main screen (a bare scheme is a valid link) |
| `maiscan://info/songID=10721` | Opens the detail page of song 10721 |
| `maiscan://info/songID=random` | Picks a random song and opens its detail page |
| `maiscan://info/songID=10721{plugin="com.exp.pack",action=run,execution=1}` | Silent execution: hands the song file directly to the target app |
| `maiscan://info/songID=10721{action=play}` | Sends the song to the built-in player; stays on the detail page if the player is not enabled |

**Writing conventions**

- Wrap the parameter list in `{` `}`, separate parameters with `,`, and use `key=value`.
- String values are best written with double quotes; quotes around `songID` are optional.
- `{` `}` `"` are not standard URI characters. If a writing tool percent-encodes them (`%7B` `%7D` `%22`), MaiScan decodes first and both forms are accepted.

---

## 3. Parameters

| Parameter | Value | Meaning |
|---|---|---|
| `plugin` | Plugin package name | The plugin responsible for the action. For bundles you may write the **parent** (the matching child is located automatically), or the **child package name** directly, which limits the action to that child. A child requires its parent to be enabled and the child itself not disabled |
| `action` | `run` / `play` | The action to perform, see Section 4 |
| `execution` | `1` / `0` / omitted | Whether to run silently, see Section 5. `true` / `false` are accepted |
| `sweep` | `1` / `2` / omitted | Only effective for `action=run`, see Section 7 |
| `wlist` | `"1,2,3"` | Only for `songID=random`: whitelist |
| `blacklist` | `"1,2,3"` | Only for `songID=random`: blacklist |
| `debug` | `1` / `0` | `1` shows each step as a Toast; omitted or `0` shows nothing |

Unknown parameters are ignored and do not invalidate the link.

---

## 4. Action `action`

| Value | Behavior |
|---|---|
| `run` | Simulates the plugin button on the detail page. FILE plugins: hands the song file to the declared target app. WEB plugins: opens the declared URL in a browser |
| `play` | Sends the audio to the built-in player. On success the app returns to the main screen and the floating player continues; if the built-in player is not enabled, the detail page stays open and playback happens in-page |

**Where `play` gets its audio**

1. First, resolve from enabled plugins by song ID: `.aiu` (with `.arup`), `.adx`, `.mp3`, `.ogg` / `.oga`, `.flac`, `.wav`;
2. If that fails, fall back to playable files declared by plugin buttons.

`play` does not require `plugin`. Other formats (such as `.m4a`, `.aac`, `.opus`) depend on the device decoder and are not guaranteed.

### WEB plugins

WEB plugins have no file and no target package, only a URL (`url` in `Webrule.json`). Using `action=run` on them opens that URL directly in a browser, with the placeholders `[id]`, `[title]`, `[artist]` substituted as usual.

- Any URL scheme is allowed: `https://` and custom schemes (such as `astrodx://…`) are dispatched by the system.
- Recursion guard: if the plugin's target is `maiscan://` itself, the call fails and stays on the detail page.
- The same rule applies to FILE plugins: a target package pointing at MaiScan itself is rejected.
- WEB plugins do not use `sweep`, since no import into a target app is involved.

---

## 5. Silent Execution `execution`

| Value | Behavior |
|---|---|
| `1` (or `true`) | Try silent: no UI is shown when the action succeeds |
| omitted / `0` (or `false`) | Opens the detail page first, then the app simulates the corresponding button |

---

## 6. Random Pick `songID=random`

Write `songID` as `random` (case-insensitive) to pick a song at random.

**Filtering rules (applied in order)**

1. If `wlist` is not empty, only pick from it;
2. Exclude songs in `blacklist`;
3. If `plugin` is given, keep only songs covered by that plugin: `[SongList]` / `%file%` rules must match; FILE plugins must actually contain the file (`pack-all` counts as covering everything); for bundles, either the parent or any enabled child may match; if a child package name is given, only that child is considered.

If no candidate remains, the link is treated like a nonexistent song: the main screen opens with no message.

```
maiscan://info/songID=random
maiscan://info/songID=random{wlist="10721,10722"}
maiscan://info/songID=random{blacklist="9"}
maiscan://info/songID=random{action=play}
```

---

## 7. Running Target `sweep`

Target apps (for example AstroDX) only read imports on a cold start; while running, a new launch request is ignored. `sweep` is used to attempt an import when the target is already running.

| Value | Approach | Measured result (AstroDX only) |
|---|---|---|
| omitted (=0) | Normal launch | Target in background: **cannot inject**; restarting the target and retrying fails the same way. Target in foreground: launching **crashes immediately**, with no relaunch afterwards, and an error dialog (Unity) may appear directly |
| `sweep=1` | Same as 0, but **relaunches the target after the crash** | The crash dialog still appears, but usually flashes by; if it is not dismissed/cancelled, the import continues |
| `sweep=2` | Lets the target create a new task in its own stack | Usually does not crash; the cost is one extra recent-task entry per trigger |

⚠️ This has been **tested on AstroDX only**; other apps may behave differently. Other Unity apps that support external imports are expected to behave similarly.

With `sweep`, the flow is always a silent import; `execution` no longer affects silence.

Both modes try to bring the target back to the foreground about 1.8 seconds after the import; failures are logged only, and shown as a Toast when `debug=1`.

---

## 8. Failure Behavior

| Situation | Result |
|---|---|
| Malformed link / song ID not parsable / ID not in the library | Main screen (no message) |
| Valid ID but neither `plugin` nor `action` given | Song detail page |
| Invalid parameter values (e.g. `action` is not `run` / `play`) | Song detail page |
| Plugin not installed / installed but not enabled | Song detail page |
| The plugin has no file for this song | Song detail page |
| Target app not installed or rejects the file | Song detail page |
| `action=play` cannot resolve any audio | Song detail page |

> A plugin must be "installed and enabled" for actions to run, consistent with the buttons shown on the detail page.

---

## 9. NFC Tags

- Write one **URI record** whose content is a `maiscan://…` link from this document.
- It is recommended to also write an **AAR (Android Application Record)**: `com.MaiScan.Rev`. Then, even if other apps on the device declare `maiscan://`, the system hands the intent directly to MaiScan.
- MaiScan registers both plain links (`VIEW`) and NFC tags (NDEF), so both `maiscan://` and `maiscan://info/…` are accepted.

---

## 10. Full Examples

Open a song detail page:

```
maiscan://info/songID=10721
```

Open a random song:

```
maiscan://info/songID=random
```

Silent import (easiest when the target app is not running):

```
maiscan://info/songID=10721{plugin="com.exp.pack",action=run,execution=1}
```

The target app is running (`sweep=1` relaunches it after the crash):

```
maiscan://info/songID=10721{plugin="com.exp.pack",action=run,execution=1,sweep=1}
```

Troubleshooting (step-by-step prompts):

```
maiscan://info/songID=10721{plugin="com.exp.pack",action=run,execution=1,sweep=1,debug=1}
```

Send to the built-in player:

```
maiscan://info/songID=10721{action=play}
```

Pick a random song and play it:

```
maiscan://info/songID=random{action=play}
```

Percent-encoded form (equivalent to the silent import above):

```
maiscan://info/songID=10721%7Bplugin=%22com.exp.pack%22,action=run,execution=1%7D
```

---

## 11. Compatibility and Limitations

- **Platform**: Android 6.0 and above; however **`run` / `play` depend on the new UI and the plugin system**, requiring Android 8.0+ on a 64-bit device.
- **Legacy devices**: on Android below 8.0 or on 32-bit devices only the Legacy UI is available, with **no plugin support** — links that carry `plugin` will not run and will land on the song detail page as "plugin not installed / not enabled". `maiscan://` and plain `songID` links are unaffected.
- **Offline**: everything is processed locally; no network requests are made.
- **Plugin requirement**: `run` needs a target package name declared by the plugin (`targetPackage` in `metadata.ini`); without it the system falls back to an app chooser and silence is impossible.
- **Target app behavior**: if the target app does not handle a running launch request, only `sweep` can attempt it; Unity targets crash once during the import (see Section 7). The cleaner solution is for the target app to re-read the link content when it receives a new launch request.
- **Language**: link syntax is independent of the system language; UI strings follow the app language setting.

---

## 12. FAQ

**Q: How do I find the child package name of a bundle?**

Unzip the bundle: every `.msrp` under `msrpack/` is a separate child. The `package=` (or `name=`) value in its `pack_manifest.ini` is the child package name. Write it directly into `plugin=`; do not prefix it with the parent name, and do not add the file name or extension.

**Q: The child package is written but does nothing.**

A child depends on its parent: the parent bundle must be installed and enabled, and the child itself must not be disabled.

**Q: `songID=random` picked nothing and went straight to the main screen.**

Either the whitelist/blacklist filtering left no candidate, or the given plugin/child covers no songs. In that case random pick is treated as a nonexistent song, with no message.

**Q: `action=play` plays no sound.**

First check that the built-in player is enabled (otherwise the detail page opens and playback happens in-page). Then check that the song actually has playable audio in an enabled plugin (`.aiu` / `.adx` / `.mp3`, etc.).

**Q: Can legacy phones (Android 8.0 or lower / 32-bit) use these links?**

Opening the main screen or a song detail page works; `action=run` and `action=play` do not — legacy devices only have the Legacy UI without plugins or the built-in player, so links carrying `plugin` are treated as "plugin not installed / not enabled".

**Q: `action=run` shows an app chooser instead of running silently.**

The plugin did not declare a target package. Silent `run` depends on the plugin declaring its target app; otherwise the system can only let the user choose.

**Q: Why does the target app in the link not respond?**

Most target apps only read imports on a cold start. With the target in the background, `sweep` cannot inject either; with it in the foreground, Unity targets crash once, and `sweep=1` relaunches and continues the import. See Section 7.

**Q: Can links with `debug=1` be published to ordinary users?**

Yes, but they will show step-by-step prompts. Omit the parameter for public releases.

---

## 13. Changelog

| Version | Date | Changes |
|---|---|---|
| 1.0 | 2026-11-26 | First release: parameters and actions, random pick, `sweep`, failure behavior, NFC usage, and FAQ |
