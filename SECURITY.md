# 安全策略

## 报告问题

本账号下的私有仓库涉及个人 AI 系统数据、公司项目配置。如发现密钥泄露、权限配置错误、依赖供应链风险，**不要开公开 Issue**，直接私下联系账号所有者。

## 严禁提交的内容

| 类型 | 示例 |
|---|---|
| 凭据 | API Key、Token、SSH 私钥、`.credentials`、`.runner` |
| 环境文件 | `.env`、`.env.local`、`*.pem`、`*.key` |
| 运行态数据 | 数据库转储、会话记录、缓存 |
| 第三方私密内容 | 客户数据、未公开的合作方资料 |

## Actions 供应链

- 只允许 `actions/*`、`github/*` 和 Marketplace 已验证发布者的 action
- 第三方 action 必须锁定到具体版本 tag 或 commit SHA，不用 `@master`
- 需要 `write` 权限的 workflow 必须单独说明理由

## 泄露后的处置顺序

1. **先撤密钥**（在服务商侧作废，不是先删仓库）
2. 再清理仓库历史（`git filter-repo` 或联系 GitHub 支持）
3. 最后记录事件到 Issue（私有仓库）
