# 协作约定

适用于 skysze-polyu 账号下所有仓库（各仓库有自己的 `CONTRIBUTING.md` 时以仓库内为准）。

## 四步流程

提请求 → 推 → 审 → 合，缺一步都不算完。

1. **提请求**：开 Issue，用 `缺陷报告` / `需求请求` / `杂务` 三个模板之一。必须写「什么算完成」。
2. **推**：从 Issue 拉分支，不要直改 main。
   - `feat/<issue号>-<简述>`
   - `fix/<issue号>-<简述>`
   - `chore/<简述>`
   - `docs/<简述>`
3. **审**：CI 检查必须全绿；对照 PR 模板的自查清单逐条确认。
4. **合**：Squash merge，自动删源分支。main 保持单线历史。

## 单人账号的审查原则

GitHub 不允许自己批自己的 PR，所以本账号**不设强制人工 approve**。替代做法：

- PR 必须存在（这是最低门槛，保证有记录、有 diff、可回滚）
- 必须通过状态检查
- 必须逐条勾完 PR 自查清单
- 涉及 Actions / 权限 / 密钥的 PR，额外让 Copilot 审一遍再合

## 分支保护

`main` 分支规则由管理员在 Settings → Rules 里设置，禁止直推、禁止强推、禁止删除。机器人如果需要直推，必须走 bypass 白名单，且要有明确理由记录在 Issue 里。

## Actions 使用原则

**默认关闭，按需开启。** 新仓库建好后 Actions 是关的，确实需要 CI 才打开，并且：

- 触发条件必须限定分支和路径
- 必须写 `concurrency` 防止重复排队
- `permissions` 只给必需的最小权限
- 公开仓库一律不开任何 workflow

## 密钥

一律放仓库或组织的 Secrets / Environments，绝不进仓库。提交前用 `git diff --cached` 扫一眼。
