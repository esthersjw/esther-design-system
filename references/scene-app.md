# Scene: App型 / 功能型页面

> 适用于个人看板、书架、Canvas白板等功能优先的应用型页面。视觉克制，交互优先。基于 `brand-dna.md`（KAI 设计体系）落地。

---

## 核心原则

- **功能优先，视觉克制** — 装饰元素最少化，不干扰操作
- **信息密度高** — 内容紧凑，间距小于教程/Landing页（但不低于呼吸感下限）
- **交互反馈清晰** — 每个可操作元素都有hover/active状态
- **导航永远可见** — Sticky header或侧边栏，用户不迷路
- **层级靠字号字重** — 不用颜色分层级，交互态例外（见下）

---

## 📐 布局

### 基本结构
```
Sticky Header (48~64px高度)
  ↓
Tab栏 / 侧边栏导航
  ↓
内容区 (max-width: 820px ~ 1200px)
  ↓
卡片网格为主要内容承载
```

### Header
```css
.app-header {
  position: sticky;
  top: 0;
  z-index: 100;
  height: 56px;
  background: var(--cream, #FCFCFC);
  border-bottom: 1px solid rgba(42, 38, 36, 0.08);
  display: flex;
  align-items: center;
  padding: 0 1.5rem;
}
```

### 侧边栏（可选）
```css
.app-sidebar {
  position: fixed;
  top: 56px; left: 0; bottom: 0;
  width: 220px;
  padding: 1.5rem 1rem;
  border-right: 1px solid rgba(42, 38, 36, 0.08);
  overflow-y: auto;
}
.app-main {
  margin-left: 220px;
  padding: 2rem;
  max-width: 1200px;
}
```

### 内容区
```css
.app-content {
  max-width: 820px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
}

/* 宽内容区（看板/网格型） */
.app-content--wide {
  max-width: 1200px;
}
```

---

## 🎨 色彩简化规则

App型页面色彩更简洁，全部来自色板：

| 元素 | 色值 | 说明 |
|------|------|------|
| 页面背景 | `#FCFCFC` | 近白，唯一的底色 |
| 卡片 | `#FCFCFC` + `1px solid rgba(42,38,36,0.08)` + 轻阴影 | 层次靠描边，不靠底色差 |
| Header/主交互 | `var(--blue)` = `#2F4767` | 藏青做主交互色 |
| 徽章/选中态 | `var(--yellow)` = `#FAD470` | 姜黄做badge/选中标记，小面积 |
| 提示框底 | `var(--red)` = `#F3BB99` | 暖辅做温和提示（变量名沿用，值已换） |
| 危险操作 | `#FAD470` 描边 + `#2A2624` 文字 | 姜黄是体系里唯一"需要注意"的功能色 |
| 特殊功能板块 | `rgba(243,199,161,0.2)` | 暖辅浅底（不用绿色系） |

### 分类标签扩展色
功能页面分类标签可使用色板派生色（主色明暗变体、暖辅变体、透明度变体），但总色数不超 6 种：
- 所有标签底色一律低饱和、浅透明变体，文字用中性色
- 近白卡片底 + 藏青描边是App页面标准配色

---

## 🖱️ 交互标准

### Tab切换
```css
.tab-bar {
  display: flex;
  gap: 4px;
  overflow-x: auto;
  border-bottom: 2px solid rgba(42, 38, 36, 0.08);
}
.tab {
  padding: 10px 20px;
  border: none;
  background: transparent;
  cursor: pointer;
  font-size: 0.9rem;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
  transition: all .2s;
}
.tab.active {
  border-bottom-color: var(--blue);
  color: var(--blue);
  font-weight: 600;
}
```

### Modal
```css
.modal-overlay {
  position: fixed;
  inset: 0;
  z-index: 1000;
  background: rgba(42, 38, 36, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal-content {
  background: var(--cream, #FCFCFC);
  border-radius: 12px;
  padding: clamp(24px, 3vw, 40px);
  max-width: 560px;
  width: 90%;
  max-height: 80vh;
  overflow-y: auto;
}
```

### 卡片Hover
```css
.app-card {
  background: #FCFCFC;
  border: 1px solid rgba(42, 38, 36, 0.08);
  border-radius: 10px;
  padding: 1.25rem;
  box-shadow: 0 2px 12px rgba(0,0,0,.04);
  transition: transform .2s, box-shadow .2s;
  cursor: pointer;
}
.app-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0,0,0,.08);
  border-color: rgba(42, 38, 36, 0.16);
}
```

### 输入Focus
```css
.app-input {
  border: 1.5px solid rgba(42, 38, 36, 0.12);
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 0.9rem;
  transition: border-color .2s;
  background: #FCFCFC;
}
.app-input:focus {
  outline: none;
  border-color: var(--blue, #2F4767);
  box-shadow: 0 0 0 3px rgba(47, 71, 103, 0.12);
}
```

---

## 🎨 无限画布 / Canvas 规范

适用于白板、信息可视化、自由拖拽布局：

### Grid Dot背景
```css
.canvas-grid {
  width: 100%; height: 100%;
  background-image: radial-gradient(circle, rgba(47, 71, 103, 0.13) 1.2px, transparent 1.2px);
  background-size: 28px 28px;
}
```

### Cursor
```css
.canvas-area {
  cursor: grab;
}
.canvas-area:active {
  cursor: grabbing;
}
```

### Transform Origin
```css
.canvas-transform {
  position: absolute;
  transform-origin: 0 0;
  will-change: transform;
}
```

### Canvas卡片（手绘轮廓感）
```css
.canvas-card {
  background: #FCFCFC;
  border: 2px solid rgba(12, 12, 12, 0.55);
  border-radius: 10px;
  padding: 1.25rem;
  box-shadow: 0 4px 16px rgba(0,0,0,.06);
}
```

---

## 📱 响应式

- Header高度保持，内部元素简化
- 侧边栏移动端变为底部Tab或汉堡菜单
- 卡片网格：`repeat(auto-fill, minmax(260px, 1fr))`自适应
- Modal：移动端全屏或底部弹出

---

## 🚫 App页面禁忌

- 不要加大段装饰性文字（功能页不是杂志）
- 不要用Scroll Reveal（App页面要即时加载，不等动画）
- 不要用超大标题（App内标题控制在1.2rem以内）
- 不要用纯白 `#fff` 卡片底压在纯白背景上（层次靠炭黑细描边）
- 不要在功能区域加藏青大色块（藏青只做交互色和小面积header，大色块留给内容页）
