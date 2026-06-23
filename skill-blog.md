# 创建博客文章流程

## 1. 新建文章

在 `src/content/blog/` 下创建 `.md` 文件，文件名作为 URL slug。

## 2. Frontmatter 格式

```markdown
---
title: "文章标题"
date: 2026-06-23
description: "简短描述，会显示在文章卡片上"
tags: ["标签1", "标签2"]
cover: https://图片直链.jpg    # 可选，卡片缩略图（16:9横图最佳）
---
```

注意：
- `cover` 图片要使用**直链**（不要用 `/thumb/` 缩略图链接）
- 标签显示在卡片上，最多显示 3 个
- 日期格式 `YYYY-MM-DD`

## 3. 嵌入视频

文章正文直接用 iframe：

```html
<iframe src="https://视频链接" width="100%" height="400" frameborder="0" allowfullscreen></iframe>
```

宽度用 `100%` 自适应，高度设 `400` 左右。

## 4. 本地预览

```powershell
npm run dev
```

然后浏览器打开 `http://localhost:4321/blog/文件名`

## 5. 构建并部署到 Cloudflare

```powershell
npm run build
npx wrangler pages deploy dist/client --project-name capyblog --branch main
```

## 6. 提交到 GitHub

```powershell
git add -A
git commit -m "feat: add new article"
git push
```

GitHub Actions 会自动构建部署到 `https://capyblog-98d.pages.dev`。
