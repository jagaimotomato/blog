# Hugo 博客部署到 GitHub Pages 指南

## 前置条件

1. GitHub 账号
2. 本地 Git 环境
3. Hugo 博客项目（已完成）

## 部署步骤

### 1. 在 GitHub 上创建仓库

1. 登录 [GitHub](https://github.com)
2. 点击右上角的 "+" → "New repository"
3. 仓库设置：
   - **Repository name**: `blog`
   - **Description**: `我的Hugo博客`
   - **Visibility**: Public
   - **不要**勾选 "Add a README file"
   - **不要**勾选 "Add .gitignore"
   - **不要**选择 "Choose a license"
4. 点击 "Create repository"

### 2. 推送代码到 GitHub

```bash
# 如果网络问题，可以尝试使用SSH方式
# 首先设置SSH密钥（如果还没有的话）

# 推送代码
git push -u origin main
```

如果遇到网络问题，可以：

- 使用 SSH 方式：`git remote set-url origin git@github.com:jagaimotomato/blog.git`
- 或者使用代理
- 或者稍后再试

### 3. 配置 GitHub Pages

推送成功后，在 GitHub 仓库页面：

1. 点击 **Settings** 标签页
2. 在左侧菜单中找到 **Pages**
3. 在 "Source" 部分选择：
   - Source: **GitHub Actions**
4. 保存设置

### 4. 查看部署状态

1. 点击 **Actions** 标签页
2. 你会看到 "Deploy Hugo site to Pages" 工作流正在运行
3. 等待工作流完成（通常需要 1-3 分钟）
4. 完成后会显示绿色的 ✅

### 5. 访问你的网站

部署完成后，你的网站将在以下地址可用：

```
https://jagaimotomato.github.io/blog/
```

## 后续更新流程

每次更新博客内容后：

```bash
# 1. 添加更改
git add .

# 2. 提交更改
git commit -m "更新博客内容"

# 3. 推送到GitHub
git push

# 4. GitHub Actions会自动部署
```

## 自定义域名（可选）

如果你有自己的域名：

1. 在仓库根目录创建 `static/CNAME` 文件
2. 在文件中写入你的域名，如：`blog.yourdomain.com`
3. 在域名 DNS 设置中添加 CNAME 记录，指向 `jagaimotomato.github.io`

## 常见问题

### 1. 构建失败

- 检查 Hugo 版本是否匹配
- 确保所有子模块正确初始化

### 2. 页面空白

- 检查 baseURL 是否正确设置
- 确保主题文件完整

### 3. 图片不显示

- 确保图片路径正确
- 检查图片是否在正确的目录中

### 4. 推送失败

- 检查网络连接
- 确认 GitHub 仓库地址正确
- 检查 Git 凭证

## 工作流文件说明

`.github/workflows/hugo.yml` 文件的作用：

- 自动检测 main 分支的推送
- 使用 Ubuntu 环境构建 Hugo 网站
- 自动部署到 GitHub Pages
- 支持子模块（主题）
- 包含缓存优化
