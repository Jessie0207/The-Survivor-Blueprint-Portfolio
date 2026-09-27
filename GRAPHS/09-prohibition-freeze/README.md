# 09 — Prohibition — Automatic Travel and Staged Stillness

**第三关：蜘蛛行进与分阶段冻结**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 第三关蜘蛛/载具的行进控制，以及控制环境停止的关卡或管理蓝图。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 09-01 | `09-01-spider-travel.txt` | **自动行进**：从蜘蛛或承载玩家的 Actor 打开蓝图，复制行进开始、更新和停止入口；若引用路径，附路径实例设置。 |
| 09-02 | `09-02-staged-freeze.txt` | **鸟、水、音乐、玩家依次停止**：复制控制停止顺序的主链，保留每次调用的真实目标及延迟/时间驱动方法。 |

**还需补充：** 附停止前后同机位截图和受控对象列表。若黑丝带 Niagara 的播放也由蓝图控制，可把调用附在本模块；材质/粒子资产只登记实际使用项。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
