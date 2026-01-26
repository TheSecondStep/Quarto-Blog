# CLAUDE.md

本文件为 Claude Code (claude.ai/code) 在此代码库中工作时提供指导。

## 项目概述

这是一个基于 Quarto 的技术博客，托管于 GitHub Pages。博客文章以 Jupyter notebooks (`.ipynb`) 或 Quarto markdown (`.qmd`) 文件编写。内容为中文，启用了 Giscus 评论功能。

## 常用命令

### 开发环境
```bash
# 安装/同步 Python 依赖（使用 uv，Python 3.13）
uv sync

# 本地预览服务（支持实时刷新）
quarto preview

# 渲染/构建网站
quarto render
```

### 部署
- 推送到 `main` 分支会自动触发 GitHub Actions 部署到 `gh-pages`
- 手动发布：`quarto publish gh-pages`

## 项目结构

- `posts/` - 博客文章，每篇文章存放在独立子目录中，包含 `index.ipynb` 或 `index.qmd`
- `posts/_metadata.yml` - 文章共享配置（当前设置：`freeze: true` 冻结计算输出，`title-block-banner: true` 启用标题横幅）
- `index.qmd` - 首页，展示所有文章列表（按日期降序排列，启用分类）
- `_quarto.yml` - Quarto 主配置文件（主题：flatly + brand 自定义，Giscus 评论配置为 `TheSecondStep/Quarto-Blog`）
- `.github/workflows/quarto_publish.yml` - GitHub Actions CI/CD 工作流

## 内容架构

**文章**：每篇博客文章是 `posts/` 下的子目录，包含 `index.ipynb` 或 `index.qmd` 文件。首页列表会自动发现并展示这些文章。

**Freeze 模式**：计算输出被冻结（`posts/_metadata.yml` 中设置 `freeze: true`）以确保构建可复现。编辑包含代码的 notebook 时，可能需要临时禁用 freeze 或手动重新渲染单元格。

**分类**：通过 `index.qmd` 中的 `categories: true` 在列表页启用分类显示。

## 主题与样式

- 基础主题：`flatly` (Bootswatch)
- 自定义主题层：`brand`
- 自定义 CSS：`styles.css`
- 代码块：启用复制功能、启用边框
