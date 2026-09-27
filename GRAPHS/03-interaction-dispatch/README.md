# 03 — Interaction Dispatch and Door Fallback

**交互分发与门交互回退**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** XRPawn → TryInteract、TryOpenFocusedDoor。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 03-01 | `03-01-try-interact.txt` | **卡牌优先的交互分发**：打开 TryInteract，复制入口、Is Valid、卡牌激活和门回退两条分支。 |
| 03-02 | `03-02-try-open-focused-door.txt` | **门交互验证和调用**：打开 TryOpenFocusedDoor，复制目标有效性检查至门响应调用。门的动画另放模块 08。 |

**还需补充：** 附 FocusedTarotCard、门目标变量的类型。截图要让两个分支和调用名都能读清。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
