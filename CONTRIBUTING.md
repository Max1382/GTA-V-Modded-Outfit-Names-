# Contributing to GTA V PC Modded Outfit Name Image Tags

Thanks for helping improve this reference list maintained by [Max1382](https://max1382.com). The original project is available at [Max1382/GTA-V-Modded-Outfit-Names](https://github.com/Max1382/GTA-V-Modded-Outfit-Names-). Please separate **possible source IDs** from **tested working outfit-name tags**.

## Report a working or broken tag

Open an Issue with:

- **Canonical tag:** `<img src='...'>`
- **Exact name pasted:** include any `~g~`, `~r~`, or other text
- **Length:** number of UTF-8 bytes in the full name
- **GTA V platform/build:** GTA V PC and the version/build, if known
- **Editor/mod menu:** product and version
- **Results:** appeared correctly / showed plain text / blank / failed to save
- **Persistence:** still works after leaving/rejoining or reloading the outfit?
- **Evidence:** optional screenshot, avoiding account names and personal information

A name fitting into 31 or 63 bytes is **not** proof that the image source exists or renders.

## Pull requests

1. Keep the existing JSON structure and field names.
2. Include evidence for newly added sources.
3. Don't set `render_verified_in_saved_outfit` or `archive_path_verified` to `true` unless you have specific evidence for that field.
4. Calculate `tag_bytes` from the **UTF-8 bytes of `canonical_tag`**, without any added colour prefix. Recalculate other length fields as appropriate.
5. Preserve attribution to **Max1382** and a link to **https://max1382.com** and the [original repository](https://github.com/Max1382/GTA-V-Modded-Outfit-Names-), as described in the licence.

This is an unofficial fan project. Do not upload proprietary GTA asset files or copyrighted third-party textures to the repository without permission.
