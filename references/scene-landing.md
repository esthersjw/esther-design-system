# Scene: 活动页 / 分享会 / Landing Page

> 适用于分享会邀请页、活动报名页、产品发布Landing、合作宣传页等需要节奏感和行动转化的页面。基于 `brand-dna.md`（KAI 设计体系）落地。

---

## 核心原则

- **更大的Hero** — 首屏要有存在感，min-height: 100vh；主体占画面 25%–35%，其余让给白
- **节奏靠藏青与白的对比** — 全页最多 1~2 个全宽藏青面板，不靠颜色数量堆节奏
- **明确的CTA** — 每个逻辑段落结尾都应有下一步引导
- **情绪递进** — 痛点→方案→证据→行动
- **一屏一件事** — 每个面板只讲一件事，其余留给白

---

## 🎨 色彩

继承 brand-dna.md 的 KAI 色板（近白 65–70% / 藏青 20–25% / 中性 8–10% / 姜黄 ≤5%），活动页额外规则：

### 合作品牌色扩展（唯一的"特殊原因"）
原研哉说「若是无特殊原因，我的设计台上找不到多余颜色」——合作品牌色就是那个"特殊原因"：
- 当页面涉及合作产品/品牌时，可引入第四色替换暖辅（`--red`）的点缀位
- **规则**: 合作色只替换暖辅位置，不替换藏青主色与姜黄强调；只出现在徽章/标签这类小面积位置，一处足够
- 合作色需与藏青有明确对比，且不得与姜黄混淆

### 暗色面板色值
- 标准暗底: `#243C6C`（藏青暗变体）
- 更深底: `#2A2624`（炭黑）
- 面板文字: 近白 `#FCFCFC`；正文一律中性色，姜黄只做一处小面积焦点

---

## 📐 布局偏好

推荐的Landing Page节奏组合：

```
Hero全屏（纵向居中或双栏不对称）
  ↓
三列卡片（核心价值/嘉宾/亮点）
  ↓
全宽藏青面板（金句/核心观点）
  ↓
Sticky侧栏或时间线交错（详细内容）
  ↓
Pull Quote引用
  ↓
CTA行动区
```

### 布局要点
- Hero区域首选「单栏纵向」或「双栏不对称」
- 中间部分通过近白底与藏青面板的交替制造节奏
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

CTA 按钮统一用藏青底——姜黄不做大面积按钮底色（≤5% 铁律），姜黄在 CTA 区只做一处下划线或箭头标记。

```css
.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 16px 36px;
  background: var(--blue, #2F4767);
  color: #FCFCFC;
  border-radius: 10px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  transition: transform .2s, box-shadow .2s;
}
.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(47, 71, 103, 0.3);
}
/* hover 暗变体 */
.cta-button:hover { background: var(--blue-deep, #243C6C); }
```

### CTA区域布局
```css
.cta-section {
  text-align: center;
  padding: clamp(80px, 12vh, 160px) 2rem;
}
.cta-section h2 {
  font-family: 'Noto Serif SC', serif;
  font-size: clamp(1.5rem, 3.5vw, 2.25rem);
  margin-bottom: 1rem;
}
.cta-section p {
  font-size: 1rem;
  color: var(--ink-light, #303A43);
  margin-bottom: 2rem;
}
```

---

## ✨ 动效增强

Landing页面在教程页Scroll Reveal基础上，可额外使用：

### 数字递增（统计数据）
配合IntersectionObserver，数字从0计数到目标值。数字用藏青大字重呈现，不加发光、不加渐变。

### 入场层叠
多个卡片使用 `.reveal-d1` ~ `.reveal-d5` 做stagger，间隔0.1s。

> 不要用无限循环动画（旋转轨道、脉冲光圈等）——克制是这套视觉的辨识度。

---

## 📱 响应式要点

- Hero区域移动端：双栏变单栏，图片在文字下方
- 三列卡片：移动端变单列
- CTA按钮：移动端宽度100%
- Pull Quote：移动端减小padding和字号

---

## 🚫 Landing页禁忌

- 不要在藏青面板上放大段姜黄文字（姜黄只做一处小面积焦点）
- 不要超过3个CTA按钮（选择越少转化越高）
- 不要用stock photo风格的图片
- 不要用多种品牌色面板交替（节奏靠藏青与白的对比，不靠颜色数量）
- 不要塞满信息——每个面板只讲一件事，其余留给白
