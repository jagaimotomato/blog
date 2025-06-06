---
title: "JavaScript30 挑战之旅 🎯"
description: "闲来无事做一下GitHub上的JavaScript30练习项目，记录学习过程和心得体会"
slug: Javascript30
draft: false
tags: ["代码"]
categories: ["前端"]
date: "2025-06-05T10:00:00+08:00"
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

## 🎉 总结

JavaScript30 项目通过实际动手练习，让我们：

- 💪 **强化基础**：巩固原生 JavaScript 技能
- 🎨 **提升创意**：通过有趣的项目激发编程热情
- ⚡ **快速实践**：每个项目都能快速完成，成就感满满

期待接下来的 28 个挑战！ 🔥

---

_💻 持续更新中... 敬请期待更多有趣的 JavaScript 练习项目！_
