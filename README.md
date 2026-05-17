# 具身大脑 Wiki

[![Deploy to GitHub Pages](https://github.com/wikieden/embodied-brain-wiki/actions/workflows/pages.yml/badge.svg)](https://github.com/wikieden/embodied-brain-wiki/actions/workflows/pages.yml)

> 从反射型机器人到智能体的全景知识库

在线访问：https://wikieden.github.io/embodied-brain-wiki/

---

## 目录

- [自定义域名](#自定义域名)
- [访问统计](#访问统计)
- [本地预览](#本地预览)
- [内容贡献](#内容贡献)

---

## 自定义域名

如需绑定自己的域名，请执行以下步骤：

1. 将 `docs/CNAME.example` 重命名为 `docs/CNAME`
2. 编辑 `docs/CNAME`，只保留域名（无注释）：
   ```
   wiki.yourdomain.com
   ```
3. 编辑 `mkdocs.yml`，更新 `site_url`：
   ```yaml
   site_url: https://wiki.yourdomain.com
   ```
4. 在 DNS 提供商处添加记录：
   - **子域名**（推荐）: CNAME `wiki.yourdomain.com` → `wikieden.github.io`
   - **顶级域名**: A 记录指向 `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
5. 提交更改，自动部署：
   ```bash
   git add docs/CNAME mkdocs.yml
   git commit -m "chore: 添加自定义域名"
   git push
   ```
6. 在 GitHub 仓库设置中确认 `Settings > Pages > Custom domain` 已启用并通过验证。

---

## 访问统计

本站点内置了 Google Analytics 4 统计，但需要你配置自己的 GA4 测量 ID。

1. 前往 [Google Analytics](https://analytics.google.com/) 创建新媒体资源，获取测量 ID（格式：`G-XXXXXXXXXX`）
2. 编辑 `mkdocs.yml`，更新以下字段：
   ```yaml
   extra:
     analytics:
       provider: google
       property: G-XXXXXXXXXX  # 替换为你的实际 ID
   ```
3. 提交更改：
   ```bash
   git add mkdocs.yml
   git commit -m "chore: 更新 GA4 测量 ID"
   git push
   ```

---

## 本地预览

```bash
# 安装依赖
uv pip install mkdocs-material mkdocs-minify-plugin

# 启动本地服务
mkdocs serve

# 构建
mkdocs build
```

---

## 内容贡献

原始知识库位于独立的 Obsidian Vault，本仓库只是静态网站构建。

如需更新内容，请直接编辑 `docs/` 目录下的 Markdown 文件，提交后 GitHub Actions 会自动部署。

---

© 2026 wikieden | 具身大脑知识库
