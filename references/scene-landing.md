# Scene: 活动页 / 分享会 / Landing Page

> 适用于分享会邀请页、活动报名页、产品发布Landing、合作宣传页等需要强节奏感和行动转化的页面。

---

## 核心原则

- **更大的Hero** — 首屏要有冲击力，min-height: 100vh
- **更强的节奏感** — 深浅面板交替频率高于教程页
- **深色面板对比多** — 至少1~2个全宽深色或品牌色面板
- **明确的CTA** — 每个逻辑段落结尾都应有下一步引导
- **情绪递进** — 痛点→方案→证据→行动

---

## 🎨 色彩

继承 brand-dna.md 的三色体系，额外规则：

### 合作品牌色扩展
当页面涉及合作产品/品牌时，可引入第四色替代暖棕的点缀位：
- YU 合作: `#F1752D`（橙色），替代暖棕作为强调色
- 金橙: `#F7A946`（偏金），用于slogan/时间标识
- **规则**: 第四色只替代暖棕位置，不替代蓝/黄主色

### 暗色面板色值
- 标准暗底: `#1A1A2E`
- 深色底: `#0d1117`
- 梨黄底: `var(--pear)` + 白字
- 品牌黄底: `var(--blue)` + 墨色字

---

## 📐 布局偏好

推荐的Landing Page节奏组合：

```
Hero全屏（纵向居中或双栏不对称）
  ↓
三列卡片（核心价值/嘉宾/亮点）
  ↓
全宽深色面板（金句/核心观点）
  ↓
Sticky侧栏或时间线交错（详细内容）
  ↓
Pull Quote引用
  ↓
CTA行动区
```

### 布局要点
- Hero区域首选「单栏纵向」或「双栏不对称」
- 中间部分通过深浅色背景交替制造节奏
- 结尾必须有明确的CTA面板

---

## 🧩 组件偏好

Landing页面高频使用的组件：

### Pull Quote（大字引用+装饰引号）
用于嘉宾金句、核心slogan。参见 `components.md #6`。

### 系统流程条（Flow Arrow）
用于展示产品/活动流程。参见 `components.md #11`。

### 头像集群（Avatar Cluster）
用于嘉宾/团队展示。参见 `components.md #15`。

### Do/Don't对比列表
用于痛点展示、方案对比。参见 `components.md #12`。

---

## 🔘 CTA按钮样式标准

```css
.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 16px 36px;
  background: var(--pear, #F0E4D2);
  color: #fff;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  transition: transform .2s, box-shadow .2s;
}
.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(240,228,210,0.3);
}

/* 黄色变体（用于深色背景上） */
.cta-button--blue {
  background: var(--blue, #9EC1C0);
  color: var(--ink, #1A1A2E);
}
.cta-button--blue:hover {
  box-shadow: 0 8px 24px rgba(158,193,192,0.3);
}
```

### CTA区域布局
```css
.cta-section {
  text-align: center;
  padding: clamp(80px, 12vh, 160px) 2rem;
}
.cta-section h2 {
  font-family: 'Noto Serif SC', serif;
  font-size: clamp(1.6rem, 4vw, 2.6rem);
  margin-bottom: 1rem;
}
.cta-section p {
  font-size: 1rem;
  color: var(--ink-light, #4A4A5A);
  margin-bottom: 2rem;
}
```

---

## ✨ 动效增强

Landing页面在教程页Scroll Reveal基础上，可额外使用：

### 轨道旋转（头像集群）
```css
@keyframes heroSpin {
  to { transform: rotate(360deg); }
}
.ring {
  animation: heroSpin 20s linear infinite;
}
```

### 数字递增（统计数据）
配合IntersectionObserver，数字从0计数到目标值。

### 入场层叠
多个卡片使用 `.reveal-d1` ~ `.reveal-d5` 做stagger，间隔0.1s。

---

## 📱 响应式要点

- Hero区域移动端：双栏变单栏，图片在文字下方
- 三列卡片：移动端变单列
- CTA按钮：移动端宽度100%
- Pull Quote：移动端减小padding和字号

---

## 🚫 Landing页禁忌

- 不要在品牌色面板上放同色文字（蓝底不放蓝字）
- 不要超过3个CTA按钮（选择越少转化越高）
- 不要用stock photo风格的图片
- 不要所有section都用白底（必须有节奏对比）
