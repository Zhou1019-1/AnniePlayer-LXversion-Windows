# 安全与敏感信息规范

## 禁止入库或公开传输

不得提交或在 Issue、PR、QQ 中明文发送：GitHub Token、服务器密码、私钥、签名证书、Apple/Android 凭据、QQ Cookie、用户账号数据及含秘密的配置文件。

## Secrets 管理

- 发布凭据由 `@Zhou1019-1` 直接配置到 GitHub Secrets 或 `release` Environment。
- 贡献者的 AI agent 只提供 Secret 名称、用途和所需权限，不接收秘密原文。
- PR CI 不读取发布 Secret，默认使用只读 token；不要通过日志、Artifact 或 echo 输出秘密。
- 发现秘密已进入 Git 历史时，立即通知 owner，先轮换/吊销，再清理历史；仅删除文件不算修复。

## 漏洞报告

不要在公开 Issue 中披露可复现的利用细节、用户数据或服务器凭据。通过项目既有的私密联系渠道通知 owner，并在 GitHub 中只保留不含敏感信息的修复记录。

## 大二进制与供应链

大二进制不直接进 Git；运行时依赖使用固定 URL、版本和 SHA256 校验。发布包必须能从公开源码和仓内脚本复现，禁止上传来源不明或与 tag 不一致的附件。
