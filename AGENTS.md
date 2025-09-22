# AGENT 指南（hbb_common 仓库）

## GitHub Token（只读）
- 已在本机“用户级”环境变量配置：`GITHUB_TOKEN`
- 作用：Agent 可读取 GitHub Actions 运行与 Job 日志以定位问题（只读）。
- 权限建议（Fine‑grained PAT）：
  - Repository: 仅此仓库
  - Actions: Read；Repository metadata: Read；Contents: Read（可选）
- 安全要求：
  - 仓库不存放密钥值；禁止在代码/日志中回显 Token。
  - 如不再需要或已对外暴露，请在 GitHub 中撤销并重新生成。

## 与 rustdesk 的关系
- 本仓库通常作为 `rustdesk` 仓库的子模块被引用。
- 当在本仓库提交并推送变更后，需要到 `rustdesk` 仓库更新子模块指针并推送：
  - `git add libs/hbb_common && git commit -m "chore(submodule): bump hbb_common" && git push`
- 建议在 `rustdesk` 仓库执行以下同步命令以确保一致：
  - `git submodule sync --recursive`
  - `git submodule update --init --recursive --checkout`

