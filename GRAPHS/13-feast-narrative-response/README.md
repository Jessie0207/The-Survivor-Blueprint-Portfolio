# 13 — Feast — Stab Response and Narrative Timing

**第五关：刺入反馈与叙事时序**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 第五关接收 On Dish Stabbed (TRG_StabDish) 的图；你已在作品集截过这一块。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 13-01 | `13-01-stab-scene-response.txt` | **刺入事件及场景反馈**：复制 On Dish Stabbed (TRG_StabDish) → Sequence 及音频/ShowNow/反馈分支。需要延续到吊灯启动调用，但吊灯更新可放模块 14。 |
| 13-02 | `13-02-dish-hit-timeline.txt` | **食物被刺后的位移反馈**：复制 TL_DishHit → FinalDish → SetWorldLocation 的实际连线，另附 Timeline 曲线与起止位置来源。 |

**还需补充：** 使用现在修好的时序。已完成的改动可以写入说明，但不要新增“用户测试改善百分比”等没有记录的结果。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
