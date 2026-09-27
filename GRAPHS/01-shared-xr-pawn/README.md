# 01 — XR Pawn Extension and Desktop Input

**XR Pawn 扩展与键鼠输入**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 你当前使用的 XRPawn；以工程中实际资产名为准。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 01-01 | `01-01-desktop-input.txt` | **自定义键鼠移动、视角和交互入口**：XRPawn → Event Graph：从键鼠输入事件开始，复制到移动/视角更新或 TryInteract 调用结束。已有函数分别导出，别只复制 Event Graph。 |
| 01-02 | `01-02-vr-input-routing.txt` | **VR 交互输入与项目函数的连接**：XRPawn → Event Graph：复制当前手柄输入如何进入你的卡牌/门交互。保留抓取判断和实际分支，不把它改写成假定的统一输入。 |

**还需补充：** 附实际使用的 Input Action / Input Mapping Context、Pawn 的 Components 树和相关变量。官方模板未改动的整套传送逻辑不必反复截图。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
