# Scene: App型 / 功能型页面

> 适用于个人看板、书架、Canvas白板等功能优先的应用型页面。视觉克制，交互优先。

---

## 核心原则

- **功能优先，视觉克制** — 装饰元素最少化，不干扰操作
- **信息密度高** — 内容紧凑，间距小于教程/Landing页
- **交互反馈清晰** — 每个可操作元素都有hover/active状态
- **导航永远可见** — Sticky header或侧边栏，用户不迷路

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
  background: var(--cream, #fefcf6);
  border-bottom: 1px solid rgba(26,26,26,.06);
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
  border-right: 1px solid rgba(26,26,26,.06);
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

App型页面色彩更简洁：

| 元素 | 色值 | 说明 |
|------|------|------|
| 背景 | `#fefcf6` | 保持品牌暖底 |
| 卡片 | `#fff` | 白卡片浮于背景上 |
| Header/Badge | `var(--pear)` | 梨黄做主交互色 |
| 强调/边框 | `var(--blue)` | 黄色做border/badge |
| 危险操作 | `var(--brown)` | 暖棕仅用于删除/警告 |
| 绿色板块 | `#2d6a4f` | 特殊功能板块（如梦境/自然） |

### 分类标签扩展色
功能页面分类标签可使用扩展色，但总色板不超6种：
- 所有扩展色饱和度应低于主三色
- 白色卡片底 + 品牌色header是App页面标准配色

---

## 🖱️ 交互标准

### Tab切换
```css
.tab-bar {
  display: flex;
  gap: 4px;
  overflow-x: auto;
  border-bottom: 2px solid #eee;
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
  border-bottom-color: var(--ink);
  color: var(--ink);
  font-weight: 600;
}
```

### Modal
```css
.modal-overlay {
  position: fixed;
  inset: 0;
  z-index: 1000;
  background: rgba(0,0,0,.6);
  backdrop-filter: blur(4px);
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal-content {
  background: var(--cream, #fefcf6);
  border-radius: 16px;
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
  background: #fff;
  border-radius: 12px;
  padding: 1.25rem;
  box-shadow: 0 2px 12px rgba(0,0,0,.04);
  transition: transform .2s, box-shadow .2s;
  cursor: pointer;
}
.app-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0,0,0,.08);
}
```

### 输入Focus
```css
.app-input {
  border: 1.5px solid rgba(26,26,26,.1);
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 0.9rem;
  transition: border-color .2s;
  background: #fff;
}
.app-input:focus {
  outline: none;
  border-color: var(--pear, #F0E4D2);
  box-shadow: 0 0 0 3px rgba(240,228,210,0.1);
}
```

---

## 🎨 无限画布 / Canvas 规范

适用于白板、信息可视化、自由拖拽布局：

### Grid Dot背景
```css
.canvas-grid {
  width: 100%; height: 100%;
  background-image: radial-gradient(circle, rgba(74,124,201,0.13) 1.2px, transparent 1.2px);
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

### Canvas卡片（手绘感）
```css
.canvas-card {
  background: #fff;
  border: 2px dashed rgba(74,124,201,0.35);
  border-radius: 16px;
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
- 不要在功能区域加深色面板（深色只用于夜间模式场景）
