<p align="center">
<a href="AdvSearch_zh.md">简体中文</a> ｜ <b>English</b> ｜ <a href="AdvSearch_ja.md">日本語</a> ｜ <a href="AdvSearch_zh-TW.md">繁體中文</a>
</p>

# MaiScan Rev Advanced Search Guide

**Applies to**: MaiScan Rev `build.20261001` and later

This guide covers advanced text-search syntax: exact matching, sort suffixes, and chart-constant ranges. All symbols must be **half-width ASCII**.

---

## 1. Basics

Text search runs per category, each with its own matching rule:

| Category | Matching |
|---|---|
| Title | Contains (case-insensitive) |
| Artist | Contains (case-insensitive) |
| Alias | Contains; wrap in double quotes for exact equality |
| ID | Exact number |
| Chart constant | Exact float, or a range |
| Level | Exact string equality |

Sort suffixes **work in every category** and are appended to the query.

---

## 2. Exact Matching (alias only)

A song usually has several aliases, so the alias category offers an "exactly equal" form.

| Input | Meaning |
|---|---|
| `example` | Matches every alias **containing** "example", e.g. `example1`, `example song` |
| `"example"` | Matches only the alias **exactly equal to** "example" |

> Applies to the **alias** category only. Title and artist are always substring matches; quotes do not change them.

---

## 3. Sort Suffixes

### 3.1 Syntax

```
query&[param]
```

- Spaces are allowed between `&` and `[`
- Parameters are **case-insensitive**
- `+` means ascending, `-` means descending; omitting the sign means ascending
- Sorting applies to the **current result set** and does not change which songs match

### 3.2 Chart constant sort `ds`

| Input | Meaning |
|---|---|
| `query&[ds]` / `&[ds+]` | Ascending by **highest** chart constant |
| `query&[ds-]` | Descending by highest chart constant |
| `query&[ds1+]` … `&[ds5+]` | Ascending by the constant of the **given difficulty** |
| `query&[ds1-]` … `&[ds5-]` | Descending by the given difficulty |

Difficulty numbers: `1`=Basic, `2`=Advanced, `3`=Expert, `4`=Master, `5`=Re:Master.

> Songs without that difficulty (for example a 4-slot song with `ds5`) are **always placed last**, never at the start of an ascending sort.

### 3.3 Alphabetical sort `az`

| Input | Meaning |
|---|---|
| `query&[az]` / `&[az+]` | By reading of the title's leading part, A → Z |
| `query&[az-]` | By reading, Z → A |

- Readings are derived from kana/Latin letters at the start of the title (katakana is normalized to hiragana first)
- Songs whose title starts with characters that cannot be read (kanji, symbols) are placed **after** the A–Z block and sorted by pinyin
- This is therefore **not** a strict A–Z over the whole list

### 3.4 ID sort `id`

| Input | Meaning |
|---|---|
| `query&[id]` / `&[id+]` | Oldest first (ascending ID) |
| `query&[id-]` | Newest first (descending ID) |

### 3.5 Unknown parameters

If the content of `&[…]` is not recognized, the whole token is treated as part of the query; nothing is reported and sorting is unchanged.

---

## 4. Chart Constant Ranges

Type a closed range in the **chart constant** category:

```
13.4-14.4
```

- Supported separators: `-` `~` `〜` `～` `－` `−` `–` `—`
- Both ends are inclusive
- A song matches if **any one difficulty** falls inside the range
- Using the same number at both ends (`13.5-13.5`) is equivalent to the exact query `13.5`
- Double quotes around the ends are stripped automatically

> Ranges apply to the **chart constant** category only; other categories will return nothing.

---

## 5. Combinations and Precedence

| Input | Valid? |
|---|---|
| `query&[ds4+]` | Yes |
| `"alias"&[id-]` | Yes (exact alias + descending ID) |
| `13.4-14.4&[ds-]` | Yes (filter by range, then sort by highest constant descending) |
| `&[ds4+]query` | Yes (the token may appear anywhere and is extracted) |
| `query&[ds6+]` | Invalid parameter ⇒ treated as query text; usually no results |

Only the **first** valid sort token in an input is used.

---

## 6. FAQ

**Q: Quotes still return many results.**

Exact matching applies to the **alias** category only. Title and artist are substring matches.

**Q: The order after `&[az]` looks odd.**

`az` only works for titles with a derivable reading; songs starting with kanji or symbols are placed after the A–Z block and sorted by pinyin.

**Q: With `&[ds5]` some songs go last.**

Those songs have no 5th difficulty (Re:Master) and are placed last by design.

**Q: A chart constant range returns nothing.**

Make sure the current category is **chart constant**; ranges only work there.

**Q: The sort parameter does nothing.**

Check that you used half-width ASCII and a valid parameter (`ds` / `az` / `id`, difficulty 1–5).
