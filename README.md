# 逃之夭夭's Blog

基于 [Quarto](https://quarto.org/) 构建的技术博客，托管于 GitHub Pages。

## 简介

这是一个使用 Quarto 搭建的个人技术博客，支持使用 Jupyter Notebook (`.ipynb`) 或 Quarto Markdown (`.qmd`) 撰写文章。博客采用中文写作，启用了 Giscus 评论系统。

## 特性

- 📝 支持 Jupyter Notebook 和 Markdown 撰写文章
- 🎨 基于 Bootswatch Flatly 主题 + 自定义样式
- 💬 集成 Giscus 评论系统（基于 GitHub Discussions）
- 🚀 推送到 main 分支自动部署到 GitHub Pages
- 📦 使用 uv 管理 Python 依赖
- 🏷️ 支持文章分类

## 本地开发

### 环境要求

- [Quarto CLI](https://quarto.org/docs/getting-started/install.html)
- Python 3.13
- [uv](https://github.com/astral-sh/uv)（Python 包管理器）

### 安装依赖

```bash
# 安装/同步 Python 依赖
uv sync
```

### 预览网站

```bash
# 启动本地开发服务器（支持实时预览）
quarto preview
```

访问 `http://localhost:6334` 查看效果。

### 渲染网站

```bash
# 构建网站到 _site 目录
quarto render
```

## 写作

### 新建文章

在 `posts/` 目录下创建子目录，并添加 `index.ipynb` 或 `index.qmd` 文件：

```
posts/
└── your-post-title/
    └── index.ipynb  (或 index.qmd)
```

### 文章配置

在文章的 YAML frontmatter 中添加元数据：

```yaml
---
title: "文章标题"
date: 2025-01-25
categories: [分类1, 分类2]
image: "cover-image.jpg"
---
```

共享配置位于 `posts/_metadata.yml`，会影响所有文章。

### 代码执行

- 当前配置启用了 `freeze: true`，代码计算输出会被冻结
- 编辑包含代码的文章时，如需重新执行，可临时禁用 freeze 或手动执行单元格

## 项目结构

```
.
├── _quarto.yml              # Quarto 主配置文件
├── index.qmd                # 首页（文章列表）
├── about.qmd                # 关于页面
├── styles.css               # 自定义样式
├── pyproject.toml           # Python 依赖配置
├── posts/                   # 博客文章目录
│   ├── _metadata.yml        # 文章共享配置
│   └── [post-name]/         # 单篇文章目录
│       └── index.ipynb      # 文章内容
├── .github/
│   └── workflows/
│       └── quarto_publish.yml  # GitHub Actions 部署配置
├── _site/                   # 构建输出目录（gitignore）
└── .quarto/                 # Quarto 缓存目录（gitignore）
```

## 部署

本项目使用 GitHub Actions 自动部署：

1. 推送代码到 `main` 分支
2. GitHub Actions 自动触发构建
3. 构建完成后发布到 `gh-pages` 分支
4. GitHub Pages 自动更新

手动部署命令：

```bash
quarto publish gh-pages
```

## 主题自定义

- **基础主题**：Flatly（Bootswatch）
- **自定义主题**：brand（本地自定义层）
- **自定义样式**：`styles.css`
- **代码块**：启用复制按钮、显示边框

主题配置在 `_quarto.yml` 中修改。

## 评论系统

使用 [Giscus](https://giscus.app/) 实现评论功能：

- 基于 GitHub Discussions
- 需要用户登录 GitHub 账号才能评论
- 支持反应（reactions）
- 中文界面

配置位于 `_quarto.yml` 的 `comments.giscus` 部分。

## 许可证

博客内容采用 [CC-BY-SA 4.0](LICENSE) 许可证。

## 致谢

- [Quarto](https://quarto.org/) - 科学与技术发布系统
- [Bootswatch](https://bootswatch.com/) - Bootstrap 主题
- [Giscus](https://giscus.app/) - 评论系统
- [GitHub Pages](https://pages.github.com/) - 静态站点托管
