# 02 — Tarot Targeting and Focus Feedback

**塔罗牌射线定位与悬停反馈**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** XRPawn → UpdateTarotFocus；卡牌蓝图中接收焦点变化的事件。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 02-01 | `02-01-update-tarot-focus.txt` | **完整的卡牌目标定位函数**：打开 UpdateTarotFocus，复制函数全图。过宽时截图分成“射线来源”和“命中及更新焦点”，但文本保留完整函数。 |
| 02-02 | `02-02-card-focus-feedback.txt` | **卡牌获得与失去焦点**：顺着 UpdateTarotFocus 对卡牌的调用，打开实际接收事件，复制亮起/取消亮起的逻辑。旧记录出现过 TarotFocusOn 和 Overlay，按当前工程核对。 |

**还需补充：** 附射线通道设置、相关变量类型，以及实际使用的高亮材质/材质实例说明。别把 FocusedTarotCard 当作一个函数单独寻找。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
