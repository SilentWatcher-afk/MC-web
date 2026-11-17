# 方块世界（MC-web）

一个原创的浏览器体素沙盒模板，使用 Three.js 和原生 JavaScript。它借鉴方块建造游戏的通用玩法与像素风格，不是 Minecraft 1.21.1，也不包含 Minecraft / Eaglercraft 的专有游戏代码或素材。Eaglercraft-Extras 是独立的参考项目，不是本项目的依赖。

## 当前模板包含

- Three.js 第一人称 3D 世界、种子化地形与简单树木
- WASD 移动、空格跳跃、Shift 疾跑、方块碰撞
- 挖掘、收集、放置方块；快捷栏和背包
- 简单的快速合成菜单
- 昼夜视觉循环、坐标与 FPS 显示
- `localStorage` 世界/背包/玩家位置存档和新世界重置
- 暂停菜单、视野距离/灵敏度/FOV 设置
- 移动端触控按钮初始界面
- GitHub Actions 静态站点部署工作流（Pages）

这是一个可扩展的原型，不包含区块流式加载、原版生物、完整合成配方、多人联机、完整 1.21.1 内容或原版美术资源。

## 本地运行

需要支持 WebGL 的现代浏览器，以及 Python 3 或其他静态 HTTP 服务器。不要直接用 `file://` 打开 ES module 页面。

```bash
git clone https://github.com/SilentWatcher-afk/MC-web.git
cd MC-web
python3 -m http.server 8000
```

打开 <http://localhost:8000>，点击“进入世界”。Three.js 由 jsDelivr CDN 加载，因此运行时需要网络连接。

### 控制

| 输入 | 操作 |
| --- | --- |
| WASD | 移动 |
| 空格 | 跳跃 |
| Shift | 疾跑 |
| 鼠标移动 | 转动视角 |
| 鼠标左键 | 挖掘并收集方块 |
| 鼠标右键 | 放置选中方块 |
| 1–8 / 滚轮 | 切换快捷栏 |
| E | 打开物品栏 |
| Esc | 暂停/释放鼠标 |

存档保存在当前浏览器和站点来源的 `localStorage` 中。清除浏览器站点数据会删除存档；不同设备/浏览器间不会同步。

## 部署到 GitHub Pages

仓库包含 `.github/workflows/deploy.yml`。工作流会在 `main` 分支有推送或手动触发时发布仓库根目录静态文件。

1. 在 GitHub 仓库打开 **Settings → Pages**。
2. 在 **Build and deployment → Source** 选择 **GitHub Actions**。
3. 推送到 `main`，或在 **Actions → Deploy static game to GitHub Pages → Run workflow** 手动运行。
4. 首次部署后，Pages 会显示公开站点地址，通常形如 `https://<账户>.github.io/MC-web/`。

若 Actions 报权限错误，检查 **Settings → Actions → General → Workflow permissions**，允许 Actions 执行部署所需权限；确认 Pages 已启用并允许该环境部署。工作流需要 `pages: write` 和 `id-token: write`。

## 运行时与许可

- Three.js 0.160.0 从 CDN 加载。需要离线运行时，请自行下载 Three.js 并核对其许可证和版本。
- 本项目采用仓库现有 Apache-2.0 许可证。第三方依赖仍遵循各自许可证。
- 请勿在没有授权的情况下添加或再分发 Minecraft 原版客户端代码、纹理、音效、字体或商标素材。
