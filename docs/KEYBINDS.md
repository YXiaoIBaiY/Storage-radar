# Controls & Keybinds

> 中文版：[KEYBINDS.zh-CN.md](KEYBINDS.zh-CN.md)

Storage Radar has two kinds of input:

1. **malilib hotkeys (keyboard)** — fully rebindable, stored in the mod config.
2. **GUI actions (mouse + keys inside the screen)** — fixed; they are part of the grid UI.

## Rebindable hotkeys

| Hotkey | Default | Active when | Config name | Notes |
| --- | --- | --- | --- | --- |
| Open Storage Radar | **B** | in game | `openStorageGui` / 打开展示界面 | Needs a loaded world and ChestTracker; if no world/ChestTracker, an action-bar message explains why |
| Take hovered slot / selection | **R** | inside the Storage Radar screen | `takeHoveredItem` / 取物热键 | See "R semantics" below |
| Cancel the current retrieval | **ESC** | in game, only while a retrieval is running | `cancelTake` / 取物中取消 | Stops Baritone and clears the take queue. The keypress is consumed while it cancels, so the pause menu does not open; when nothing is running, ESC keeps its vanilla behaviour |

**How to rebind:** open the mod config screen → click the key field → press the new key.
The config screen is reachable from:

- Mod Menu → Storage Radar → **Config** button,
- the **配置** button inside the Storage Radar screen,
- malilib's shared config screen list (masa mods use one switcher).

malilib keeps its own key registry, so these hotkeys do not occupy vanilla `KeyMapping` slots and do not fight with Baritone / Tweakeroo / MiniHUD binds. If a key is already used by another malilib mod, pick a different one.

## Screen controls

### Mouse

| Action | Input | Result |
| --- | --- | --- |
| Select / unselect | **Left click** on a cell | Toggles that cell; also sets the range anchor |
| Select only this | **Ctrl + Left click** | Clears the selection and selects just this cell |
| Range select | **Shift + Left click** | Selects every cell between the anchor and the clicked cell (across pages) |
| Select identical stacks | **Alt + Left click** | Adds every stack on the **current page** that is the same item + same components |
| Take this slot | **Right click** on a cell | Immediately starts retrieval of that one slot, without changing the selection |
| Previous / next page | **Mouse wheel** | Wheel up = previous page, wheel down = next page (works anywhere on the screen) |
| Hover info | Move the mouse over a cell | Item tooltip; container name, coordinates, slot and distance are shown left of the grid |

### Keyboard (screen open)

| Action | Input | Result |
| --- | --- | --- |
| Take hovered / selected | **R** | Default take hotkey; see semantics below |
| Take the selection | **Tab** | Same as the **取选中 / Take selected** button |
| Select the whole page | **Ctrl + A** | Adds every cell on the current page to the selection |
| Previous / next page | **← / →** | Arrow keys page the grid |
| Jump to page | Type a number in the page box | The box next to "第 x / y 页" jumps as you type |
| Search | Click the search box, then type | Filters by Chinese name, English name, full pinyin or pinyin initials |
| Abort retrieval | **ESC** | Cancels Baritone pathing and clears the take queue, then closes the screen |
| Close | **ESC** (when nothing is running) | Closes the screen |

### Buttons

| Button | Action |
| --- | --- |
| `< 上一页` / `< Previous` | Previous page |
| `刷新` / `Refresh` | Re-read ChestTracker memory and rebuild the list |
| `下一页 >` / `Next >` | Next page |
| `取选中` / `Take selected` | Start retrieval for all selected cells |
| `清空选择` / `Clear selection` | Drop the selection (also stops keeping it across refreshes) |
| `配置` / `Config` | Open the mod config screen |

On small windows the second button row is dropped first; the `配置` button stays reachable from Mod Menu.

## R semantics

`R` (or whatever you rebind it to) does the smart thing:

1. **More than one cell selected** → take the whole selection (same as Tab / 取选中).
2. **Nothing multi-selected, a cell is hovered** → take the hovered cell only.
3. **Exactly one cell selected, nothing hovered** → take that one selected cell.
4. Nothing selected and nothing hovered → nothing happens.

## Notes

- While a text box (search or page number) has focus, typing goes to the box: `R`, `←/→` and `Ctrl+A` are not treated as hotkeys.
- The mouse wheel pages even when the cursor is over the search box.
- GUI actions (clicks, Tab, arrows, mouse wheel) cannot be rebound.
- The cancel hotkey (default **ESC**) is only intercepted while a retrieval is running. It is registered with "cancel on handle", so the game does not also open the pause menu. With nothing running, ESC is untouched.
