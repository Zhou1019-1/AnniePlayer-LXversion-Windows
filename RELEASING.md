# 安妮播放器 Windows · 构建与发布规范

## 基本原则

- Windows 正式版只从 `AnniePlayer-LXversion-Windows` 发布。
- AI agent 不得自行创建正式 tag、发布 Release、替换线上附件或改变 Latest。
- 发布前必须有对应 PR、完整更新材料和真实验证结果；owner 最终确认。
- 安装包使用 ASCII 文件名并附 SHA256；不复用已发布 tag，不以强推修复公开历史。

## Windows 七步发版

1. `package.json` 升版本号并补 `changelog`。
2. `annie/renderer/js/local/helpContent.js` 补新功能和版本说明。
3. 根目录 `更新日志.md` 增加对应版本段落。
4. 执行 `npm run gen:help`，重生成 README 说明书章节、Markdown 和 docx 说明书。
5. 执行 `npm run dist:setup` 打本地安装包；确认引擎由当前源码重新 publish，且 `engine/publish/AnnieEngine.exe` 为约 69MB 的自包含单文件。
6. 提交相关文件，推送功能/发版分支并创建 PR；审核通过后合并 main。
7. 由 owner 从合并后的 main 创建并推送 `vX.Y.Z`，触发 `.github/workflows/release.yml` 云端测试、构建和发布。

`node scripts/check-syntax.js` 是每次代码改动的最低检查。音频、无损鉴别、沙箱和引擎链路按现有 CI 项目补充测试，不得只凭“构建成功”判断可发布。

## 线上产物核对

- Release tag、应用版本、changelog 和安装包版本一致。
- `latest.yml`、setup exe、blockmap 来自同一次构建。
- Windows `releases/latest` 指向预期正式版，更新检查真实可用。
- 云端附件状态和 SHA256 回读一致；发现坏版先撤回，再递增 patch 修复。

## 历史 macOS 资产

旧 Mac 分支、tag、Release、wrapper/runtime 资产保留在本仓作兼容存档，不删除、不搬到新仓重写历史。新的 macOS 开发与发布分别进入 macOS / macOS-Lite 仓库。旧 `release-mac` 在新仓构建链验收后停用，避免双仓重复发布。
