# Changelog

All notable changes to Storage Radar are documented here. Each release is written in Chinese and English.

---

## 1.0.0 — 2026-11-07

### 中文

- 首个公开发布版本，适用于 Minecraft 1.21.11 / Fabric。
- 存储雷达界面：列出检索半径内 ChestTracker 记录过的容器物品，9×6 格分页展示。
- 槽位级展示：一行 = 一个容器槽位里的一组物品，不做合并。
- 中英双语搜索，支持中文名、英文名、全拼与首字母。
- 多选：左键切换、Ctrl 单选、Shift 连选、Alt 选本页相同、Ctrl+A 全选本页；右键单格取物。
- 批量取物按容器归并：一个容器一次行程、箱内逐格取完；Baritone 自动寻路，`allowBreak` 双向强制并在结束后恢复。
- 取物过程中可按 Esc（可改键）立即取消：停掉寻路并清空队列，取消时按键被吞掉，不弹暂停菜单。
- 物品栏上方进度播报；取物结果提示停留约 4 秒，尾部 1 秒渐隐消失。
- masa 风格配置面板（中英双行），热键可在配置里修改。
- Mod Menu 图标与作者信息：YXiaoIBaiY B站爱吐槽的小白。
- 不含 mixin，只用公开 API。

### English

- First public release for Minecraft 1.21.11 / Fabric.
- Storage Radar screen: lists items inside every container ChestTracker has recorded within the configured radius, in 9×6 cell pages.
- Slot-level rows: one row = one stack in one container slot; nothing is merged.
- Bilingual search: Chinese names, English names, full pinyin and pinyin initials.
- Selection: left click toggles, Ctrl single-selects, Shift range-selects, Alt selects identical stacks on the page, Ctrl+A selects the page; right click takes a single slot.
- Batch retrieval groups by container: one trip and one opening per container, every selected slot inside it taken; Baritone pathing with bidirectional `allowBreak` forcing and restore afterwards.
- Press ESC (rebindable) to cancel a running retrieval: pathing stops, the queue is cleared, and the keypress is consumed so no pause menu opens.
- Action-bar progress; the result message stays for about 4 seconds and fades out during the last second.
- masa-style config panel (bilingual rows), hotkeys rebindable in the config screen.
- Mod Menu icon and author: YXiaoIBaiY B站爱吐槽的小白.
- No mixins; public APIs only.
