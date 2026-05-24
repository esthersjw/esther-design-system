# Esther's Design Skill

一套给 AI 看的个人品牌设计系统。告诉 AI 用什么颜色、字体、布局、组件，以及什么绝对不能用。

等于把审美写成了操作手册，AI 每次帮我做页面时必须翻这本手册，不能自由发挥。

---

## 它能做什么

把一段文字/一篇文章/一个需求，变成风格统一、有品牌感的 HTML 页面。

支持 4 种场景：
- **教程/介绍页** — 信息清晰、步骤明确
- **活动页/Landing** — 视觉冲击、有节奏感
- **App型/功能型** — 功能优先、交互感
- **小红书图文卡片** — 3:4比例、字大、手机可读、一键导出PNG

---

## 核心逻辑

```
SKILL.md（流程 — AI按什么步骤干活）
    ↓
brand-dna.md + references/*（规范 — 能用什么不能用什么）
    ↓
assets/template-*.html（起点 — 从模板改，不从零写）
```

**限制AI的自由度 = 保证输出质量。**

- AI 不能随便发明布局 → 只能从 15 种里选
- AI 不能随便用颜色 → 只能用三色 + 扩展规则
- AI 不能随便写样式 → 必须从组件库里选
- AI 做完要自检 → 对照 checklist 逐条过，P0 不过就打回

---

## 文件结构

```
esther-design-system/
├── SKILL.md                    ← 7步工作流（大脑）
├── brand-dna.md                ← 品牌基因：颜色/字体/气质/禁忌
├── README.md                   ← 你在看的这个
├── assets/                     ← 模板骨架（起点）
│   ├── template-tutorial.html      教程页
│   ├── template-landing.html       活动页/Landing
│   ├── template-app.html           App型/功能型
│   ├── template-cards.html         小红书图文卡片
│   └── avatar.jpg                  IP头像
└── references/                 ← 规则和零件（知识库）
    ├── layouts.md                  15种布局模式（附完整代码）
    ├── components.md               组件库（2988行）
    ├── checklist.md                质量检查清单（P0/P1/P2）
    ├── scene-tutorial.md           教程场景规范
    ├── scene-landing.md            活动页场景规范
    ├── scene-app.md                App型场景规范
    └── scene-cards.md              小红书卡片场景规范
```

---

## 7步工作流

AI 每次做设计必须按这个顺序走：

| 步骤 | 做什么 | 为什么 |
|------|--------|--------|
| 1 | 问 5 个问题（类型/受众/几屏/素材/约束） | 不自作主张 |
| 2 | 读 brand-dna + 对应场景文件 | 先学规矩再动手 |
| 3 | 从 assets/ 复制对应模板 | 从半成品开始，不从零写 |
| 4 | 从 layouts.md 选 3-5 种布局 | 每个 section 不能一样 |
| 5 | 从 components.md 选组件 | **禁止用 HTML 默认样式** |
| 6 | 对照 checklist 自检 | P0 不过就打回 |
| 7 | 交付 HTML 文件 | 浏览器打开就能看 |

---

## 品牌基因

### 三色

| 颜色 | 色值 | 比例 |
|------|------|------|
| 蓝 | `#2B7FD8` | 60% |
| 黄 | `#F4D758` | 30% |
| 红 | `#E84A5F` | 10% |

### 字体

| 用途 | 字体 |
|------|------|
| 中文标题 | 汇文明朝体（衬线，印刷感） |
| 中文正文 | Noto Sans SC |
| 英文装饰 | Fraunces italic |
| 手写/注释 | Caveat |
| 代码/终端 | Fira Code |

### 气质

可爱但有品质 · 手绘蜡笔感 · 有温度 · **不像AI** · 一看就是"不二的"

### 禁忌

蓝紫渐变 · glassmorphism · neon · bounce动画 · Inter/Roboto · 所有section居中 · HTML默认blockquote/列表/表格 · 看起来像AI生成的通用模板

---

## 组件库（2988行）

所有可用的"零件"，每个都是写好的 HTML+CSS 代码，AI 直接复制进去用：

- 卡片 × 5种（杂志裁切 / 编号主导 / 标签主导 / 暗色 / 引用块风格）
- 引用块 × 5种（极简竖线 / 大引号白底 / 手写badge / 黄色高亮 / 终端风格）
- 代码面板 × 4种（暗色终端 / 亮色snippet / diff对比 / 多Tab）
- 流程步骤条 · Do/Don't对比 · Pull Quote · 聊天气泡 · 导航栏 · 日历 · 书卡 · 机票/住宿卡 ……

---

## 质量检查

做完逐条对照：

**P0（必须全过）：** 品牌三色比例 · 无禁忌元素 · 无HTML默认样式 · 暖底背景 · 衬线+无衬线混搭 · 响应式 · 每section布局不同 · clamp() fluid sizing · 截图发Twitter不会被说"又是AI做的"

**P1（应过）：** 至少一个视觉惊喜section · 字号对比极端 · Scroll Reveal动效 · 大装饰数字/英文

**P2（加分）：** 图片溢出容器 · 深色面板打破节奏 · 装饰元素克制 · prefers-reduced-motion

---

## 怎么用（Fork指南）

1. Fork 这个仓库
2. 改 `brand-dna.md` — 换成你的颜色、字体、气质关键词
3. 改 `assets/avatar.jpg` — 换成你的头像
4. 组件库可以先不动，等你积累了自己的偏好再替换
5. 把整个文件夹放到你的 AI 能读到的地方（Cola Skill目录 / Claude Project / 任何支持上下文的工具）
6. 告诉 AI："做页面之前先读 SKILL.md"

核心不是这些文件本身，是**你的审美判断力**。文件只是把你的判断写成了 AI 能执行的规则。

---

## 关于

Made by [Esther不二](https://github.com/esthersjw) — 在AI时代认真生活的女生

灵感来源：[归藏 op7418](https://github.com/op7418) 的 PPT Design Skill
