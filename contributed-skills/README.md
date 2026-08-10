# 贡献的 Skill（社区沉淀）

本目录收录学员 / 维护者在使用 AI 共学群过程中沉淀出的可复用 Skill。每个子目录是一个独立 Skill，含 SKILL.md。

- `skill-install-security-auditor`：从 URL / 路径安装 Skill 时先做安全审计（危险模式扫描 + 版本比对 + P0/P1/P2 定级）再落地。
- `conversation-to-skill-candidate-detector`：回顾对话、提取 5 轮以上重复话题、四标准评估、提问确认（不擅自创建）。
- `github-submit-via-gh-cli`：当 GitHub MCP 连接器无写权限(403) 或被沙箱代理拦截 git clone 时，改用 gh CLI + gh api Contents API 建分支 / 写文件 / 开 PR。

用法：把对应子目录整体复制到你的 `~/.workbuddy/skills/` 即可启用。
