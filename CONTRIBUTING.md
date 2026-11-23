# 安妮播放器 Windows · 贡献与协作规范

## 职责边界

- 章鱼（`@Zhou1019-1`）负责 Windows 开发，并负责各平台仓库的代码审核、整理和发布把关。
- macOS、macOS Lite、iOS、Android 的功能由对应平台贡献者开发；不要把其他平台的实现任务派给章鱼。
- AI agent 是贡献者的执行助手，不是仓库所有者，不得自行审批自己的 PR 或发布正式版本。

## 平台仓库

- Windows：`Zhou1019-1/AnniePlayer-LXversion-Windows`
- macOS：`Zhou1019-1/AnniePlayer-LXversion-macOS`
- macOS Lite：`Zhou1019-1/AnniePlayer-LXversion-macOS-Lite`
- iOS：`Zhou1019-1/AnniePlayer-LXversion-IOS`
- Android：`Zhou1019-1/AnniePlayer-LXversion-Android`

## 分支与 PR

1. 从最新 `main` 创建 `feat/<主题>`、`fix/<问题>` 或 `chore/<事项>`。
2. 所有人和 AI agent 都通过 PR 提交；禁止直接推 main、强推、删除 main 或自行创建发布 tag。
3. 一个 PR 只做一类事项，不把功能、迁移、格式化和大批杂物混在一起。
4. 只添加本次相关文件，禁止无差别 `git add -A` / `git add .`。
5. PR 必须写清改动、真实测试、影响范围、已知限制和回滚方式；未执行的验证写「未执行」，不得编造。
6. 修改后运行 `node scripts/check-syntax.js`；涉及音频、下载、沙箱或引擎时，补充对应现有测试。
7. 由章鱼或授权平台负责人审核合并。执行 agent 不代替 owner 自我审批。

## QQ 联系与 GitHub 留痕

QQ 是主要沟通渠道。贡献者的 AI agent 需要章鱼协助时，发送以下完整信息：

```text
【平台/仓库】
【任务与 PR 链接】
【分支 / commit SHA】
【改动范围】
【已执行的测试及真实结果】
【Actions Run / Artifact / 安装包链接】
【SHA256（如有安装包）】
【需要章鱼审核、合并、配置 Secret 或发布的具体事项】
【已知限制与待确认问题】
```

代码差异、审核意见和验证结果应落在 PR；QQ 用于通知、协调和紧急联系。QQ 中形成的版本或发布决定，回填到对应 PR 或 Release 说明。

## 二进制与敏感信息

- 安装包、DMG、APK、签名证书、私钥和大二进制不进 Git 源码。
- CI 临时产物走 Actions Artifacts；经验证的安装包走 Release 资产，使用 ASCII 文件名并附 SHA256。
- 密码、Token、Cookie、证书和服务器信息不写进 Issue、PR、QQ 或代码；需要配置时只向章鱼说明 Secret 名称和用途。
