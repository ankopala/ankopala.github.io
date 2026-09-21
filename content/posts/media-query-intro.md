+++
title = '媒体查询（Media Query）与 @media 用法'
date = '2026-09-21T15:20:29+08:00'
draft = false
tags = ['html', 'css']
ShowToc = true
description = '媒体查询（Media Query）与 @media 用法'
+++

> 背景：做博客「左侧目录」的窄屏适配时，用到了 `@media` 让目录在窄屏下隐藏/缩小。这里系统记录媒体查询是什么、怎么用。

---

## 一、媒体查询是什么

一句话：**媒体查询（Media Query）是 CSS 里的一种"条件判断"，让某些样式只在"满足特定条件"时生效。**

最常用的条件是"屏幕宽度"，但也可以是设备类型、屏幕方向（横屏/竖屏）、是否支持某功能等。

它和编程里的 `if` 语句是同一个思想：

```css
/* 如果屏幕宽度 ≤ 1200px，就应用里面这些样式 */
@media (max-width: 1200px) {
    .toc-sidebar {
        display: none;
    }
}
```

这等价于（用伪代码表达）：

```
如果 (屏幕宽度 <= 1200px) {
    隐藏 .toc-sidebar
}
```

---

## 二、@media 的基本语法

结构是固定的，记住这个骨架：

```css
@media 条件 {
    选择器 {
        属性: 值;
    }
}
```

- `@media` 是关键字
- 括号里写"条件"
- 花括号里写"满足条件时要应用的样式"
- 里面的写法和普通 CSS 完全一样

---

## 三、最常用的宽度条件

### 1. `max-width`（小于等于某个宽度时生效）

```css
@media (max-width: 768px) {
    /* 屏幕 ≤ 768px（手机）时生效 */
}
```

**记忆**：`max-width` = "最多就这么宽"，所以是**"小屏时生效"**。

### 2. `min-width`（大于等于某个宽度时生效）

```css
@media (min-width: 1200px) {
    /* 屏幕 ≥ 1200px（大屏）时生效 */
}
```

**记忆**：`min-width` = "至少这么宽"，所以是**"大屏时生效"**。

### 3. 组合区间（一个范围）

```css
@media (min-width: 768px) and (max-width: 1200px) {
    /* 屏幕在 768px ~ 1200px 之间时生效 */
}
```

用 `and` 把两个条件连起来，表达"在某个范围内"。

---

## 四、其他常用条件（了解即可）

| 条件 | 作用 | 例子 |
|------|------|------|
| `orientation: portrait` | 竖屏 | `@media (orientation: portrait)` |
| `orientation: landscape` | 横屏 | `@media (orientation: landscape)` |
| `prefers-color-scheme: dark` | 用户偏好深色模式 | `@media (prefers-color-scheme: dark)` |
| `hover: none` | 设备不支持悬停（触屏） | `@media (hover: none)` |

其中最实用的是 `prefers-color-scheme`（深色模式适配），以后做"跟随系统深色"会用到。

---

## 五、移动端优先 vs 桌面端优先

媒体查询有两种书写思路，理解这个能少走弯路：

### 桌面端优先（Desktop-first）

先写"大屏"样式（默认），再用 `max-width` 往下"缩"：

```css
/* 默认：大屏样式 */
.toc-sidebar { width: 260px; }

/* 屏幕变窄时，一步步调整 */
@media (max-width: 1300px) { .toc-sidebar { width: 200px; } }
@media (max-width: 1100px) { .toc-sidebar { display: none; } }
```

**特点**：从大到小，用 `max-width`。适合"先做桌面版，再适配手机"的场景——**你现在的博客就是这种**。

### 移动端优先（Mobile-first）

先写"小屏"样式（默认），再用 `min-width` 往上"加"：

```css
/* 默认：小屏（手机）样式 */
.toc-sidebar { display: none; }

/* 屏幕变宽时，逐步增强 */
@media (min-width: 1100px) { .toc-sidebar { display: block; } }
```

**特点**：从小到大，用 `min-width`。是当前主流推荐的做法。

---

## 六、媒体查询的两个"坑"

### 坑 1：断点（breakpoint）是"猜"出来的

媒体查询里的宽度值（1200px、768px 等）叫**断点**。问题是——**屏幕尺寸无穷多，断点写不完**。

比如你设了 1200px 隐藏目录，但用户的屏幕是 1199px 还是 1210px，效果差别可能很大，你没法为每个像素都写一条。

**这是媒体查询的固有局限**，也是为什么"复杂的响应式布局"最终要配合其他技术（比如 `position: sticky`、flex、grid）一起用，而不是全靠媒体查询硬撑。

### 坑 2：断点要和"内容"匹配，不是抄别人的

网上常有人说"768px 是平板、1024px 是桌面"——这些是**参考值**，不是金科玉律。

正确的做法是：**根据你自己的内容"什么时候会挤"来定断点**。比如你正文 900px + 目录 260px，那大概 1200px 以下就会挤，所以断点设 1200px。换个内容，断点就该换。

---

## 七、媒体查询 vs position: sticky

回顾一下两者的定位（呼应 `why-position-sticky.md`）：

| | 媒体查询 | position: sticky |
|---|---|---|
| 思路 | "补丁式"：到了某宽度就改样式 | "结构性"：从根上让布局自适应 |
| 解决的问题 | 临时补救重叠 | 从根本上避免重叠 |
| 局限 | 断点写不完，要猜 | 需配合 HTML 结构 |

**结论**：媒体查询是**好用的工具**，但不是**万能的**。它擅长"简单的开关式调整"（比如窄屏隐藏目录、切换字号），但面对"复杂布局的重叠"问题，更该用 `sticky`/`flex`/`grid` 这类结构性方案。

---

## 八、速记关键词

- **媒体查询（media query）**：CSS 的条件判断，满足条件才生效。
- **`max-width`**：小于等于某宽度时生效（小屏适配）。
- **`min-width`**：大于等于某宽度时生效（大屏增强）。
- **断点（breakpoint）**：媒体查询里的宽度分界值。
- **桌面端优先**：默认大屏，用 `max-width` 往下缩。
- **移动端优先**：默认小屏，用 `min-width` 往上加。
- **媒体查询的局限**：断点是"猜"的，复杂布局要配合结构性方案。
