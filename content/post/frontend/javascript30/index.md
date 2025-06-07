---
title: "JavaScript30 挑战之旅 🎯"
description: "闲来无事做一下GitHub上的JavaScript30练习项目，记录学习过程和心得体会"
slug: Javascript30
draft: false
tags: ["代码"]
categories: ["前端"]
date: "2025-06-05T10:00:00+08:00"
lastmod: "2025-06-07T11:00:00+08:00"
---

> 🚀 **JavaScript30** 是一个为期 30 天的 JavaScript 挑战项目，通过 30 个不同的小项目来提升原生 JavaScript 技能。

## 🎵 Day 01 - JavaScript Drum Kit

### 📝 项目描述

实现一个模拟打鼓的交互式页面，让用户通过键盘按键来演奏不同的鼓点。

### ✨ 功能特性

- 🎹 **键盘交互**：用户按下 `A` `S` `D` `F` `G` `H` `J` `K` `L` 键
- 🎨 **视觉反馈**：对应按钮会变大变亮，提供即时的视觉响应
- 🔊 **音效播放**：每个按键对应不同的鼓点声音
- ⚡ **流畅体验**：按键响应迅速，支持连续敲击

### 🎯 学习要点

- **事件监听**：`keydown` 事件的处理
- **DOM 操作**：动态添加/移除 CSS 类
- **音频 API**：HTML5 Audio 元素的使用
- **CSS 动画**：transition 和 transform 的应用

### 🔗 在线预览

👉 [点击体验 Drum Kit](https://jagaimotomato.github.io/javascript30/drumKit/index.html)

### 💡 核心技术

```javascript
// 核心实现思路
function playSound(e) {
  const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
  const key = document.querySelector(`div[data-key="${e.keyCode}"]`);

  if (!audio) return;

  key.classList.add("playing");
  audio.currentTime = 0;
  audio.play();
}
```

---

## 🕐 Day 02 - CSS + JS 时钟

### 📝 项目描述

制作一个漂亮甜美的模拟时钟，实时显示当前时间，包含时针、分针、秒针三个指针的动画效果。

### ✨ 功能特性

- 🕰️ **实时时间**：显示当前准确时间
- ⏰ **三针联动**：时针、分针、秒针同步更新
- 🎯 **精准计算**：指针角度精确到每秒每分
- 🎨 **优雅样式**：圆形时钟面板配合阴影效果
- 🔄 **12 小时制**：支持标准 12 小时时间格式

### 🎯 学习要点

- **定时器**：`setInterval()` 的使用
- **时间对象**：JavaScript `Date` 对象操作
- **CSS Transform**：`rotate()` 和 `translate()` 变换
- **数学计算**：角度换算（时针 30°/小时，分秒针 6°/单位）
- **DOM 查询**：`querySelector()` 选择器

### 🔗 在线预览

👉 [点击体验 Clock](https://jagaimotomato.github.io/javascript30/clock/index.html)

### 💡 核心技术

```javascript
// 时钟核心逻辑
setInterval(() => {
  const date = new Date();
  let hour = date.getHours();
  const min = date.getMinutes();
  const sec = date.getSeconds();

  // 12小时制转换
  if (hour > 12) hour -= 12;
  if (hour === 0) hour = 12;

  // 角度计算
  const houroffset = hour * 30 + min * 0.5; // 时针每分钟0.5度
  const minoffset = min * 6; // 分针每分钟6度
  const secoffset = sec * 6; // 秒针每秒6度

  // 应用变换
  hourhand.style.transform = `translate(-50%, -100%) rotate(${houroffset}deg)`;
  minhand.style.transform = `translate(-50%, -100%) rotate(${minoffset}deg)`;
  sechand.style.transform = `translate(-50%, -100%) rotate(${secoffset}deg)`;
}, 1000);
```

### 🔧 技术细节

- **指针差异化**：不同长度的指针便于区分（时针 40%，分针 45%，秒针 50%）
- **变换原点**：`transform-origin: 50% 100%` 让指针从底部旋转
- **平滑过渡**：可添加 `transition` 实现更流畅的动画效果
- **背景美化**：使用 Unsplash 随机图片作为背景

---

## 🎨 Day 03 - CSS Variables + JS

### 📝 项目描述

使用 JavaScript 动态更新 CSS 变量，实现图片的实时样式调整，包括边距、模糊度和主题色彩的交互式控制。

### ✨ 功能特性

- 🎛️ **滑块控制**：通过 range 输入框调整数值
- 🌈 **颜色选择器**：实时更改主题色彩
- 🔄 **实时预览**：拖动时即时看到效果变化
- 📐 **多属性控制**：同时调整 padding、blur、background
- ⚡ **平滑过渡**：CSS transition 提供流畅的变化效果

### 🎯 学习要点

- **CSS 变量**：`:root` 中定义全局 CSS custom properties
- **CSS 函数**：`var()` 函数的使用方法
- **数据属性**：HTML `data-*` 属性的应用
- **事件类型**：`change` 和 `mousemove` 事件的区别
- **DOM 样式操作**：`setProperty()` 方法动态更新样式

### 🔗 在线预览

👉 [点击体验 CSS Variables](https://jagaimotomato.github.io/javascript30/cssVariables/index.html)

### 💡 核心技术

```javascript
// CSS 变量更新核心逻辑
function handleUpdate() {
  // 获取单位（px 或空字符串）
  const suffix = this.dataset.sizing || "";

  // 更新CSS变量
  document.documentElement.style.setProperty(
    `--${this.name}`,
    this.value + suffix
  );
}

// 事件监听器绑定
const inputs = document.querySelectorAll(".controls input");
inputs.forEach((input) => {
  input.addEventListener("change", handleUpdate); // 完成更改时
  input.addEventListener("mousemove", handleUpdate); // 拖动时实时更新
});
```

### 🔧 技术细节

- **CSS 变量定义**：在 `:root` 中定义 `--base`、`--spacing`、`--blur`
- **变量应用**：`padding: var(--spacing)` 等语法使用变量
- **数据驱动**：通过 `data-sizing` 属性动态添加单位
- **事件优化**：同时监听 `change` 和 `mousemove` 确保最佳用户体验

---

## 💪 Day 04 - Array Cardio Day 1

### 📝 项目描述

通过 8 个练习深入掌握 JavaScript 数组的核心方法，包括 filter、map、sort、reduce 等，所有结果都会在浏览器控制台中显示。

### ✨ 功能特性

- 🔍 **数据过滤**：根据条件筛选数组元素
- 🔄 **数据转换**：将数组元素映射为新形式
- 📊 **数据排序**：按不同规则对数组进行排序
- 🧮 **数据统计**：使用 reduce 进行复杂计算
- 📝 **控制台输出**：清晰展示每个练习的结果

### 🎯 学习要点

- **Array.filter()**：过滤符合条件的元素
- **Array.map()**：将数组转换为新格式
- **Array.sort()**：自定义排序规则
- **Array.reduce()**：累加器模式的应用
- **字符串处理**：split()、includes()、localeCompare() 方法

### 🔗 在线预览

👉 [点击体验 Array Cardio](https://jagaimotomato.github.io/javascript30/arrayCardio/index.html)

### 💡 核心技术

```javascript
// 1. 过滤1500年代出生的发明家
const fifteenHundreds = inventors.filter(
  (person) => person.year >= 1500 && person.year < 1600
);

// 2. 获取发明家姓名
const fullNames = inventors.map(
  (inventor) => `${inventor.first} ${inventor.last}`
);

// 3. 按出生年份排序
const ordered = inventors.sort((a, b) => a.year - b.year);

// 4. 计算所有发明家总寿命
const totalYears = inventors.reduce((total, inventor) => {
  return total + (inventor.passed - inventor.year);
}, 0);

// 8. 统计数据出现次数
const transportation = data.reduce((obj, item) => {
  obj[item] = obj[item] ? obj[item] + 1 : 1;
  return obj;
}, {});
```

### 🔧 技术细节

- **过滤条件**：使用逻辑运算符组合多个条件
- **排序比较**：`a - b` 升序，`b - a` 降序
- **累加器初值**：reduce 第二个参数的重要性
- **字符串处理**：`split(", ")` 分割姓名格式
- **对象计数**：使用对象作为计数器的技巧

### 📚 练习列表

1. **时代过滤** - 筛选 1500 年代发明家
2. **姓名提取** - 组合姓名字符串
3. **年龄排序** - 按出生年份排序
4. **寿命统计** - 计算总生存年数
5. **寿命排序** - 按寿命长短排序
6. **名称搜索** - 查找包含特定字符的条目
7. **字母排序** - 按姓氏字母顺序排序
8. **数量统计** - 统计各项目出现次数

---

## 📱 Day 05 - Flex Panels 图片展示

### 📝 项目描述

创建一个响应式的图片面板展示效果，点击面板时会展开并显示完整的文字内容，结合 Flexbox 布局和 CSS 动画实现流畅的交互体验。

### ✨ 功能特性

- 🖼️ **五个面板**：每个面板都有独特的背景图片
- 🎯 **点击展开**：点击面板触发展开动画
- 📝 **文字动画**：上下文字滑入滑出效果
- 🎨 **平滑过渡**：使用 CSS transition 实现流畅动画
- 📱 **响应式设计**：适配不同屏幕尺寸

### 🎯 学习要点

- **Flexbox 布局**：`display: flex` 和 `flex` 属性的应用
- **CSS Transform**：`translateY()` 实现文字滑动效果
- **事件委托**：使用 `this` 在事件处理函数中引用当前元素
- **CSS 类切换**：`classList.toggle()` 方法的使用
- **定时器应用**：`setTimeout()` 控制动画时序

### 🔗 在线预览

👉 [点击体验 Flex Gallary](https://jagaimotomato.github.io/javascript30/flexGallary/index.html)

### 💡 核心技术

```javascript
// 面板点击处理逻辑
const panels = document.querySelectorAll(".panel");

panels.forEach((panel) =>
  panel.addEventListener("click", function (e) {
    // 切换展开状态
    this.classList.toggle("open");

    // 延迟添加文字动画
    setTimeout(() => {
      this.classList.toggle("open-active");
    }, 1000);
  })
);
```

### 🔧 技术细节

- **Flexbox 展开**：`flex: 5` 让点击的面板占据更多空间
- **文字定位**：`translateY(-100%)` 和 `translateY(100%)` 隐藏上下文字
- **动画时序**：先展开面板，延迟 1 秒后显示文字
- **CSS 选择器**：`:nth-child()` 和 `:first-child`、`:last-child` 的使用
- **过渡函数**：`cubic-bezier()` 自定义缓动效果

### 🎨 CSS 关键样式

```css
/* 面板基础布局 */
.panels {
  display: flex;
  min-height: 100vh;
}

.panel {
  flex: 1 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  transition: flex 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11);
}

/* 展开状态 */
.panel.open {
  flex: 5;
  font-size: 40px;
}

/* 文字滑动效果 */
.panel p:nth-child(1) {
  transform: translateY(-100%);
}
.panel p:nth-child(3) {
  transform: translateY(100%);
}
.panel.open-active > *:first-child,
.panel.open-active > *:last-child {
  transform: translateY(0);
}
```

---

## 🎉 总结

JavaScript30 项目通过实际动手练习，让我们：

- 💪 **强化基础**：巩固原生 JavaScript 技能
- 🎨 **提升创意**：通过有趣的项目激发编程热情
- ⚡ **快速实践**：每个项目都能快速完成，成就感满满

期待接下来的 25 个挑战！ 🔥

---

_💻 持续更新中... 敬请期待更多有趣的 JavaScript 练习项目！_
