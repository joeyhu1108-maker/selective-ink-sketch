---
name: selective-ink-sketch
description: Turn a user-uploaded photograph into an original monochrome observational pen-and-ink sketch through deliberate omission, negative space, density control, and source fidelity. Use when the user asks for 钢笔速写, 建筑速写, 风景速写, 人物速写, 肖像速写, photo-to-ink sketch, architectural sketch, landscape sketch, figure sketch, portrait sketch, or wants an attached JPG/PNG/WebP photo redrawn with selective hand-drawn ink lines. Support global architecture, streets and spaces, mountains and natural scenes, full- or half-body figures, and portraits. Require a real source photo; do not use for text-only illustration briefs, watercolor, pencil, charcoal, vector tracing, or unrelated image styles.
---

# Selective Ink Sketch｜取舍钢笔速写

把一张真实照片转译成独立的钢笔速写成稿。先观察、再删除、最后落线；不要把照片机械描边。

## 核心原则

- 保住照片中使主体可识别的结构、姿态、比例和身份特征。
- 动态人物先锁定造型律动，再决定破型和透视夸张；优先级为 `gesture rhythm > form breaking > perspective exaggeration > detail`。
- 默认删除照片约 40%–60% 的可见信息。
- 只设置一个主密度中心，最多两个次级中心。
- 主密度中心必须选择一种局部刻画主方法：`ink-mass`、`directional-hatching` 或 `corrective-overdraw`；不要三种平均铺满全图。
- 用空白组织画面；不要用均匀排线填满照片的每个区域。
- 允许寻找形体的轻线、断线、回看线和少量重复修正线。
- 允许在运动、遮挡、受力和结构交接处“破型”：打断轮廓闭合，让穿出线、墨块与空白共同重建形体；不得破坏主体数量、解剖或建筑结构。
- 只在结构承重、交叠、转折或身份锚点处使用重线。
- 输出纯粹的速写成稿，不出现手、画本、桌面、现场照片或生成过程。

## 已确认黄金样例

默认视觉机制以 [assets/golden-style-snow-mountain-selective-ink.png](assets/golden-style-snow-mountain-selective-ink.png) 为通过样例。生成前可检查真实资产，但运行时不得把它作为第二张风格参考图；源照片仍是唯一编辑目标。

只迁移下列机制，不复制样例里的雪山、人物、峰形或构图：

- **单一高完成度锚点：** 约 5%–15% 画面承担重点刻画，完成度向外至少下降两级。
- **空白承担对象：** 纸面可直接成为天空、雪、云雾、水面、墙面或衣服，不必给每个对象补完整轮廓。
- **黑白灰差异：** 深黑只落在真实凹部、交叠、接触或尺度标记；中间灰只来自可见排线疏密。
- **雾与空气：** 通过线条消失、山体被白纸切断和错位重启表现，不使用灰洗或柔和晕染。
- **尺度人物：** 环境中的小人物压缩为少量决定性线段或墨结，不与主景争夺完成度。
- **现场笔触：** 保留轻重、干涩、停顿、寻找线和少量修正，不追求机械干净的等粗描边。

## 工作流

1. **确认输入。** 必须有一张照片作为编辑目标。若照片不可访问，要求用户重新上传；不要仅凭文字想象原图。
2. **检查原图。** 打开并观察照片，记录主体、方向、裁切、透视或动态线、识别锚点、遮挡和背景干扰。
3. **选择模式。** 按下表选择一个模式，不要把四种模式平均混合。
4. **做取舍图。** 在生成前列出 `保留 / 简化 / 删除`：
   - `保留`：主体轮廓、主要结构或动作、识别锚点、一个密度中心，并为密度中心指定一种局部刻画主方法；
   - `简化`：次级建筑、衣褶、植被、地面、配件；
   - `删除`：天空细节、无关路人、杂乱电线、伪文字和无助于识别的纹理。
5. **读取规范。** 始终读取 [references/style-system.md](references/style-system.md)。写最终图像提示词时读取 [references/prompt-recipes.md](references/prompt-recipes.md)。若使用默认视觉机制，同时检查黄金样例的密度断层、空白功能和墨色比例；不要提取其具体题材。
6. **执行编辑。** 使用当前环境可用的图像生成/编辑工具，把源照片作为唯一编辑目标；运行时不要再附带风格参考图。除非用户只要 Prompt，否则直接生成图像。
7. **检查结果。** 读取 [references/quality-gates.md](references/quality-gates.md)，同时检查全尺寸和缩略图。未通过时只修正失败维度，再编辑一次；不要无目的地重做整张图。
8. **交付。** 用户只要图片时，显示生成图并附一句质检说明。用户只要 Prompt 时，只返回可复制 Prompt。

## 模式选择

| 模式 | 识别条件 | 第一任务 | 默认留白 |
|---|---|---|---|
| `architecture` | 建筑、街巷、室内外空间为主 | 保住轮廓、透视轴和地域结构特征 | 35%–55% |
| `landscape` | 山地、海岸、田野、森林或自然场景为主 | 保住地貌轮廓、主走势、尺度关系和一个结构锚点 | 55%–75% |
| `figure` | 全身或半身人物、动作和服装为主 | 保住动态线、重心、肩胯和身份配件 | 55%–75% |
| `portrait` | 头部或面部占主体 | 保住脸型、五官比例、表情和识别锚点 | 35%–60% |

若人物与环境同时出现：人物只用于尺度时选 `architecture` 或 `landscape`；人物占主要面积或叙事中心时选 `figure`；脸部占画面主要面积时选 `portrait`。

## 默认参数

- `density`: `standard`
- `paper`: 暖白或自然白的轻微纸张肌理
- `ink`: 近黑色单色墨线
- `crop`: 跟随原照片方向与主体关系
- `field-note`: `off`
- `background`: 主动删除或降到最低信息量
- `focus-rendering`: `auto`，从 `ink-mass / directional-hatching / corrective-overdraw` 中只选一种主方法
- `form-breaking`: `controlled`；动态强烈或用户明确要求“破型”时使用 `strong`
- `gesture-rhythm`: `source-locked`；不得为了夸张近大远小而改掉主动态线、反向支撑线和肢体负形

用户说“更松”时使用 `loose`；说“更细致”时使用 `dense`。无论密度如何，都必须保留空白和单一主焦点。

## 现场注记

默认不生成姓名、日期、题字、印章、水印或伪招牌。只有用户明确提供完整文字并要求添加时，才启用 `field-note`：把原样文字小尺寸放在底角，不模仿陌生艺术家的签名，不自行补日期。

## 硬性禁止

- 不得输出照片滤镜、边缘检测、阈值描边或矢量描摹感。
- 不得使用水彩、铅笔、炭笔、马克笔、灰度喷枪、渐变阴影或彩色墨水。
- 不得让每个物体拥有同样粗的完整轮廓。
- 不得让每面墙、每块衣服、每片皮肤都布满排线。
- 不得美化人物、改变年龄体型、增删肢体或制造额外手指。
- 不得给不同地域的建筑套用同一种中式屋檐、欧式装饰或虚构细节。
- 不得自动添加边框、圆形宣纸、装裱、画本线圈、手或摄影现场。
- 不得生成虚构文字、签名、日期、印章或水印。
