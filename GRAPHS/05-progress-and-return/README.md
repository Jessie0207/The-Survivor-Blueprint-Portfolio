# 05 — Encounter Completion and Shop State Restoration

**关卡完成记录、返回与商店恢复**

**Status:** export guide prepared; original graph text, screenshots and BlueprintUE URLs pending.

**Open in Unreal / 在哪里找：** 项目 GameInstance、各关返回逻辑、BP_TarotCard → BeginPlay、TheShop 的终章条件检查。

[Module overview](../../README.md) · [Export instructions](../../DOCS/EXPORT_GUIDE_ZH.md)

| Graph ID | Save node text as | 内容及复制范围 |
| --- | --- | --- |
| 05-01 | `05-01-completion-write.txt` | **完成状态写入**：各关结束前找到写入完成记录的节点，连同当前关卡/卡牌身份和返回调用导出；如果五关复用同一函数，导出一次并注明五处调用。 |
| 05-02 | `05-02-shop-card-restoration.txt` | **回店后的卡牌状态恢复**：BP_TarotCard → Event BeginPlay：复制 CompletedCardCount / ActiveCardIndex / CardIndex 的判断，到燃烧或已燃烧状态设置。 |
| 05-03 | `05-03-ending-condition.txt` | **全部完成判定**：TheShop 或实际管理蓝图中找到终章调用，向前复制真正控制它的完成条件。 |

**还需补充：** GameInstance 没有复杂节点时，也要导出其 .uasset，并附变量、类型、默认值；逐关核对写入点。检查当前实现是计数、逐卡记录还是两者结合，不能凭旧方案填数组名。

**Export record / 导出后记录**

| Field | Value |
| --- | --- |
| Source asset or map path | Pending export |
| Graph / function / event names | Pending export |
| Native asset archive path | Pending export |
| BlueprintUE URLs | Not published |
| Screenshot filenames | Pending capture |
| Current-build check | Not recorded |
