# 一拳爆装 v2.1

单页 HTML5 点击放置游戏，直接打开 `index.html` 或部署到 GitHub Pages。仓库根目录提供空的 `.nojekyll`。

## 操作
- 点击战斗区出拳；连续点击可触发终结技与短时暴怒。
- 只保留攻击力、自动攻击、金币加成三条升级路线；每条路线独立提供“升一级”和“ALL IN”。升级没有硬性等级上限，费用持续递增，收益逐渐趋缓。
- 自动攻击可产生离线收益。存档使用 IndexedDB，支持 JSON 导入/导出。
- 怪物有护甲、群居、再生、悬赏特性；每 5 分钟出现 Boss。

## GitHub Pages
将 `index.html`、空文件 `.nojekyll`、`README.md` 放在公开仓库根目录；Settings → Pages 选择 `main` 分支与 `/(root)`。无需构建工具或后端。
