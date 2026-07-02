---
name: esther-design-system
description: 个人IP设计系统模板。做HTML页面、个人网站、教程页面、介绍页面、landing page等任何前端设计时自动触发。包含品牌DNA和多个场景子规范。
---

> ❗ **首次使用前必须完成配置：**
> 1. 默认品牌色是本仓库作者的蓝/黄/红三色，可直接使用。如需换成你自己的，修改 `brand-dna.md` 中的三色色值，并同步修改 `assets/template-*.html` 里 `:root` 的 CSS 变量（三色比例原则不变：主色60% / 强调色30% / 点缀色10%）
> 2. 将你的头像放入 `assets/avatar.jpg`（正方形，至少400×400px，仓库未附带此文件）
> 3. 如有IP形象，放入 `assets/character.png`
> 4. 把 `assets/template-cards.html` 中的作者名（Esther不二）替换成你自己的
> 5. 根据你的品牌调性修改 `brand-dna.md` 中的“气质关键词”和“禁忌清单”
>
> 不完成配置就直接用，出来的东西会是别人的风格。

触发条件：当用户要求制作HTML网页、个人页面、教程页面、介绍型页面、landing page、活动页面、App型页面、作品集等任何前端设计相关任务时触发。也在用户说“做图文”、“图文卡片”、“小红书图文”、“文章转卡片”、“转成图文”、“做卡片”时触发。

## 使用方式(7步工作流)

### Step 1: 澄清需求
向用户确认5个问题:
1. **类型** - 教程/介绍/科普?活动页/Landing?App型/功能型?**图文卡片?**
2. **受众** - 给谁看的?技术水平?
3. **Section数** - 大概几屏内容?
4. **素材** - 有哪些文案/图片/数据?
5. **硬约束** - 必须包含什么?有没有合作品牌色?

### Step 2: 读规范
1. **必读** `brand-dna.md` - 确认品牌底层规范
2. 根据类型选读场景文件:
   - 教程型/介绍型/科普型 → `references/scene-tutorial.md`
   - 活动页/分享会/Landing → `references/scene-landing.md`
   - App型/功能型(看板/书架/Canvas) → `references/scene-app.md`
   - **图文卡片/小红书图文/文章转卡片** → `references/scene-cards.md`

### Step 3: 拷模板
从 `assets/` 选择对应模板作为起点:
- 教程型 → `assets/template-tutorial.html`
- 活动页/Landing → `assets/template-landing.html`
- App型/功能型 → `assets/template-app.html`
- **图文卡片** → `assets/template-cards.html`

**从模板开始改,不从零写。**

注意:模板内的头像引用是相对路径 `avatar.jpg`(与HTML同目录)。复制模板到输出位置后,把 `assets/avatar.jpg` 一并复制到输出HTML所在目录。

### Step 4: 选布局组合
从 `references/layouts.md` 中选取 3~5 种布局模式,为每个 section 分配不同布局。

**每个 section 布局必须不同。**

(图文卡片模式:参考 `scene-cards.md` 中的推荐排版手法,为每页选择不同手法。)

### Step 5: 选组件填充
从 `references/components.md` 中选取组件填入各 section。

**硬规则:禁止使用任何HTML默认样式。** 所有引用块、列表、表格、卡片必须从 components.md 里选用对应组件的代码。不允许用默认 `<blockquote>`、默认 `border-left` 引用、无样式 `<ul>/<ol>`、默认 `<table>`。如果在 components.md 里找不到合适的,自己设计一个符合 brand-dna 规范的,但绝不能用浏览器默认样式。

### Step 6: 自检
对照 `references/checklist.md` 逐条检查:
- **P0 必须全过** - 任何一条不过就要改
- P1 应过 - 尽量满足
- P2 加分 - 锦上添花

(图文卡片模式:额外对照 `scene-cards.md` 底部的 Checklist。)

### Step 7: 交付
输出最终 HTML 文件,确保可直接在浏览器打开。

## 场景类型速查

| 类型 | 场景文件 | 模板 |
|------|----------|------|
| 教程型/介绍型/科普型 | `references/scene-tutorial.md` | `assets/template-tutorial.html` |
| 活动页/分享会/Landing | `references/scene-landing.md` | `assets/template-landing.html` |
| App型/功能型 | `references/scene-app.md` | `assets/template-app.html` |
| 图文卡片/小红书图文 | `references/scene-cards.md` | `assets/template-cards.html` |

## 关键原则
- **从模板开始改,不从零写** - 模板已内置品牌变量和基础结构
- **每个 section 布局必须不同** - 避免单调重复,从 layouts.md 选不同模式
- **做完必须跑 checklist** - P0 全过才能交付

## 禁忌
严格遵守 `brand-dna.md` 的禁忌清单,不在此重复。核心底线:截图发 Twitter 不会被说"又是AI做的"。
