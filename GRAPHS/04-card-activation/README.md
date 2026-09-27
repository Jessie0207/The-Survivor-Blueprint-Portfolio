# 04 — Tarot Activation and Level Entry

**卡牌激活、视觉响应与进入关卡**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** BP_TarotCard → ActivateTarotCard 自定义事件及其后续执行链。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 04-01 | `04-01-activation-and-motion.txt` | **卡牌激活与升起旋转**：BP_TarotCard：从 ActivateTarotCard、IsActivated 判断复制到升起/旋转/漂浮的更新节点。 |
| 04-02 | `04-02-selection-and-level-entry.txt` | **记录选择、淡出、开关卡**：同一执行链继续复制 Delay → GameInstance → ActiveCardIndex / ReturnFadeColor → 淡出 → Open Level。 |

**还需补充：** 附卡牌各 Timeline 的曲线与时长、CardIndex 和目标地图的实例配置。不要把自定义事件误写成函数。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
