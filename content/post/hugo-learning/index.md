---
title: "Hugo 静态网站生成器学习笔记"
description: "从零开始学习Hugo的完整记录，包括安装配置、主题选择、内容管理等实用技巧。"
slug: hugo-learning
date: 2025-05-27T09:00:00+08:00
lastmod: 2025-05-27T09:00:00+08:00
draft: false
author: "Joy"
authorLink: "https://github.com/jagaimotomato"
authorEmail: "your-email@example.com"
authorAvatar: "img/avatar.png"
tags: ["Hugo", "静态网站", "学习笔记", "建站"]
categories: ["学习笔记", "技术"]
featuredImage: ""
featuredImagePreview: ""
---

最近开始学习使用 Hugo 构建静态网站，记录一下学习过程中的重点内容和踩过的坑。

<!--more-->

## 什么是 Hugo？

Hugo 是一个用 Go 语言编写的静态网站生成器，以其极快的构建速度而闻名。

### 主要优势

- ⚡ **速度极快**：构建大型网站只需几秒
- 🚀 **部署简单**：生成纯静态文件
- 🔧 **配置灵活**：强大的模板系统
- 📱 **响应式**：移动端友好
- 🔍 **SEO 优化**：天然支持 SEO

## 安装和初始化

### 1. 安装 Hugo

```bash
# macOS (使用Homebrew)
brew install hugo

# 验证安装
hugo version
```

### 2. 创建新站点

```bash
# 创建新站点
hugo new site my-blog

# 进入目录
cd my-blog

# 初始化Git仓库
git init
```

### 3. 添加主题

```bash
# 添加主题为子模块
git submodule add https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack

# 在配置文件中指定主题
echo "theme = 'hugo-theme-stack'" >> hugo.toml
```

## 目录结构

```
my-blog/
├── content/          # 内容文件
│   ├── post/        # 博客文章
│   └── _index.md    # 首页内容
├── static/          # 静态资源
├── assets/          # 需要处理的资源
├── themes/          # 主题文件
├── layouts/         # 自定义模板
└── hugo.toml        # 配置文件
```

## 配置文件详解

### 基本配置

```toml
baseURL = "https://example.com"
languageCode = "zh-cn"
title = "我的博客"
theme = "hugo-theme-stack"

# 中文支持
hasCJKLanguage = true
defaultContentLanguage = "zh-cn"

# 输出格式（用于搜索）
[outputs]
home = ["HTML", "RSS", "JSON"]
```

### 菜单配置

```toml
[[menu.main]]
    name = "首页"
    url = "/"
    weight = 10
    [menu.main.params]
        icon = "home"

[[menu.main]]
    name = "归档"
    url = "/archives"
    weight = 20
    [menu.main.params]
        icon = "archives"
```

### 作者信息

```toml
[params.author]
name = "你的名字"
email = "your-email@example.com"

[params.sidebar]
emoji = "🍥"
subtitle = "你的个人简介"

[params.sidebar.avatar]
enabled = true
local = true
src = "img/avatar.png"
```

## 内容管理

### 1. 创建文章

```bash
# 创建新文章
hugo new post/my-first-post/index.md
```

### 2. Front Matter

```yaml
---
title: "文章标题"
description: "文章描述"
slug: "url-slug"
date: 2025-05-27T09:00:00+08:00
draft: false
tags: ["标签1", "标签2"]
categories: ["分类"]
---
```

### 3. 文章摘要

使用 `<!--more-->` 标记来分割摘要和正文：

```markdown
这是文章的摘要部分。

<!--more-->

这是文章的正文内容。
```

## 常用命令

```bash
# 启动开发服务器
hugo server

# 构建生产版本
hugo

# 创建新内容
hugo new post/article-name/index.md

# 清理缓存
hugo server --ignoreCache
```

## 学习过程中的问题和解决方案

### 1. 中文字符显示问题

**问题**：中文字符在 URL 中显示异常
**解决**：在配置中添加：

```toml
hasCJKLanguage = true
```

### 2. 头像不显示

**问题**：配置了头像路径但不显示
**解决**：

- 确保图片放在 `assets/` 目录下，不是 `static/`
- Stack 主题使用 `resources.Get()` 处理图片

### 3. 菜单重复

**问题**：菜单项重复显示
**解决**：

- 确保所有菜单配置都在 `hugo.toml` 中
- 删除主题配置文件中的重复配置

### 4. 搜索功能不工作

**问题**：搜索页面无法找到内容
**解决**：

```toml
[outputs]
home = ["HTML", "RSS", "JSON"]
```

## 优化技巧

### 1. 图片优化

```toml
[params.imageProcessing.cover]
enabled = true

[params.imageProcessing.content]
enabled = true
```

### 2. SEO 优化

```yaml
# 在文章的Front Matter中
seo:
  images: ["featured-image.jpg"]
```

### 3. 社交分享

```toml
[params.article]
share:
  enable = true
```

## 部署选项

### 1. GitHub Pages

- 免费托管
- 自动构建
- 支持自定义域名

### 2. Netlify

- 持续部署
- 表单处理
- CDN 加速

### 3. Vercel

- 零配置部署
- 全球 CDN
- 实时预览

## 学习资源

- 📖 [Hugo 官方文档](https://gohugo.io/documentation/)
- 🎨 [Hugo 主题库](https://themes.gohugo.io/)
- 💬 [Hugo 社区论坛](https://discourse.gohugo.io/)
- 📺 [Hugo 教程视频](https://www.youtube.com/results?search_query=hugo+tutorial)

## 总结

Hugo 是一个功能强大且灵活的静态网站生成器。虽然初期学习曲线有点陡峭，但一旦掌握了基本概念，就能快速构建出专业的网站。

**关键点**：

- 理解目录结构的作用
- 掌握配置文件的语法
- 熟悉 Front Matter 的使用
- 了解主题的工作原理

继续学习 Hugo 的高级功能，比如自定义 Shortcodes、多语言支持等，让网站更加个性化！
