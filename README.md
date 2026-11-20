# 一拳爆装（v1.0）

纯前端 HTML5 点击放置游戏；无需构建步骤、服务器或后端。仓库根目录包含 `index.html`、空的 `.nojekyll` 和本说明文件。

## 本地运行与操作

- 直接打开 `index.html` 即可游玩；战斗区任意位置按下即可攻击，连续点击 10 次触发 5 秒暴怒。
- 使用底部按钮升级攻击、暴击与自动攻击。自动攻击解锁后会持续造成伤害；每 5 分钟出现一次限时 Boss。
- 页面每 10 秒自动保存到 IndexedDB。离线超过 30 秒且已有自动 DPS 时会计算离线金币，点击“收下”入账。
- 右上角“导出/导入”用于 JSON 备份与跨设备恢复；导入会要求确认。
- `idb` 通过 CDN 加载；若 CDN 不可用，页面尝试使用浏览器原生 IndexedDB。离线运行时仍可游玩，但首次打开需允许浏览器存储。

## GitHub Pages 部署

1. 在 GitHub 创建 **Public** 仓库。
2. 将 `index.html`、空文件 `.nojekyll`、`README.md` 放在仓库根目录并推送至 `main` 分支。
3. 打开仓库 **Settings → Pages**，选择 **Deploy from a branch**，分支选 `main`，目录选 `/(root)`，保存。
4. 等待 Pages 部署完成，访问 `https://<用户名>.github.io/<仓库名>/`。
5. 若遇到 404 或白屏，检查 `.nojekyll` 是否位于根目录且为空、文件名大小写是否一致、页面资源路径是否为相对路径。

无需 `package.json`、构建工具或 `node_modules`。`favicon.ico` 为可选项，本版本未引用外部游戏素材。
## 触感反馈（Haptics）

战斗区每次点击都会请求轻触反馈；暴击与暴怒使用不同的反馈模式。支持 `navigator.vibrate()` 的浏览器会直接调用该 API。**iOS Safari 不支持 Vibration API**，因此 GitHub Pages 网页本身不能让 iPhone 马达震动；要在 iOS 上获得真实触感，需要用注册了 `hapticFeedback` 消息处理器的原生 `WKWebView` 宿主打开页面。页面会向该桥发送 `tap`、`rage` 或 `critical` 字符串。
