# The Survivor：GitHub 蓝图归档与上传指南

这份整理沿用你项目一的“英文 README 分模块说明 + BLUEPRINTS 原始蓝图 + BlueprintUE 在线查看”逻辑，并增加节点文本、截图与导出登记，方便教授阅读和你自己维护。

**当前已完成的是文档和收集目录。当前包里没有你的原始 .uasset、节点文本、蓝图截图或新 BlueprintUE 链接。**这些必须从正在使用的 UE 工程导出。说明文档不等于源代码，不能把这份初始包称为“完整工程源码”。

## 1. 仓库怎么命名

建议新建独立仓库：**The-Survivor-Blueprint-Portfolio**。

也可以延续项目编号命名，但不要把本项目覆盖进 Project1-Blueprint-Portfolio。你发来的项目一仓库只作为结构参考。

GitHub Description 可直接填：

> Custom Unreal Engine 5.7 Blueprint systems for The Survivor, a VR experience with desktop input support.

README 已写好英文主体。开头的 Archive status 要保留到真实源文件补齐；实际补完后再根据内容改状态。

## 2. 哪些东西分别放在哪里

| 文件/内容 | 放置位置 | 用途 |
| --- | --- | --- |
| 英文项目介绍和 16 个模块说明 | 根目录 README.md | 教授先读的首页 |
| 原始蓝图资产 .uasset | BLUEPRINTS/Content/原来的子目录/ | 保留真实资产；一个资产只放一次 |
| 从 UE 复制的节点文本 .txt | GRAPHS/对应模块/ | 便于检查、复制及上传 BlueprintUE |
| 清晰节点截图 | IMAGES/ | 不打开 UE 也能看清实现 |
| Timeline 曲线、变量、组件和 Widget 图 | IMAGES/ | 补充节点文本无法完整说明的信息 |
| BlueprintUE 网址 | 对应模块 README 和清单 | 在线查看真实图；现在不填假链接 |
| 原始资产路径与模块关系 | DOCS/NATIVE_ASSET_REGISTER.csv | 避免漏文件和重复归档 |
| 每段图的来源与进度 | DOCS/GRAPH_EXPORT_CHECKLIST.csv | 逐项完成收集 |

模块名是整理用的标题，不要求你在 UE 里把资产全部改名。

## 3. 按什么顺序收集

先收已经能明确定位的共享函数及第五关图，再补其他关卡。以下 16 块都已经写入 README。

| 模块 | 先打开哪里 | 要收什么 |
| --- | --- | --- |
| 01 XR Pawn 扩展 | XRPawn → Event Graph | 自己增加的键鼠输入；手柄输入接入自定义交互的部分 |
| 02 卡牌定位 | XRPawn → UpdateTarotFocus | 射线来源、命中、FocusedTarotCard，以及卡牌高亮接收端 |
| 03 交互分发 | TryInteract；TryOpenFocusedDoor | 卡牌有效性检查、ActivateTarotCard 调用、门回退 |
| 04 卡牌响应 | BP_TarotCard → ActivateTarotCard | 激活判断；升起旋转；记录 ActiveCardIndex / ReturnFadeColor；开关卡 |
| 05 进度与返回 | GameInstance；卡牌 BeginPlay；各关结束处 | 完成记录写入、回店读取、牌消失、全部完成检查 |
| 06 文字叙事 | NarrativeTrigger；ShowNow 的接收对象 | 触发、显示、音频时序、Widget 与动画 |
| 07 第一关 | 铃铛交互对象/第一关 Level Blueprint | 敲铃→声音/叙述→完成/返回 |
| 08 第二关 | 门的接近触发；当前出口门蓝图 | 显现、开启、穿门检测；旧名 BP_ExitDoor 仅作定位参考 |
| 09 第三关 | 蜘蛛运动和场景冻结控制 | 自动行进；鸟→水→音乐→玩家/蜘蛛停止 |
| 10 第四关 | 小沙漏交互及场景接收端 | 输入、翻转、王冠/人物响应、叙述和返回 |
| 11 第五关献菜 | 献菜触发/第五关 Level Blueprint | FinalDish 落位、十二位食客动画、后续阶段 |
| 12 第五关刀具 | 刀具/手部及刺入目标 | 抓握或附着、自定义偏移、刺入识别和事件发出 |
| 13 第五关反馈 | On Dish Stabbed (TRG_StabDish) | Sequence、音频/ShowNow、TL_DishHit 和现在修好的时序 |
| 14 第五关吊灯 | TL_ChandelierFall 所在图 | Lerp(Vector)→SetActorLocation，起止位置和完成出口 |
| 15 商店终章 | TheShop 终章图 | 第六张牌、分批火焰、灯光与旁白 |
| 16 结尾黑屏 | 眨眼控制图和最终标题 Widget | 黑→恢复→再黑；最终标题和结束状态 |

每块的 GRAPHS 子文件夹内还写了更具体的复制范围和保存文件名。

## 4. 节点文本怎样导出：以 TryInteract 为例

1. 在 UE 打开当前 XRPawn。
2. 在 My Blueprint 面板中双击 **TryInteract**，进入函数图。
3. 点击节点画布空白处，让焦点落在图里；按 **Ctrl+A** 选中这个图的节点，再按 **Ctrl+C**。
4. 打开记事本，把内容粘贴进去。真实节点文本一般包含 `Begin Object`、节点类和引脚信息；不是你手打的一段流程描述。
5. 以 UTF-8 保存为 **03-01-try-interact.txt**，放进 **GRAPHS/03-interaction-dispatch/**。确认没有被记事本保存成 `.txt.txt`。
6. 再截一张能看清函数入口、Is Valid 和两个分支的图，保存到 **IMAGES/03-01-try-interact.png**。
7. 在 **GRAPH_EXPORT_CHECKLIST.csv** 的 03-01 行填写来源资产路径、实际图名、链接和状态。

节点文本用于保存图的内容，不等于一个可以单独运行的完整 Blueprint。调用的函数、变量、组件和依赖需要一起登记。

## 5. Event Graph、函数、Timeline、关卡蓝图各怎么收

**Event Graph**

如果一张图放了很多互不相关的事件，不要只截一张缩到看不清的大图。按本指南的模块选中完整事件链分别复制；一段必须包含入口、关键判断、主要调用和结束结果。与别的模块共用的函数只归档一次。

**函数与宏**

在 My Blueprint 中逐个打开你增加或修改的函数/宏。只在 Event Graph 按一次 Ctrl+A 不会替你导出所有函数的内部实现。

**Timeline**

保留 Timeline 节点及它驱动的更新图；再双击 Timeline，截图曲线、轨道名、长度和循环设置。不要假定一段复制的节点文本就完整保存了曲线。原生资产也是需要的。

**Level Blueprint：尤其容易漏掉**

先打开对应关卡，在关卡编辑器工具栏的 **Blueprints → Open Level Blueprint** 进入关卡蓝图。TheShop 和五个关卡都要查一次。第五关场景接收事件、吊灯控制或商店结尾，可能写在这里。

Level Blueprint 属于地图，不会作为独立普通 Actor 蓝图出现在 Content Browser 里。展示仓库至少要有其节点文本、截图、实际地图路径和 Actor 引用说明；若要归档其原生来源，也需保存对应地图及必要依赖，而不是只拿几个 BP_*.uasset 就说代码齐了。

**Widget 和输入资产**

文字 Widget、黑屏/标题 Widget 要附 Designer、相关动画和 Event Graph。新增/修改的 Input Action、Input Mapping Context、GameInstance、接口、枚举、结构体、函数库也要检查，登记实际引用的项。

## 6. 原始 .uasset 怎样整理

1. 在当前 UE 工程先 **Save All**。
2. 在 Content Browser 找到要归档的实际蓝图，右键使用 **Show in Explorer / 在资源管理器中显示**，定位文件。
3. 为这个“代码展示归档”复制原始文件到独立整理目录，保留相对 Content 的原目录。不要移动或重命名原工程中的文件，也不要把整理目录当作可直接回拷的运行工程。
4. 一份 XRPawn 可以对应 01、02、03 等多个模块，原生文件只存一份。清单里写模块关联即可。
5. 原始蓝图依赖的模型、音频、材质、地图实例等没有一起发布时，要保留 README 中“非独立可运行工程”的说明。

如果目标改成“别人下载后直接打开运行”，需要另外用 UE 的 **Asset Actions → Migrate** 处理依赖，并准备真实 `.uproject`、配置及必要资源；这比你项目一式的代码展示仓库多一层工作。当前整理按展示仓库进行。

购买的火焰、商店资源和音乐不需要整包放进公开代码仓库；这里记录它们被自定义蓝图调用的方式与来源。

## 7. BlueprintUE 怎样和 GitHub 对应

你项目一的关键形式是每个模块都能在线打开蓝图。The Survivor 也用相同方式：

1. 把刚才从 UE 复制出的真实节点文本粘贴到 BlueprintUE 的新建蓝图页面。
2. 使用清楚的标题，例如 `The Survivor | 03-01 | TryInteract`。
3. 按网站当前可用选项记录 UE 版本；项目实际版本保持 **5.7**，不要为了填表把 README 改成别的版本。
4. 生成链接后，放进对应模块 README 的 Export record，并同步填写 CSV。
5. 把根 README 对应模块里的 `BlueprintUE: pending source export` 换成真正的链接，例如：

```markdown
[View Blueprint Graph on BlueprintUE](把实际生成的网址放这里)
```

这段是写法示例，不是可直接使用的链接。一个模块若包含两张独立函数图，可以有两个分别命名的链接。

## 8. 发布前核对这几件具体事情

- **第一关统一为 Baiting**，不要写 Bating，也不在这里又改回 Hunting。
- VR/键鼠写成 **VR pawn with desktop input support**；继承的 VR 模板基础与自定义逻辑分清楚。
- **CompletedCardCount 和逐卡完成记录不是同一回事**。用实际导出的写入/读取代码确定当前顺序与完成条件，不为迎合说明临时编一个数组。
- 第五关归档你**已经修好的版本**。叙事时序如何实现，按当前代码写；不强行指定它必须是之前讨论过的某种碰撞开关。
- 吊灯现有图是 **Timeline + Lerp(Vector) + SetActorLocation**，文档不称为物理自由落体。
- 两段视频和所有 BlueprintUE 地址都用真实链接。现在的包没有假定或生成这些地址。
- 没有保存到磁盘的系统，就只写“当前运行期间跨关卡保留”，不写退出重开还能恢复进度。

## 9. 上传 GitHub

1. 建立新仓库 **The-Survivor-Blueprint-Portfolio**。如果先放文档，就保留当前状态说明。
2. 解压文件包，进入同名文件夹。需要传的是里面的 `README.md`、`BLUEPRINTS`、`GRAPHS`、`IMAGES`、`DOCS` 等，**不要只上传整个 ZIP**。
3. 新仓库中使用 **Add file → Upload files**，上传这些内容；根 README 应位于仓库最外层。
4. 提交说明可写 `Add The Survivor technical documentation`。补上真实蓝图后另一次提交写 `Add current Blueprint source exports`。
5. 打开仓库首页检查 README、模块跳转、图片和 BlueprintUE 链接。

GitHub 网页上传单文件上限为 **25 MiB**，一次最多 **100 个文件**。文件较大或数量较多时改用 Git/GitHub Desktop；超过普通 Git 大小限制的文件需要正确配置 Git LFS。当前包没有自动启用 LFS，不会把普通网页上传伪装成 LFS 上传。

## 10. 最先可以发给我核对的一批

先发 **UpdateTarotFocus、TryInteract、TryOpenFocusedDoor、ActivateTarotCard、BP_TarotCard BeginPlay、GameInstance 的变量/完成写入、第五关 On Dish Stabbed 与 TL_ChandelierFall** 的节点文本或原生资产。

这些覆盖作品集代码页的主体。我拿到原始文本后，就能把现有概述逐条核对成准确节点说明，再继续补齐其余关卡；当前没有把缺失源代码重新编造出来。

## 参考

- 项目一结构：https://github.com/Jessie0207/Project1-Blueprint-Portfolio
- UE Level Blueprint：https://dev.epicgames.com/documentation/en-us/unreal-engine/level-blueprint-in-unreal-engine
- UE 资产迁移：https://dev.epicgames.com/documentation/unreal-engine/migrating-assets-in-unreal-engine
- GitHub 网页上传：https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository
