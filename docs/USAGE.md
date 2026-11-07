# Usage Guide

> 中文版：[USAGE.zh-CN.md](USAGE.zh-CN.md)

A practical walkthrough of Storage Radar. For the key table see [KEYBINDS.md](KEYBINDS.md); for every option see [CONFIG.md](CONFIG.md).

## 1. Before the first use

Storage Radar does not scan the world. It reads **ChestTracker's memory**, which is filled while you play:

1. Install ChestTracker (a 1.21.11 build) and this mod.
2. Open containers normally — every container you open is recorded with its contents.
3. Open them again after moving items around, so the memory matches reality.

A container that has never been opened does not exist for the radar.

## 2. Opening the radar

- Press **B** (default) while in a world.
- The radar opens as a full-screen GUI.

If a message appears instead, it tells you what is missing: enter a world first, or install ChestTracker.

## 3. Reading the screen

```
                [ search box: 搜索物品名 / Filter ]
 ┌──────────────────────────────────────────────────┐
 │  container info   9 × 6 grid of item cells       │   status / take progress
 └──────────────────────────────────────────────────┘
           [< 上一页] [刷新] [下一页 >]
        [ page number box ] 第 1 / 3 页
 ┌──────────────────────────────────────────────────┐
 │  your inventory (4 rows)                         │
 └──────────────────────────────────────────────────┘
```

- **A cell = one slot of one container = one stack.** Nothing is merged: three stacks of diamonds are three cells, even inside the same chest.
- **Hover** a cell to see its tooltip. With "Show container location" on, the container name, its coordinates, the slot index and the distance are drawn to the left of the grid.
- The **left hint text** repeats the mouse gestures; the **right side** shows item count, page number, selection size and live retrieval progress.
- The **inventory panel** is drawn just above your hotbar so you can see what you already have.

## 4. Finding an item

Use the search box at the top. Matching is case-insensitive and accepts:

- Chinese item names: `钻石`
- English item names: `diamond`
- Full pinyin: `zuanshi`
- Pinyin initials: `zs`

Search matches the item name only. It is not a regex; plain substrings work best.

Without a search, the list is sorted by:

- **stack size, largest first, then distance** when "Sort by count" is on (default), or
- **distance** when it is off.

Sort by count is handy for finding bulk materials; turn it off to find the nearest copy of something.

## 5. Selecting cells

| Gesture | Selection result |
| --- | --- |
| Left click | Toggle one cell |
| Ctrl + left click | Only this cell |
| Shift + left click | Range from the anchor to the clicked cell (can span pages) |
| Alt + left click | Add every identical stack on the current page |
| Ctrl + A | Add the whole page |
| Clear selection button | Empty the selection |

The selection survives a **Refresh** as long as the same container slot still exists.

## 6. Taking items

### One slot

- **Right click** a cell: take that slot immediately (the selection is not changed).
- Or hover a cell and press **R**.

### Several slots

1. Select the cells you want.
2. Press **R** (or **Tab**, or click **取选中**).

### What happens next

1. The radar screen is closed (if "Close GUI after taking" is on) and Baritone starts walking to the first container.
2. On arrival the mod right-clicks the container, opens it and **shift-clicks the exact slot** (a normal quick-move, exactly one stack).
3. It waits for the server to confirm that the item arrived, then takes the next selected slot **in the same container without closing it**.
4. When every selected slot in that container is done, it closes the container and walks to the next one.
5. Progress is reported in the action bar (`[container 2/3] heading to …`, `taking …`, `confirming …`). The status stays on screen for about 4 seconds after the last message and fades out.

The result line reports the **target** count (what the cache said the stack had) and the **actually taken** count (how much really appeared in your inventory). If the cache was stale, the actual number can be lower — the mod then reports that the slot was empty or moved.

### Containers in another dimension

Not supported. Only the current dimension is listed and retrieved.

## 7. Stopping and refreshing

- **ESC** (the cancel hotkey, rebindable) cancels a running retrieval anywhere in the world: Baritone stops, the queue is cleared, and the keypress is consumed so the pause menu does not open.
- Inside the radar screen, **ESC** aborts the queue and closes the screen.
- **Refresh** re-reads ChestTracker's memory. Use it after opening a container again or after a stale-cache message.
- If the take gets interrupted (you die, change dimension, close a container by hand), press ESC or reopen the radar and start again.

## 8. Small windows / large GUI scale

The layout is adaptive: it first shrinks the number of grid rows, then removes the second button row, then the inventory panel. If even that does not fit, only the search box stays and a message asks you to enlarge the window or lower GUI scale. At normal scales all of it fits.

## 9. Practical tips

- Keep the radius moderate (16–32). It only filters the cached list, so a big radius costs no world scanning, but a huge list is harder to browse.
- Name your storage rooms' containers and turn on **Only named containers** if you keep decorative chests around.
- Turn **Sort by count** off when you want the nearest source instead of the biggest stack.
- Leave **Allow breaking while pathing** off unless Baritone keeps getting stuck; the mod restores your previous Baritone setting when done.
- Automated retrieval may break server rules — check before using it on a public server.

## 10. Known limitations

- Only the **current dimension**.
- Only containers **ChestTracker remembers** (opened at least once).
- Cache counts are a snapshot and can be stale.
- Containers farther than ~4.5 blocks need **Baritone**.
- One retrieval moves one stack per slot; it does not "take all of this item type" across the world in one click (select the cells you want — Alt+click makes that fast).
