# 质量检查清单

> 做完设计后逐条对照。P0必须全过，否则打回修改。

---

## P0（必须全过）

任何一条不过就要改：

- [ ] 品牌三色使用正确（主色60/强调30/点缀10比例）
- [ ] 没有使用禁忌清单里的任何元素（蓝紫渐变/glassmorphism/bounce动画/neon/居中病）
- [ ] 背景使用品牌暖底（默认 #fefcf6 或 #faf6eb），非纯黑纯白
- [ ] 字体用了推荐字体池里的（Fraunces/Noto Serif SC/Caveat等）
- [ ] 标题衬线+正文无衬线混搭
- [ ] 有响应式（至少900px断点）
- [ ] 截图发Twitter不会被说"又是AI做的"
- [ ] 每个section布局形式不同
- [ ] clamp()做fluid sizing
- [ ] 没有使用任何HTML默认样式（默认blockquote、默认border-left引用、无样式ul/ol、默认table）——所有组件必须从components.md选用

---

## P1（应过）

尽量满足，提升品质：

- [ ] 至少一个section有视觉惊喜（出血/3D/全宽色块/装饰突破）
- [ ] 字号对比足够极端（大的>3rem，小的<0.85rem）
- [ ] 有Scroll Reveal动效 + stagger延迟
- [ ] 使用了大装饰数字或大透明英文做背景
- [ ] 有品牌色条（border-left）或高亮标记
- [ ] ::selection用强调色高亮

---

## P2（加分）

锦上添花：

- [ ] 图片溢出容器边界
- [ ] 有全宽深色面板打破节奏
- [ ] 装饰元素（虚线圆/渐变光晕/条纹肌理）使用克制
- [ ] prefers-reduced-motion尊重
