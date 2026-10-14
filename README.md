# GTA V PC — Modded Outfit Name Image Tags

A reference list of **1,570 image-source candidates**, compiled by **[Max1382](https://max1382.com)** for experimenting with custom **GTA V PC saved outfit names** using a compatible mod menu or outfit-name editor.

The accompanying [`image-sources-shortest-first.json`](image-sources-shortest-first.json) contains image tags, their UTF-8 byte lengths, and compatibility **length checks**. The list is sorted from shortest to longest tag.

> [!IMPORTANT]
> **These are candidates, not confirmed working outfit-name icons.** The JSON checks string lengths only. At the time of compilation, **none of the 1,570 entries had been verified to render in a saved outfit name** or verified against a GTA archive path. A tag fitting the field does **not** mean that GTA will render it.

## How to use (GTA V on PC)

1. Open [`image-sources-shortest-first.json`](image-sources-shortest-first.json) and find an image you want to test.
2. Copy its **`canonical_tag`** value exactly, including the angle brackets, single quotes, and `img src=` text.
3. Put a GTA colour code **before** the tag. For green, add `~g~` at the start.
4. In your compatible PC mod menu or outfit editor, find the **saved outfit name / rename** input, paste the completed string, and save or preview it if your tool supports that.
5. Check the result in game. If it appears as plain text, a blank space, or nothing, it may not be supported by that menu/game UI.

**Example from the JSON:**

```json
{
  "source": "rockstar_logo",
  "canonical_tag": "<img src='rockstar_logo'>",
  "tag_bytes": 25,
  "fits_saved_outfit_name": true,
  "render_verified_in_saved_outfit": false
}
```

Copy `canonical_tag` and add green:

```text
~g~<img src='rockstar_logo'>
```

**Another example (longer tag):**

```text
~g~<img src='img://game_stream/unlockcasinodiscounticon'>
```

That casino example is **57 UTF-8 bytes**, including `~g~`. It does **not** fit the standard 31-byte name limit documented by the file, but it falls within the experimental 63-byte field. **That does not confirm it will save or render.**

### Colour prefixes

| Prefix | Intended colour |
| --- | --- |
| `~g~` | Green |
| `~r~` | Red |
| `~b~` | Blue |
| `~y~` | Yellow |
| `~p~` | Purple |
| `~o~` | Orange |
| `~w~` | White |
| `~s~` | Reset to default formatting |

Colour codes are GTA formatting tokens; **whether they tint an image** rather than just nearby text depends on how the particular game UI renders the string. Each of the prefixes above is **3 additional ASCII / UTF-8 bytes**.

## Check the byte limit before pasting

This list describes a **31-byte saved outfit name limit**, plus a separate **experimental 63-byte field** in some editor workflows. These are **byte counts, not visible-character counts**.

**Formula:** `total_bytes = UTF8_bytes(colour_prefix + canonical_tag + any_other_text)`

| Example with green prefix | Total bytes | Fits 31 bytes? | Fits 63 bytes? |
| --- | ---: | :---: | :---: |
| `~g~<img src='rockstar_logo'>` | 28 | Yes | Yes |
| `~g~<img src='img://golf/clubs'>` | 31 | Yes | Yes |
| `~g~<img src='img://golf/grass'>` | 31 | Yes | Yes |
| `~g~<img src='img://hud/hud_g0'>` | 31 | Yes | Yes |
| `~g~<img src='img://hud/hud_g1'>` | 31 | Yes | Yes |
| `~g~<img src='img://game_stream/unlockcasinodiscounticon'>` | 57 | No | Yes, experimental only |

**Dataset length results:** 14 of 1,570 raw image tags fit within 31 bytes, but only **5** still fit when `~g~` is added. All 1,570 raw tags fit within 63 bytes; **1,567** fit within 63 bytes after adding `~g~`.

> [!WARNING]
> The 63-byte option is **experimental**. According to this dataset's notes, it should only be tested when explicitly enabled and when the relevant field tail is empty. Saving, persistence, and rendering have **not** been established. Do not force overlength strings into an editor that does not support them.

The JSON's `fits_saved_outfit_name` and `fits_experimental_63_byte_field` values are for the **unprefixed `canonical_tag` only**. Adding `~g~` or any other text means you must **recalculate** the length.

## Understanding the JSON

| Field | Meaning |
| --- | --- |
| `source` | Image-source identifier taken from a candidate list. |
| `dictionary` / `texture` | Parsed parts of `img://dictionary/texture` identifiers; `null` for some other source formats. |
| `canonical_tag` | Full `<img src='...'>` string to copy. |
| `source_bytes` | UTF-8 bytes used by `source`, not the entire tag. |
| `tag_bytes` | UTF-8 bytes used by `canonical_tag`, without a colour prefix. |
| `fits_saved_outfit_name` | Whether the unprefixed tag fits the file's 31-byte limit. |
| `remaining_name_bytes` | Unused bytes in the 31-byte limit (before adding a prefix). |
| `fits_experimental_63_byte_field` | Whether the unprefixed tag fits the file's experimental 63-byte limit. |
| `remaining_experimental_bytes` | Unused bytes in that experimental limit (before adding a prefix). |
| `render_verified_in_saved_outfit` | Whether actual rendering in a saved outfit was verified; `false` currently means **not verified**, not necessarily broken. |
| `archive_path_verified` | Whether the game-archive asset path was verified; currently not verified. |
| `evidence` | Where a candidate came from; **not** necessarily proof that it works. |

## Credit and redistribution — attribution required

**This compilation and its original documentation were created by [Max1382](https://max1382.com).** The official project is hosted at **[Max1382/GTA-V-Modded-Outfit-Names](https://github.com/Max1382/GTA-V-Modded-Outfit-Names)**.

If you **copy, reupload, mirror, redistribute, or adapt the original compilation or documentation**, keep clear attribution and a link back to the creator. Give credit prominently in your project's README, website, video description, or equivalent location.

**Copy/paste attribution:**

> GTA V PC Modded Outfit Name Image Tags — compiled by **[Max1382](https://max1382.com)**. Original project: **[https://github.com/Max1382/GTA-V-Modded-Outfit-Names](https://github.com/Max1382/GTA-V-Modded-Outfit-Names)**. Original compilation licensed under **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)**. Changes: [describe changes, or write "none"].

The licence applies to **Max1382’s original contributions**, such as the selection, arrangement, annotations, and documentation, to the extent those elements are copyrightable. It **does not** claim ownership of Rockstar Games / Take-Two assets, brand names, logos, textures, or independently existing technical identifiers. See [`LICENSE.md`](LICENSE.md).

## Contributing and reporting working tags

Found an image that really works in a saved outfit name? Open a GitHub Issue or Pull Request with:

- The exact full string you tested (including colour prefix).
- Your GTA V PC version/build and outfit editor or mod-menu name/version.
- Whether it **rendered**, **saved**, and **remained after reloading**.
- A screenshot if possible, with personal details hidden.

See [`CONTRIBUTING.md`](CONTRIBUTING.md). Please don't mark an entry as verified just because its byte count fits.

## Important notes

- This is a **JSON research/reference list**, not a mod menu, executable, injector, or collection of image files.
- Rendering depends on the game version, the exact UI text renderer, and the editor/mod menu used. Some GTA interfaces may treat image tags as literal text.
- Only **lengths** have been checked. Do not assume all listed sources exist in game archives or work as saved outfit names.
- Use third-party mod tools at your own risk. Modifying GTA Online may violate Rockstar's rules and may result in account restrictions.
- This is an **unofficial fan project**, not affiliated with or endorsed by Rockstar Games or Take-Two Interactive. All game-related trademarks and assets belong to their respective owners.

---

**Created and maintained by [Max1382](https://max1382.com) — [GitHub repository](https://github.com/Max1382/GTA-V-Modded-Outfit-Names). If you reuse or redistribute this compilation, credit Max1382 and link back to the original project.**
