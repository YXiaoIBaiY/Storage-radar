# Configuration Reference

> 中文版：[CONFIG.zh-CN.md](CONFIG.zh-CN.md)

## Where the config lives

- File: `config/truesight-storage.json` inside your Minecraft instance folder.
- It is managed by **malilib**; hotkey bindings are stored in the same file.
- Prefer the in-game config screen over hand-editing: the file is rewritten by malilib.

## Opening the config screen

Any of these:

- **Mod Menu** → Storage Radar → **Config**
- The **配置 / Config** button in the Storage Radar screen
- malilib's shared config screen switcher (the same list Tweakeroo / MiniHUD / Litematica use)

The panel is masa-style and bilingual: the first line of each row is Chinese, the second line is the English name. The header also shows the current open/take hotkeys and radius.

## Options

| # | Chinese label | Internal name | Type | Default | Range | Meaning |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 检索半径 | `radius` | integer | 16 | 1–128 | Search radius in blocks around the player. Only filters ChestTracker's memory — no world scanning, so a large value is cheap. |
| 2 | 打开展示界面 | `openStorageGui` | hotkey | B | — | Opens the Storage Radar screen. Works in game. |
| 3 | 取物热键 | `takeHoveredItem` | hotkey | R | — | Takes the hovered slot, or the whole selection when several cells are selected. Only active inside the radar screen. |
| 4 | 取物中取消 | `cancelTake` | hotkey | ESC | — | Cancels a running retrieval: stops Baritone and clears the take queue. The key is consumed while it cancels, so no pause menu opens; with nothing running, ESC behaves normally. |
| 5 | 按数量排序 | `sortByCount` | boolean | on | — | On: sort by stack size (largest first), then by distance. Off: sort by distance only. |
| 6 | 显示容器位置 | `showLocationInfo` | boolean | on | — | On hover, show container name, coordinates, slot index and distance to the left of the grid. |
| 7 | 寻路允许破坏 | `allowBreakWhilePathing` | boolean | off | — | Forces Baritone's "allow break" setting to this value while a retrieval is running, and restores the previous value when it ends. Both directions are written, so turning it off really turns it off even if Baritone's default was on. |
| 8 | 取完关闭界面 | `closeAfterTake` | boolean | on | — | On: the radar screen closes when a retrieval starts, and each container screen is closed once its selected slots are taken. Off: screens stay open. |
| 9 | 取完重开界面 | `reopenAfterTake` | boolean | off | — | Reopens the radar screen after the whole batch is finished. |
| 10 | 只看命名容器 | `onlyNamedContainers` | boolean | off | — | Only list containers that have a custom (anvil-given) name. Useful to filter decorative chests. |

## Changing hotkeys

In the config screen, the hotkey rows show a key field:

1. Click the key field.
2. Press the new key (modifier keys may be combined, e.g. `Ctrl + B`).
3. Press `Esc` to cancel capture.

The three hotkeys are registered with malilib's own key registry, so they do not occupy vanilla key bindings and do not conflict with vanilla `Controls` entries.

## Notes

- Options 8 and 9 work best together: with 8 on and 9 on, the radar closes for the trip and comes back with the refreshed list.
- The cancel hotkey uses malilib's "cancel on handle" behaviour: it is only consumed while a retrieval is actually running, so ESC remains the normal pause-menu key otherwise.
- There is no "merge identical stacks" option: a row is always exactly one slot / one stack.
- All values are per-instance and per-profile; copying the JSON to another instance reproduces the setup.
