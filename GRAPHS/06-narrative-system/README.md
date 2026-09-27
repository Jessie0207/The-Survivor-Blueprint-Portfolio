# 06 — Spatial Narrative Cues and Audio Timing

**空间文字触发、浮动文本与旁白时序**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 实际 NarrativeTrigger / 浮动文字 Actor / 文字 Widget；先从 ShowNow 的调用找到当前资产。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 06-01 | `06-01-narrative-trigger.txt` | **玩家进入叙事区域**：从场景中的文字触发盒打开所属蓝图，复制玩家识别、触发条件和调用文字/音频的完整链。 |
| 06-02 | `06-02-show-now-and-text.txt` | **ShowNow 与文字显示**：顺着 ShowNow 打开实际接收对象，复制显示/隐藏及相关文字更新。若为 Widget，还要留 Designer 和动画轨道图。 |
| 06-03 | `06-03-narration-timing.txt` | **声音与文字时序**：复制当前负责播放、延迟或等待结束的节点。只保留真实实现，不凭印象补“自动按音频长度计算”。 |

**还需补充：** 提供当前实际台词表或实例参数；作品集中的 T1–T3 概括不要标成逐字游戏台词。声音文件本体可以不放公开仓库，登记资产引用即可。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
