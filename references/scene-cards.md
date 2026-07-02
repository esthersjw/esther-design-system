# Scene: 小红书图文卡片（3:4）

> 适用于将文章、教程、观点拆解为小红书图文卡片。单个HTML文件包含所有卡片，支持一键导出PNG。

---

## 触发场景

用户说"做图文卡片"、"小红书图文"、"文章转卡片"、"帮我转成图文"、"做卡片"、"转成图文"等。

---

## 📐 卡片规格

| 属性 | 值 |
|------|-----|
| 尺寸 | 1080×1440px（3:4） |
| 最多张数 | 18张（小红书上限） |
| 文件形式 | 所有卡片放一个HTML文件，每张一个 `div.card` |
| 导出方式 | 顶部固定"一键导出PNG"按钮（html2canvas本地文件 + JSZip打包为zip一次性下载） |
| 浏览器预览 | `transform: scale(0.45); transform-origin: top center; margin-bottom: -792px` |
| 本地服务器 | 用 `python3 -m http.server 8765` 打开，确保html2canvas加载正常 |

---

## 🔤 字号规范（1080×1440画面）

| 用途 | 字号 | 说明 |
|------|------|------|
| 封面/金句大标题 | 72-96px | Noto Serif SC，冲击力 |
| 页面标题 | 48-60px | Noto Serif SC |
| 正文/列表项 | 36-42px | Noto Sans SC |
| 辅助说明 | 28-32px | 浅色、次要信息 |
| 小标签/badge | 24-28px | 大写字间距标签或小pill |
| 代码块内文字 | 28-32px | Fira Code |

---

## 📝 排版原则

### 密度控制
- **内容少的页**（封面、金句、小结）→ 字巨大、大量留白、视觉冲击
- **内容多的页**（对比、列表、代码结构）→ 杂志排版，信息密度合理但不拥挤
- 每页都要适配画面，内容撑满但有呼吸感

### 变化感
- 每页排版要有变化——不能所有页都一样的layout
- 深色面板页 / 浅色页 / 强调色面板穿插使用
- 大留白页和信息密度页交替

### 绝对禁忌
- ❌ 不要用左侧彩色竖线的卡片
- ❌ 不要用红色圆点前缀
- ❌ 不要千篇一律列表（每项前面一个圆点/数字的平铺排列）
- ❌ 不要HTML默认blockquote样式
- ❌ 不要所有页都用同一种layout

---

## 🧩 卡片结构模板

### P1 封面
- 大标题（84px）用汇文明朝体（Huiwen Mincho），关键词用蓝色高亮块（`background: #2B7FD8; color: #fff; padding: 4px 16px; border-radius: 6px`）
- 副标题（44px）一行显示，紧跟标题下方，`white-space: nowrap`
- 圆形头像（`avatar.jpg`，120px，`border: 4px solid #F4D758`）
- 署名「Esther不二」44px + 介绍34px
- 整体边框：`border: 28px solid #F4D758`
- 背景加浅色网格质感（`background-image: linear-gradient(rgba(0,0,0,0.03) 1px, transparent 1px), linear-gradient(90deg, rgba(0,0,0,0.03) 1px, transparent 1px); background-size: 40px 40px`）
- 中间留白区域给用户放效果图/截图

### P2-Pn 内容页
- 根据内容量决定排版密度
- 每页选择不同的排版手法（见下方推荐列表）
- 页码编号用 oversized 淡色装饰数字

### 最后一页 尾页
- 金句（oversized引号装饰 `"` ，Fraunces 200px，opacity 0.15）
- 圆形头像 + 署名「Esther不二」
- CTA：「关注 Esther不二」
- 一行小字：`在AI时代认真生活的女生｜INTJ / 跟Agent搭档的第1年`
- 底部品牌三色装饰条

---

## 🎨 推荐排版手法

从V3验证通过的案例总结，按需组合：

| 手法 | 适用场景 | 要点 |
|------|----------|------|
| 深色面板 | 代码、文件树、重点强调 | 暗色背景(#1A1A2E)+亮色文字，圆角16px |
| oversized编号 | 步骤/流程展示 | 极大(64-120px)极淡色(opacity 0.12)做背景装饰 |
| 色块交替行 | 对比/表格 | 暖底行(#faf6eb) vs 白底行(#fff) 交替 |
| 大箭头流程 | 步骤连接 | 蓝色箭头(48px)连接流程块 |
| 代码面板 | 代码/文件树/命令 | 深色底+Fira Code+三色圆点title bar |
| 金句装饰 | 核心观点/结尾 | oversized引号+白底圆角卡片 |
| 问题→解法对比行 | before/after | 左红底右蓝底，✗ vs ✓ 前缀 |
| 图标+文字横排 | 要点/优势列表 | emoji/icon左对齐+文字说明 |

---

## 🏷️ 品牌规范引用

- 所有颜色、字体、禁忌遵守 `brand-dna.md`
- 头像源文件：`assets/avatar.jpg`（HTML内用相对路径 `avatar.jpg` 引用，交付时复制到输出HTML同目录）
- 署名固定为你在 `template-cards.html` 中配置的作者名（默认「Esther不二」）
- 品牌三色比例：主色6 : 强调3 : 点缀1
- 背景主色：奶白 `#fefcf6` / 深奶 `#faf6eb`，深色面板用 `#1A1A2E`

---

## ✅ Checklist（做完自查）

- [ ] 每页字号是否适配手机阅读（标题≥48px，正文≥36px）
- [ ] 是否有丑的默认组件（竖线列表、红圆点、默认blockquote）
- [ ] 每页是否撑满画面（内容占满1080×1440，有呼吸感但不留大片空白）
- [ ] 页面之间排版是否有变化（不能连续3页同一layout）
- [ ] 品牌三色比例 6:3:1
- [ ] 头像和署名是否正确（圆形头像+「Esther不二」）
- [ ] 导出按钮是否工作（html2canvas本地文件 + JSZip CDN、exportAll打包zip一次性下载）
- [ ] 卡片是否居中显示（transform-origin: top center）
- [ ] 用localhost打开测试导出（file://协议下js加载受限）
- [ ] 总张数≤18
