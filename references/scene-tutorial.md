# Scene: 介绍型 / 教程型 / 科普型页面

> 适用于所有单页HTML科普、教程、功能介绍、概念解释类页面。基于 `brand-dna.md`（KAI 设计体系：原研哉理念 × 色板）落地。

---

## 🎨 色板

（继承 brand-dna.md 的 **Token 体系**——基础 Token 层 + 语义别名层。换主题只改 brand-dna.md 的 token 定义，本表与所有下游引用零改动）

| 用途 | 变量名 | 色值 | 说明 |
|------|--------|------|------|
| 姜黄（唯一强调） | `--yellow` | `#FAD470` | 下划线、徽章、高亮、连接线、数据点。**≤5%** |
| 姜黄浅底 | `--yellow-soft` | `rgba(250,212,112,0.18)` | 高亮底色块、气泡底色 |
| 藏青（主色） | `--blue` | `#2F4767` | 标题、主色块、超链接、重点标记 |
| 藏青暗变体 | `--blue-deep` | `#243C6C` | 深色面板底、hover 分层 |
| 暖辅（点缀承接） | `--red` | `#F3BB99` | 提示框底、问题侧标记（变量名沿用，值已换） |
| 近白底 | `--cream` | `#FCFCFC` | 页面主背景 |
| 暖辅浅底 | `--cream-dark` | `rgba(243,199,161,0.12)` | section 间交替背景 |
| 炭黑 | `--ink` | `#2A2624` | 正文主色（非纯黑） |
| 灰蓝 | `--ink-light` | `#303A43` | 次要正文 |
| 辅助灰 | `--ink-faint` | `rgba(48,58,67,0.55)` | 辅助文字、标签 |

### 色彩原则
- 绝不用纯黑 `#000` 或纯白 `#fff`——近白 `#FCFCFC` 是唯一的底色
- 姜黄像盐一样吝啬——只出现在需要人注意的那一处，占比 ≤5%
- 正文一律中性色（炭黑/灰蓝），**不用颜色分层级**
- 背景层次用暖辅极浅透明变体或纸感噪点，不用渐变背景

---

## 🔤 字体

| 用途 | 字体 | 备注 |
|------|------|------|
| 中文标题 | `Noto Serif SC`（思源宋体） | 编辑排版风的标题选项；更克制时直接思源黑体 900 |
| 正文/UI | `Noto Sans SC` + 系统栈 `-apple-system, 'PingFang SC', 'Helvetica Neue', sans-serif` | 全站默认，无衬线保证可读性 |
| 代码/等宽 | `'SF Mono', Menlo, Consolas, monospace` | 仅用于真实代码文本，不充当装饰 |

### 字号层次（全部用 `clamp()` 做fluid sizing）
- **Hero大标题**: `clamp(2.4rem, 6vw, 4.5rem)` — 沉稳有力
- **Section标题**: `clamp(1.5rem, 3.5vw, 2.25rem)` — 大但不压人
- **卡片标题**: `1.1rem ~ 1.3rem` — 清晰可辨
- **正文**: `16px` (body base)
- **辅助文字**: `0.8rem ~ 0.875rem` — 小但可读

### 字体原则
- 文字不做个性化处理——不用花哨标题字、手写体、艺术字、大号水印装饰字
- 层级只用三样：字号、字重、留白
- 用字重对比替代字体对比：标题 700–900，正文 400
- `letter-spacing`: 英文大写标签加 `0.1em~0.2em` 间距

---

## 📐 布局

### 核心原则
- **左对齐为主**，居中仅用于短标题
- **不对称**——grid用 `1fr 1.1fr` 或 `0.45fr 1fr` 这种不等分
- **每个section布局形式不同**——避免单调重复
- **留白是元素不是剩余**——排版先问「白该放在哪」
- **max-width: 1300px** + `margin: 0 auto` 约束内容宽度

### 可选的布局模式（按需组合，每页至少3种）
1. **Hero分栏**: 左文字 + 右大图，grid两栏
2. **Sticky侧栏**: 左边编号sticky，右边内容滚动
3. **时间线交错**: 中轴线+左右交替内容块（适合并列要点）
4. **全宽藏青面板**: 突出某个重要内容，打破节奏
5. **Step引导**: 编号+连接线+每步说明
6. **卡片网格**: 2~3列等宽卡片（注意：不要出现落单的孤儿卡片）
7. **产品出血型Hero**: 左侧40%紧凑文字（大标题+描述+缩略图），右侧60%大图溢出右边界。图片用 `margin-right: -5vw; border-radius: 24px 0 0 24px`，grid: `grid-template-columns: 0.4fr 0.6fr`
8. **条纹Editorial**: 条纹分割带（repeating-linear-gradient）做section分隔。内部左图右文，图片可加低饱和度滤镜。标题用思源宋体大字重，正文小号无衬线
9. **横向滚动时间线**: flex横排 + scroll-snap + 固定宽度卡片，适合经历展示、项目历程
10. **全宽藏青色面板**: 背景使用藏青 `#2F4767` 或暗变体 `#243C6C`，文字近白。一页最多1~2个，用于打破近白底的节奏。姜黄在面板内只做一处小面积焦点（下划线/徽章），禁止大段姜黄文字
11. **对称双栏（Pain展示）**: `grid-template-columns: 1fr 1fr`，min-height: 100vh。左侧大字标题，右侧列表/解释。适合问题/痛点、before/after对比

### 间距系统
- Section之间: `clamp(80px, 12vh, 160px)`
- 内容块之间: `clamp(40px, 6vw, 100px)`
- 卡片内padding: `clamp(28px, 3vw, 44px)`，且 ≥ 内容最小字号的 2 倍
- 元素间gap: `clamp(24px, 3vw, 48px)`

---

## 🎭 装饰元素

### 可用的装饰手法
- **炭黑手绘轮廓线**: `border: 2px solid #0C0C0C`（或 dashed）压住主体/卡片轮廓，圆角收敛（≤12px）
- **姜黄分割线**: 实色短条（36–56px × 4–6px）做章节锚点，或 1px 渐隐线 `linear-gradient(90deg, transparent, var(--yellow), transparent)`
- **荧光笔高亮**: `linear-gradient(180deg, transparent 60%, rgba(250,212,112,0.5) 60%)` 文字底部高亮，一句话最多一处
- **暖辅提示底**: `rgba(243,199,161,0.2)` 做提示框/引言区底色
- **SVG简笔画**: 用炭黑描边风格的简化示意图，不要写实截图
- **底部色条**: `border-bottom: 3px solid var(--blue)` 给卡片加标识（禁止使用 border-left 竖线引用块）

### 条纹肌理分割（替代渐隐线做section divider）
```css
.stripe-divider {
  height: 24px;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 3px,
    rgba(42, 38, 36, 0.05) 3px,
    rgba(42, 38, 36, 0.05) 4px
  );
}
```

### 关键词高亮底色块
```css
.keyword-highlight {
  background: rgba(250, 212, 112, 0.3);
  padding: 0.1em 0.4em;
  border-radius: 4px;
  display: inline;
  box-decoration-break: clone;
}
```

### 浮动信息pill（在图片/hero区上浮动小标签）
```css
.float-pill {
  position: absolute;
  background: var(--cream);
  border: 1px solid rgba(12, 12, 12, 0.12);
  padding: 0.5em 1em;
  border-radius: 100px;
  font-size: 0.8rem;
  box-shadow: 0 4px 20px rgba(0,0,0,0.06);
  display: flex;
  align-items: center;
  gap: 0.5em;
}
```

### 全大写字间距标签
```css
.label-caps {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  font-weight: 500;
  color: var(--ink-light);
}
```

### 装饰原则
- 每加一个装饰先问「删掉它，意思还在吗？」——在，就删
- 同时存在的装饰手法 ≤2 种，宁少勿多
- ✅ 用炭黑轮廓线制造纸感（手绘线、细描边）
- ✅ 用出血/溢出制造惊喜（图片超出容器边界，一处足够）
- ✅ 用字重与留白制造节奏（900 vs 400，大 vs 小）
- ✅ 姜黄只点在 1-2 个关键词上

---

## ✨ 动效

### Scroll Reveal
```css
.reveal {
  opacity: 0;
  transform: translateY(32px);
  transition: opacity 0.7s cubic-bezier(0.16, 1, 0.3, 1),
              transform 0.7s cubic-bezier(0.16, 1, 0.3, 1);
}
.reveal.visible { opacity: 1; transform: none; }
```
- 用 `IntersectionObserver`，threshold 0.12
- `unobserve` after triggering（只触发一次）
- 用 `.reveal-d1` ~ `.reveal-d5` 做 stagger（0.1s递增）
- 尊重 `prefers-reduced-motion`
- 选中文本高亮：`::selection { background: #FAD470; color: #2A2624; }`

### 动效原则
- **只用 opacity + transform**，不要animate layout属性
- **只用 expo ease-out** `cubic-bezier(0.16, 1, 0.3, 1)`——自然减速
- **不要 bounce/elastic/弹跳**——过时
- **不要无限循环动画**——克制是辨识度
- **入场一次就好**——不要滚回去再重新播放

### 明确禁止
- ❌ 不要用 `transform: rotate()` 让元素歪着放——这是廉价的假活泼
- ❌ 不要故意错位/偏移来制造"手工感"
- ❌ 不要藏青面板上放大段姜黄正文（姜黄只做一处小面积焦点）

---

## 📱 响应式

### 断点
- **900px**: 两栏→单栏，图片缩小，sticky变static
- **600px**: 字号微缩(15px)，图片进一步缩小

### 原则
- 移动端不是"缩小版桌面"——重新排列而不是挤压
- 时间线/交错布局在移动端自动变成单列堆叠
- 不要在移动端隐藏内容
- 小屏同样要呼吸感——留白比例不随屏幕缩小而牺牲

---

## 📝 内容语气

- 中文为主，英文点缀做标签（全大写字间距），不做大号英文装饰字
- 口语化、轻松、像跟朋友解释
- emoji 极克制：整页 ≤3 个或不用
- 类比优先（"就像百度网盘""相当于时光机"）
- 不堆术语，说人话

---

## 🧩 可发散方向

- **配色微调**: 内容跟某品牌相关时，合作色只替换暖辅（--red）的点缀位，藏青主色与姜黄强调不变
- **布局组合**: 十一种布局模式自由组合
- **装饰密度**: 轻松内容可稍多装饰，严肃内容减到只剩字体层次与留白
- **IP出现方式**: 不同姿势（叉腰、放大镜、坐椅子等）
- **深色section**: 可用一个section用藏青暗变体 `#243C6C` 底 + 近白字，制造节奏对比
- **交互**: 如果内容适合，可加hover状态、tab切换、accordion——但不要为交互而交互

---

## 🎯 设计哲学："为什么好看"的底层逻辑

- **空与克制** — 留白是最高优先级元素，一屏只讲一件事
- **黑白先行** — 灰阶成立才上色；姜黄像盐，一处足够
- **单一焦点** — 主体在白中独立呈现，图片应该"活在空间里"而不是"被框住"
- **层级靠字号、字重、留白** — 不是靠颜色和字体花样
