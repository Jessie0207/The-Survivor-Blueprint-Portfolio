# 14 — Feast — Chandelier Fall

**第五关：吊灯坠落**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 包含 TL_ChandelierFall 并引用 BP_FeastChandelier 的实际图；你已经截过这段。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 14-01 | `14-01-chandelier-fall.txt` | **吊灯位置插值与更新**：复制 TL_ChandelierFall → Lerp (Vector) → SetActorLocation，以及起止位置来源和 BP_FeastChandelier 引用。 |
| 14-02 | `14-02-fall-completion.txt` | **坠落结束后的调用**：从 Timeline Finished 或实际完成条件复制到声音/过渡/返回调用；没有某项就不要补写。 |

**还需补充：** 附 Timeline 曲线和坠落前后实机图。按现有图写 Timeline 驱动，不能改说成物理自由落体。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
