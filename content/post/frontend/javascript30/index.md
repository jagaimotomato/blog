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

## 🎉 总结

JavaScript30 项目通过实际动手练习，让我们：

- 💪 **强化基础**：巩固原生 JavaScript 技能
- 🎨 **提升创意**：通过有趣的项目激发编程热情
- ⚡ **快速实践**：每个项目都能快速完成，成就感满满

期待接下来的 29 个挑战！ 🔥

---

_💻 持续更新中... 敬请期待更多有趣的 JavaScript 练习项目！_
