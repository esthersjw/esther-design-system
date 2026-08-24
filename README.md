# Personal Design Skill

一套给 AI 看的个人品牌设计系统（KAI 设计体系）。

**Kai** · [GitHub](https://github.com/jokerwon)

> **本仓库是 [esther-design-system](https://github.com/esthersjw/esther-design-system)（作者：[ESTHER不二](https://www.xiaohongshu.com/user/profile/55c6c7695894460904f87b47?m_source=pinpai)）的 Fork，基于 CC BY-NC-SA 4.0 修改而来，已在协议允许的范围内替换为我的品牌信息（KAI 设计体系），并继续以相同协议分享。**
>
> 开源的是方法论，不是任何人的身份。使用这套系统时，请替换为你自己的姓名、头像、IP 和品牌信息。协议要求的署名仅表示内容来源，不等于身份授权。

把审美写成操作手册，AI 每次帮你做页面时必须翻这本手册，不能自由发挥。**限制 AI 的自由度 = 保证输出质量。**

> ⚠️ **使用前请先完成 `brand-dna.md` 的配置：** 默认品牌色可直接使用，如需替换成你自己的请同步修改模板变量；并放入你自己的头像。

---

## Demo

用这套系统生成的页面（基于原仓库 Demo 修改，配色已替换为 KAI 体系）：

### 📖 教程型 - Design Skill 拆解

把审美写成操作手册——从纠正AI到做出自己的Design Skill的完整过程。

🔗 [在线预览](https://jokerwon.github.io/kai-design-system/demo-readme-tutorial.html)

---

### 🎪 活动页 / Landing

视觉冲击、深浅面板交替、强节奏感的活动邀请页。

🔗 [在线预览](https://jokerwon.github.io/kai-design-system/demo-landing.html)

---

### 📱 App 型 / 功能型

功能优先、交互感、信息密度高的应用型页面。

🔗 [在线预览](https://jokerwon.github.io/kai-design-system/demo-app.html)

---

### 📕 小红书图文卡片

3:4 比例、字大、手机可读、一键导出 PNG 的图文卡片。

🔗 [在线预览](https://jokerwon.github.io/kai-design-system/demo-cards.html)

---

### 📱 公众号排版

杂志编号风：全内联样式 + section 标签，复制粘贴进微信公众号编辑器即可。

🔗 [在线预览](https://jokerwon.github.io/kai-design-system/demo-wechat.html)

---

### 📜 布局 Playground

16种经过验证的布局模式一览。

🔗 [在线预览](https://jokerwon.github.io/kai-design-system/demo-layouts.html)

---

### 🧩 组件库全览

51个经过验证的可复用组件。

🔗 [组件库预览](https://jokerwon.github.io/kai-design-system/components-preview.html)

---

## 核心逻辑

```
SKILL.md(流程 - AI 按什么步骤干活)
    ↓
brand-dna.md + references/*(规范 - 能用什么不能用什么)
    ↓
assets/template-*.html(起点 - 从模板改,不从零写)
```

- AI 不能随便发明布局 → 只能从 16 种里选
- AI 不能随便用颜色 → 只能用你定义的品牌色 + 扩展规则
- AI 不能随便写样式 → 必须从组件库里选
- AI 做完要自检 → 对照 checklist 逐条过，P0 不过就打回

---

## 文件结构

```
kai-design-system/
├── SKILL.md                    ← 7步工作流(大脑)
├── DESIGN.md                   ← KAI 设计体系设计理念
├── brand-dna.md                ← 品牌基因:颜色/字体/气质/禁忌(需配置)
├── assets/                     ← 模板骨架(起点)
│   ├── template-tutorial.html      教程页模板
│   ├── template-landing.html       活动页模板
│   ├── template-app.html           App型模板
│   ├── template-cards.html         小红书卡片模板
│   ├── template-wechat.html        公众号排版模板
│   ├── html2canvas.min.js          卡片导出依赖
│   ├── avatar-placeholder.svg      占位头像
│   ├── avatar.png                  我的头像(替换为你自己的)
│   └── character.png               IP 形象图
└── references/                 ← 规则和零件(知识库)
    ├── layouts.md                  16种布局模式(附完整代码)
    ├── components.md               组件库(51组件,完整HTML+CSS)
    ├── checklist.md                质量检查清单(P0/P1/P2)
    ├── scene-tutorial.md           教程场景规范
    ├── scene-landing.md            活动页场景规范
    ├── scene-app.md                App型场景规范
    ├── scene-cards.md              小红书卡片场景规范
    └── scene-wechat.md             公众号排版场景规范
```

---

## 7 步工作流

AI 每次做设计必须按这个顺序走：

| # | 做什么 | 为什么 |
|---|--------|--------|
| 1 | 问 5 个问题(类型/受众/几屏/素材/约束)。类型含：教程/活动页/App/卡片/**公众号** | 不自作主张 |
| 2 | 读 brand-dna + 对应场景文件 | 先学规矩再动手 |
| 3 | 从 assets/ 复制对应模板 | 从半成品开始，不从零写 |
| 4 | 从 layouts.md 选 3-5 种布局 | 每个 section 不能一样 |
| 5 | 从 components.md 选组件 | 禁止用 HTML 默认样式 |
| 6 | 对照 checklist 自检 | P0 不过就打回 |
| 7 | 交付 HTML 文件 | 浏览器打开就能看 |

---

## 品牌基因速览

### 色板（KAI 体系，主题变更只改 brand-dna.md 的 Token 层）

| 角色 | 色值 | 比例 |
|------|------|------|
| 近白（基底） | `#FCFCFC` | 65%–70% |
| 藏青（主色） | `#2F4767` | 20%–25% |
| 中性（炭黑/灰蓝） | `#2A2624` / `#303A43` | 8%–10% |
| 姜黄（唯一强调） | `#FAD470` | ≤5% |
| 暖辅 | `#F3C7A1` / `#F3BB99` | 卡片底 / 温和提示 |

### 字体

| 用途 | 字体 |
|------|------|
| 中文正文 | Noto Sans SC（思源黑体） |
| 中文标题 | Noto Serif SC（思源宋体）/ Noto Sans SC 700–900 |
| 英文装饰 | Georgia（系统衬线） |
| 代码/终端 | 系统等宽栈（SF Mono / Menlo / Consolas） |

### 气质关键词（请根据你的品牌调性修改）

空与克制 · 纸感 · 沉稳 · 单一焦点 · 一眼可辨的纯化

### 禁忌

色板外任何新颜色（最高铁律）· 姜黄大面积铺色 · 蓝紫渐变 · glassmorphism · neon · 纯黑/纯白 · 手写体/艺术字 · Inter/Roboto · 用颜色分层级 · bounce 动画 · 所有 section 居中 · HTML 默认样式 · 看起来像 AI 生成的通用模板

---

## 质量检查

**P0(必须全过)**

色板合规（无任何新增色值）· 配色比例（近白 65–70% / 藏青 20–25% / 中性 8–10% / 姜黄 ≤5%）· 灰阶成立（黑白先行）· 一屏单一焦点 · 层级只用字号字重留白 · 留白达标 · 无禁忌元素 · 无 HTML 默认样式 · 响应式且移动端留白不消失 · 每 section 布局不同 · clamp() fluid sizing

**P1(应过)**

地平线式构图 · 字号/字重对比极端 · 纸感材质 · 炭黑手绘线 · Scroll Reveal 动效

**P2(加分)**

深色面板（藏青 `#243C6C` / 炭黑 `#2A2624`）打破节奏 · 减法原则（删掉它意思还在，就删）· prefers-reduced-motion

---

## 怎么用

1. Fork 或克隆本仓库
2. 放入你的头像 `assets/avatar.png`
3. （可选）打开 `brand-dna.md`，修改「基础 Token 层」（`--c-*` 变量）的色值即可全局换主题——所有模板的 `:root` 已 Token 化，语义变量自动生效，无需逐处替换。注意：公众号模板（`template-wechat.html`）全部是内联样式，没有 CSS 变量，需手动搜索替换色值（藏青 `#2F4767` / 姜黄 `#FAD470` / 暖辅 `#F3C7A1` / 炭黑 `#2A2624` / 近白 `#FCFCFC`）
4. 把 `assets/template-cards.html` 中的作者名替换成你自己的
5. 把仓库链接发给你的 AI Agent，跟它说：

> 帮我读这个设计系统，以后做页面按这个规范来。

核心不是这些文件本身，是**你的审美判断力**。文件只是把你的判断写成了 AI 能执行的规则。

---

## Credits

- 本仓库基于 [ESTHER不二](https://github.com/esthersjw) 的 [esther-design-system](https://github.com/esthersjw/esther-design-system) 修改，遵守 CC BY-NC-SA 4.0
- 原作者的方法论灵感来源于 [归藏](https://github.com/guizang) 的 PPT Skill——“限制AI的自由度 = 保证输出质量”这个核心思路参考了他的设计

---

## License

[![CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

本仓库中的方法论、设计规范、工作流程、布局模式、组件模式、模板和文档，采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 协议。

- ✅ 可以学习、使用、修改和分享本仓库中的方法论与设计内容
- ✅ 必须注明来源：ESTHER不二 / [esther-design-system](https://github.com/esthersjw/esther-design-system)（原作），及本仓库的修改
- ❌ 禁止将本仓库内容用于商业用途
- 🔄 修改后必须以相同协议分享
- ❌ 署名不等于姓名、头像、IP、Logo、品牌标识或本人形象的使用授权

### Name, Image and IP Notice

**ESTHER不二、Esther、不二、esthersjw** 及与原作者相关的姓名、头像、IP形象、Logo、品牌标识、个人账号标识和本人形象，不属于本仓库 CC BY-NC-SA 4.0 的授权范围，本仓库的修改也未获得任何此类授权。

你可以在协议要求的范围内进行事实性来源署名，但不得把这些名称或视觉资产用作自己的账号名、用户名、头像、品牌名、角色名、产品名或对外宣传素材，也不得暗示与原作者存在官方关系。
