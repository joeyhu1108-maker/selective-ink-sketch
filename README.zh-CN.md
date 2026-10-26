# Selective Ink Sketch｜取舍钢笔速写

把用户上传的真实照片转成有取舍、有留白、保留现场笔触的黑白钢笔速写。支持全球建筑、街巷空间、自然风景、人物动态、群像与肖像。

> **商用须事先获得作者胡卓熠（Joey Hu）的明确书面授权。** 非商业学习、研究与分享可免费使用；商业集成、转售、收费服务、客户交付、品牌宣传，以及将生成作品用于商业项目，均须授权。署名、Star 或 Fork 不等于商用授权。完整条款见 [LICENSE.md](LICENSE.md)。

## 核心特点

- 一张照片是唯一事实来源，不机械描边，也不凭空发明结构。
- 每张图只设一个高完成度锚点，其他区域主动降级为基础线、骨架或空白。
- 纯黑色钢笔线；灰度只来自可见排线疏密，不使用水彩、墨水晕染或柔和渐变。
- 保留断线、寻找线、错位重启、干涩缺口和少量修正线，避免矢量化与 AI 插画腔。
- 人物优先保证造型律动；建筑优先保证地域结构与透视；风景优先保证地貌轮廓、尺度和空气留白。

## 使用方式

上传一张 JPG、PNG 或 WebP 照片，然后说：

```text
使用 Selective Ink Sketch，把这张照片转成我的钢笔速写。
```

可继续补充：

- `更松，留白再多一点`
- `只刻画门楼，周围快速省略`
- `人物动态优先，破型 strong`
- `不要晕染，中间灰只用方向性排线`

## 黄金样例

- [通过样例：雪山选择性钢笔速写](assets/golden-style-snow-mountain-selective-ink.png)
- [对应源照片](assets/example-source-snow-mountain.jpg)

黄金样例只用于理解“单一局部刻画、空白承担云雪、深黑集中、线条逐级消失”的机制。运行时仍只提交用户自己的源照片，不把样例作为第二张风格参考图。

## 文件结构

```text
selective-ink-sketch/
├── SKILL.md
├── README.zh-CN.md
├── LICENSE.md
├── agents/openai.yaml
├── assets/
├── evals/evals.json
└── references/
```

## 许可与商业授权

本项目采用 [Selective Ink Sketch 非商业使用许可 v1.0](LICENSE.md)，以公开源码、非商业许可方式提供。复制、修改或再分发时须保留署名、许可全文和原仓库链接，并说明是否作过修改。

需要商用，请[提交商业授权申请](https://github.com/joeyhu1108-maker/selective-ink-sketch/issues/new?title=Commercial%20license%20request)，简述申请主体、用途、使用方式和预计范围；公开 Issue 中请勿提交私人资料或商业机密。只有作者的明确书面许可或另行签署的协议构成授权，提交申请或未收到回复均不代表获准。

生成作品的商业使用限制属于使用本 Skill 的许可条件，不代表作者主张所有生成作品的版权。第三方照片、肖像、商标和模型服务等权利仍须另行处理，完整边界以 [LICENSE.md](LICENSE.md) 为准。
