# 布局模式库

> 16种经过验证的布局模式，按使用频率排序。每个section选不同的布局，组合使用。

---

## 1. Hero双栏不对称（文字+视觉）

**适用**: 分享会Landing、教程首屏、产品介绍首屏

```html
<section class="hero">
  <div class="hero-text">
    <span class="label-caps">CATEGORY</span>
    <h1>主标题</h1>
    <p>描述文字</p>
  </div>
  <div class="hero-visual">
    <!-- 图片或装饰 -->
  </div>
</section>
```

```css
.hero {
  min-height: 100vh;
  display: grid;
  grid-template-columns: 1fr 0.6fr;
  align-items: center;
  gap: 48px;
  padding: 6rem 2rem 4rem;
}
```

⚠️ 注意：不要做成对称50/50，不对称比例才有张力。

---

## 2. Sticky侧栏 + 内容滚动

**适用**: 长内容分段展示、知识点讲解、深度内容

```html
<section class="layout-sticky">
  <div class="sticky-side">
    <span class="section-number">01</span>
    <h2>Section标题</h2>
  </div>
  <div class="content-scroll">
    <!-- 滚动内容 -->
  </div>
</section>
```

```css
.layout-sticky {
  display: grid;
  grid-template-columns: 0.35fr 1fr;
  gap: clamp(40px, 6vw, 100px);
  align-items: start;
}
.sticky-side {
  position: sticky;
  top: 80px;
}
```

⚠️ 注意：移动端（<900px）sticky变static，变为正常纵向堆叠。

---

## 3. 三等分卡片网格

**适用**: 功能展示、能力矩阵、并列要点

```html
<div class="features-grid">
  <div class="feature-card">...</div>
  <div class="feature-card">...</div>
  <div class="feature-card">...</div>
</div>
```

```css
.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: clamp(20px, 2.5vw, 32px);
}
@media (max-width: 900px) {
  .features-grid { grid-template-columns: 1fr; }
}
```

⚠️ 注意：不要出现落单的孤儿卡片，保持3/6/9的数量。

---

## 4. 纵向Step流程线

**适用**: 安装步骤、流程教程、教学引导

```html
<div class="steps-container">
  <div class="step-item">
    <span class="step-num">1</span>
    <div class="step-content">
      <h3>步骤标题</h3>
      <p>步骤描述</p>
    </div>
  </div>
  <!-- 更多步骤 -->
</div>
```

```css
.steps-container {
  display: flex;
  flex-direction: column;
  gap: clamp(32px, 4vw, 56px);
  padding-left: 60px;
  position: relative;
}
.steps-container::before {
  content: '';
  position: absolute;
  left: 22px;
  top: 40px; bottom: 40px;
  width: 2px;
  border-left: 2px dashed rgba(12, 12, 12, 0.25);
}
.step-item {
  position: relative;
}
.step-num {
  position: absolute;
  left: -60px;
  width: 44px; height: 44px;
  border-radius: 50%;
  background: var(--blue);
  color: #FCFCFC;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: Georgia, 'Songti SC', serif;
  font-weight: 700;
}
```

⚠️ 注意：步骤不超过5个，超过则拆分成多组。

---

## 5. 中轴时间线交错

**适用**: 内容对比、时间线、并列要点展示

```html
<div class="timeline">
  <div class="timeline-axis"></div>
  <div class="timeline-item">
    <div class="timeline-content">...</div>
    <div class="timeline-visual">...</div>
  </div>
  <div class="timeline-item reverse">
    <div class="timeline-visual">...</div>
    <div class="timeline-content">...</div>
  </div>
</div>
```

```css
.timeline {
  position: relative;
}
.timeline-axis {
  position: absolute;
  left: 50%;
  top: 0; bottom: 0;
  width: 2px;
  background: rgba(47, 71, 103, 0.15);
}
.timeline-item {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  margin-bottom: clamp(40px, 6vw, 80px);
}
@media (max-width: 900px) {
  .timeline-axis { display: none; }
  .timeline-item { grid-template-columns: 1fr; }
}
```

⚠️ 注意：移动端自动变为单列堆叠。

---

## 6. 全宽深色面板

**适用**: 重要引用、核心观点、代码展示（打破近白底节奏）

```html
<section class="dark-section">
  <div class="container">
    <blockquote class="dark-quote">重要观点</blockquote>
  </div>
</section>
```

```css
.dark-section {
  background: #243C6C;
  color: #FCFCFC;
  padding: clamp(60px, 8vh, 120px) 0;
}
.dark-section .container {
  max-width: 1300px;
  margin: 0 auto;
  padding: 0 2rem;
}
```

⚠️ 注意：一页最多用1~2个深色面板，用于制造节奏对比。

---

## 7. 横向Step连接线

**适用**: 简短的3~4步骤概览

```html
<div class="steps-layout">
  <div class="step-card">
    <span class="step-dot">1</span>
    <h4>步骤名</h4>
    <p>简述</p>
  </div>
  <div class="step-card">
    <span class="step-dot">2</span>
    <h4>步骤名</h4>
    <p>简述</p>
  </div>
  <div class="step-card">
    <span class="step-dot">3</span>
    <h4>步骤名</h4>
    <p>简述</p>
  </div>
</div>
```

```css
.steps-layout {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0;
  position: relative;
}
.steps-layout::before {
  content: '';
  position: absolute;
  top: 28px;
  left: 28px; right: 28px;
  height: 3px;
  background: var(--yellow);
}
.step-card {
  text-align: center;
  padding: 0 1rem;
}
.step-dot {
  width: 56px; height: 56px;
  border-radius: 50%;
  background: var(--blue);
  color: #FCFCFC;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: Georgia, 'Songti SC', serif;
  font-size: 1.2rem;
  font-weight: 700;
  position: relative;
  z-index: 1;
}
```

⚠️ 注意：仅适合3~4步，超过则用纵向Step。

---

## 8. Hero全屏居中型

**适用**: 个人品牌首页、产品发布页（强视觉冲击力首屏）

```html
<section class="hero-centered">
  <div class="hero-card">
    <!-- 核心内容 -->
  </div>
</section>
```

```css
.hero-centered {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 6rem 2rem 4rem;
}
.hero-card {
  background: #FCFCFC;
  border-radius: 12px;
  padding: clamp(2.5rem, 5vw, 4.5rem);
  box-shadow: 0 4px 32px rgba(42,38,36,.08);
  max-width: 720px;
  width: 100%;
}
```

⚠️ 注意：居中型仅限Hero首屏使用一次，后续section必须左对齐为主。

---

## 9. Hero单栏纵向（中心辐射型）

**适用**: 活动分享页、情感叙事页（以头像/Logo为中心展开）

```html
<section class="hero-vertical">
  <div class="hero-avatar"><!-- 头像 --></div>
  <h1>标题</h1>
  <p class="hero-subtitle">副标题描述</p>
  <div class="hero-tags">
    <span class="tag">标签1</span>
    <span class="tag">标签2</span>
  </div>
</section>
```

```css
.hero-vertical {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 40px 24px;
  text-align: center;
}
.hero-avatar {
  width: clamp(120px, 18vw, 180px);
  height: clamp(120px, 18vw, 180px);
  border-radius: 50%;
  margin-bottom: 2rem;
}
```

⚠️ 注意：仅限Hero区域，后续section不要继续居中。

---

## 10. 自适应卡片网格（auto-fill）

**适用**: 技能卡片、书籍卡片、不确定数量的内容集合

```html
<div class="auto-grid">
  <div class="card">...</div>
  <div class="card">...</div>
  <!-- 任意数量 -->
</div>
```

```css
.auto-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 1rem;
}
```

⚠️ 注意：适合内容数量不固定的场景，会自动换行。

---

## 11. 全宽品牌色面板

**适用**: 情绪高潮、CTA邀请、核心观点（打破近白底节奏）

```html
<section class="section-accent">
  <div class="container">
    <h2>核心观点</h2>
    <p>描述文字</p>
  </div>
</section>
```

```css
.section-accent {
  background: var(--blue);
  color: #FCFCFC;
  padding: clamp(80px, 12vh, 160px) 0;
  position: relative;
  overflow: hidden;
}
.section-accent .container {
  max-width: 1300px;
  margin: 0 auto;
  padding: 0 2rem;
}
```

⚠️ 注意：一页最多1~2个。姜黄不做大面积面板底色（≤5% 铁律），在面板内只做一处焦点。不要在藏青面板上放大段姜黄文字。

---

## 12. 横向滚动时间线

**适用**: 经历时间线、横向浏览内容

```html
<div class="timeline-scroll">
  <div class="timeline-card">
    <span class="year">2022</span>
    <h4>事件标题</h4>
    <p>描述</p>
  </div>
  <div class="timeline-card">
    <span class="year">2023</span>
    <h4>事件标题</h4>
    <p>描述</p>
  </div>
  <!-- 更多卡片 -->
</div>
```

```css
.timeline-scroll {
  display: flex;
  gap: 1.5rem;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
  padding-bottom: 2rem;
}
.timeline-card {
  flex: 0 0 300px;
  scroll-snap-align: start;
  background: #FCFCFC;
  border-radius: 16px;
  padding: clamp(24px, 3vw, 36px);
  box-shadow: 0 4px 20px rgba(0,0,0,.06);
}
.timeline-card .year {
  font-family: Georgia, 'Songti SC', serif;
  font-size: 1.8rem;
  color: var(--blue);
  font-weight: 700;
}
```

⚠️ 注意：需要自定义scrollbar样式保持品牌一致性。

---

## 13. 分栏对称（Pain Point展示）

**适用**: 问题vs方案对比、冲突展示、before/after

```html
<section class="split-section">
  <div class="split-left">
    <h2>问题/痛点</h2>
  </div>
  <div class="split-right">
    <ul>
      <li>具体问题1</li>
      <li>具体问题2</li>
    </ul>
  </div>
</section>
```

```css
.split-section {
  min-height: 100vh;
  display: grid;
  grid-template-columns: 1fr 1fr;
  overflow: hidden;
}
.split-left {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: clamp(40px, 6vw, 80px);
}
.split-right {
  display: flex;
  align-items: center;
  padding: clamp(40px, 6vw, 80px);
  background: var(--cream-dark);
}
@media (max-width: 900px) {
  .split-section { grid-template-columns: 1fr; min-height: auto; }
}
```

⚠️ 注意：左侧放大字标题，右侧放具体内容/列表。

---

## 14. Tab切换单栏（Dashboard型）

**适用**: 个人看板、功能切换、数据面板

```html
<div class="dashboard">
  <div class="tab-bar">
    <button class="tab active" data-tab="tab1">标签1</button>
    <button class="tab" data-tab="tab2">标签2</button>
  </div>
  <div class="tab-content active" id="tab1">内容1</div>
  <div class="tab-content" id="tab2">内容2</div>
</div>
```

```css
.dashboard {
  max-width: 820px;
  margin: 0 auto;
}
.tab-bar {
  display: flex;
  gap: 4px;
  overflow-x: auto;
  border-bottom: 2px solid #eee;
  margin-bottom: 2rem;
}
.tab {
  padding: 10px 20px;
  border: none;
  background: transparent;
  cursor: pointer;
  font-size: 0.9rem;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
}
.tab.active {
  border-bottom-color: var(--blue);
  color: var(--blue);
  font-weight: 600;
}
.tab-content { display: none; }
.tab-content.active { display: block; }
```

⚠️ 注意：仅用于App型/功能型页面，教程页不需要Tab。

---

## 15. 无限画布（Canvas型）

**适用**: 白板应用、信息可视化、自由布局

```html
<div class="canvas-area">
  <div class="canvas-grid">
    <div class="canvas-transform" id="canvasTransform">
      <!-- 自由放置的卡片 -->
    </div>
  </div>
</div>
```

```css
.canvas-area {
  position: fixed;
  top: 48px; left: 220px; right: 0; bottom: 0;
  overflow: hidden;
  cursor: grab;
}
.canvas-area:active { cursor: grabbing; }
.canvas-grid {
  width: 100%; height: 100%;
  background-image: radial-gradient(circle, rgba(47,71,103,0.13) 1.2px, transparent 1.2px);
  background-size: 28px 28px;
}
.canvas-transform {
  position: absolute;
  transform-origin: 0 0;
  will-change: transform;
}
```

⚠️ 注意：需要配合JS实现拖拽/缩放。仅用于App型页面。

---

## 16. Sticky编号侧栏 + 大图杂志卡片

**适用**: 步骤教程、流程拆解、图文并茂的长教程（步骤5~10个）

```html
<div class="layout-sticky-mag">
  <div class="sidebar">
    <ul class="nav">
      <li>步骤名1</li>
      <li>步骤名2</li>
      <li>步骤名3</li>
    </ul>
  </div>
  <div class="steps-content">
    <div class="step-item step-observe" data-index="0">
      <img src="step-image.png" alt="">
      <div class="step-text">
        <span class="step-num">01</span>
        <div class="step-info">
          <h4>步骤标题</h4>
          <p>步骤描述</p>
        </div>
      </div>
    </div>
    <!-- 更多步骤 -->
  </div>
</div>
```

```css
.layout-sticky-mag {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 48px;
}
.layout-sticky-mag .sidebar {
  position: sticky;
  top: 40px;
  align-self: start;
}
.layout-sticky-mag .nav {
  list-style: none;
  counter-reset: step;
}
.layout-sticky-mag .nav li {
  counter-increment: step;
  padding: 10px 0;
  font-size: 0.85rem;
  color: var(--ink-faint);
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all 0.3s ease;
}
.layout-sticky-mag .nav li::before {
  content: counter(step, decimal-leading-zero);
  font-family: Georgia, 'Songti SC', serif;
  font-size: 1.5rem;
  font-weight: 900;
  color: rgba(47,71,103,0.2);
  min-width: 36px;
  transition: all 0.3s ease;
}
.layout-sticky-mag .nav li.active {
  color: var(--ink);
  font-weight: 700;
}
.layout-sticky-mag .nav li.active::before {
  color: var(--blue);
  font-size: 1.8rem;
}
.steps-content {
  display: flex;
  flex-direction: column;
  gap: 48px;
}
.step-item {
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 3px 16px rgba(0,0,0,0.05);
  background: #FCFCFC;
}
.step-item img {
  width: 100%;
  display: block;
}
.step-item .step-text {
  padding: 32px 36px;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 20px;
  align-items: start;
}
.step-item .step-num {
  font-family: Georgia, 'Songti SC', serif;
  font-size: 3rem;
  font-weight: 900;
  line-height: 1;
  color: rgba(47,71,103,0.15);
}
.step-item .step-info h4 {
  font-family: 'Noto Serif SC', serif;
  font-size: 1.3rem;
  font-weight: 900;
  margin-bottom: 8px;
  line-height: 1.4;
}
.step-item .step-info p {
  font-size: 1rem;
  color: var(--ink-light);
  line-height: 1.9;
}
@media (max-width: 900px) {
  .layout-sticky-mag { grid-template-columns: 1fr; }
  .layout-sticky-mag .sidebar { display: none; }
  .step-item .step-text { grid-template-columns: 1fr; }
  .step-item .step-num { font-size: 2rem; }
}
```

**JS配套**（侧栏滚动联动高亮）:
```javascript
const navItems = document.querySelectorAll('.nav li');
const stepObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const idx = parseInt(entry.target.dataset.index);
      navItems.forEach((li, i) => li.classList.toggle('active', i === idx));
    }
  });
}, { threshold: 0.35, rootMargin: '-15% 0px -50% 0px' });
document.querySelectorAll('.step-observe').forEach(el => stepObserver.observe(el));
```

⚠️ 注意：步骤5~10个最合适。超过10个太长，少于5个用横向Step连接线（#7）更紧凑。大图是关键——每一步都必须有一张占满宽度的配图。编号统一藏青，克制。移动端侧栏隐藏，变成纯纵向滚动。
