# AgentJam GitHub Pages 上传说明

这是用于 TRAE AI 创造力大赛展示的 GitHub Pages 版本。

## 文件结构

- `index.html`：页面入口文件，GitHub Pages 会默认打开它。
- `_shared/fonts/`：页面使用的本地字体资源，请和 `index.html` 一起上传。
- `.nojekyll`：告诉 GitHub Pages 不要用 Jekyll 处理下划线目录，避免 `_shared` 被忽略。

## 上传方式

1. 新建一个 GitHub 仓库，例如 `agentjam-showcase`。
2. 把本文件夹里的所有内容上传到仓库根目录。
3. 在仓库页面进入 `Settings` → `Pages`。
4. `Build and deployment` 选择 `Deploy from a branch`。
5. Branch 选择 `main`，目录选择 `/root`，保存。
6. 等待 1-3 分钟，GitHub 会生成一个公开链接，通常格式为：

`https://你的用户名.github.io/agentjam-showcase/`

把这个 `https://...` 链接放到 TRAE AI 创造力大赛帖子里，别人就可以打开。
