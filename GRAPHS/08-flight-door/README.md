# 08 — Flight — Door Reveal and Passage

**第二关：门显现、开启与通过**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 第二关门的接近触发与出口门蓝图；旧记录名 BP_ExitDoor，按工程核对。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 08-01 | `08-01-door-reveal.txt` | **靠近后的门显现**：找到控制门隐藏/显示或出现动画的触发点，复制到实际视觉响应。不要只截门模型。 |
| 08-02 | `08-02-door-open.txt` | **门交互与动画**：打开当前出口门蓝图；旧记录可搜索 BP_ExitDoor、OpenDoor、TL_OpenDoor。复制真实调用与更新位置/旋转的逻辑。 |
| 08-03 | `08-03-door-crossing-return.txt` | **通过门与回店**：从穿过门的检测事件复制到叙述、完成写入和返回。 |

**还需补充：** 第二关文案以你确认的 First to Cross 为准。输入通道和距离保留当前设置，别照搬早期测试值。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
