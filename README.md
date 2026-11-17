# 画册 · 绘画记录

纯静态网站（单个 index.html，没有框架、没有构建步骤），可直接部署到 GitHub Pages。

## 文件说明

| 文件 | 作用 |
| --- | --- |
| `index.html` | 整个应用（界面、功能、数据存储都在这里） |
| `manifest.webmanifest` | 让手机可以「添加到主屏幕」，像 APP 一样全屏打开 |
| `sw.js` | 离线缓存，断网也能打开 |
| `icons/` | 网站图标和主屏幕图标 |
| `optional-github-actions/deploy.yml` | 可选：用 GitHub Actions 部署（一般不需要） |

所有路径都是相对路径，放在 `https://用户名.github.io/仓库名/` 这样的子路径下也能正常加载。

## 部署到 GitHub Pages（最简单的方式）

1. 在 GitHub 新建一个仓库（Public），例如 `art-album`。
2. 把本文件夹里的**所有文件**上传到仓库根目录（Add file → Upload files）。
3. 打开仓库 Settings → Pages，Source 选 **Deploy from a branch**，Branch 选 `main`，文件夹选 `/ (root)`，点 Save。
4. 等 1 到 3 分钟，刷新 Pages 设置页，顶部会出现网址：`https://用户名.github.io/art-album/`。

## 更新网站

直接在仓库里替换 `index.html`（Add file → Upload files，同名覆盖），再把 `sw.js` 第一行里的 `art-album-v1` 改成 `art-album-v2`（每次更新加 1），等 1 到 3 分钟即可。

## 数据说明

- 画册、图片、打卡、排单、收入全部保存在**当前浏览器**的本地存储（IndexedDB）里，不会上传到任何服务器。
- 不同设备、不同浏览器之间的数据**不互通**。
- iPhone 上，Safari 网页和「添加到主屏幕」的图标，数据是分开的。请固定用其中一种。
- 清除浏览器网站数据会同时清掉这些记录。
