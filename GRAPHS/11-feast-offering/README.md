# 11 — Feast — Dish Placement and Diner Activation

**第五关：献菜、落位与食客活动**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 第五关献菜触发器或关卡蓝图、FinalDish、十二位食客的动画调用。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 11-01 | `11-01-offering-and-placement.txt` | **献菜到桌面落位**：第五关从献菜碰撞/接收事件开始，复制到 FinalDish 目标位置更新及落位结束。 |
| 11-02 | `11-02-diner-activation.txt` | **十二位食客活动**：复制献菜之后如何让十二位食客开始动画；若使用数组/循环，保留数组输入与动画设置。 |

**还需补充：** 附食客动画对象引用及触发前后截图。不要把“献菜”与后面 TL_DishHit 的“刺中反馈”混为同一段。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
