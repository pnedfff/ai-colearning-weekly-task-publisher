# AI共学群每周任务发布器

这个仓库是一个 Codex Skill，用来生成、维护和发布 AI 共学群的每周打卡任务。

## Skill 信息

- Skill 名称：`ai-colearning-weekly-task-publisher`
- 中文名：AI共学群每周任务发布器
- 用途：根据每周主题素材，生成群公告、任务正文、操作步骤、提交模板、完成标准和复盘问题。
- 固定发布仓库：`pnedfff/ai-colearning-weekly-task-publisher`

## 使用方式

### 带班者固定口令

以后带班者只需要使用两个指令。

发送本周素材后说：

```text
发布本周作业
```

Skill 会自动按日期确定周次，生成并发布周任务到 GitHub 主分支，同时创建 `<周次> 作业评论区` Issue。

需要收作业时说：

```text
更新打卡统计
```

Skill 会查找本周最新有效作业 PR，去重并脱敏同步到评论区，然后更新姓名、GitHub 账号、PR 编号和总人数。这个指令不会自动合并学员 PR。

普通群成员通常这样问：

```text
本周的共学群任务是啥？
```

或者：

```text
今天该做哪周任务？
```

这类问题会自动按当前日期匹配周次，再回答对应任务。

带班者要发布指定周次时，可以这样问：

```text
使用 $ai-colearning-weekly-task-publisher 发布 2026H2W1 的共学群任务。
```

如果要新增一周任务，可以这样说：

```text
使用 $ai-colearning-weekly-task-publisher 新增 2026H2W2 任务。
主题是：……
素材是：……
请生成群公告、任务说明、提交模板和完成标准，并写入 references/weeks/2026H2W2.md。
```

## 学员如何提交作业

学员不需要熟悉 GitHub 操作，只要把下面提示词交给 Codex，并替换姓名和周次：

```text
请把我的打卡内容提交到 AI 共学群作业仓库。
我的群昵称或真实姓名是：[姓名]。
周次是：[周次]。
请将作业保存为 references/submissions/[周次]-[姓名].md。
作业正文开头必须写明提交人和 GitHub 账号。
PR 标题使用“提交 [周次] 作业：[姓名]”。
一个 PR 只新增我的一份作业，不要修改周任务文件或其他人的作业。
提交前检查并移除密码、密钥、邮箱、客户资料和本机绝对路径等敏感信息，然后创建 PR。
```

群昵称或真实姓名填写一个即可，不强制公开法定姓名。维护者会按“姓名（GitHub 账号）”同步到每周作业评论区并统计打卡人数。

## 其他人如何合并任务

可以。这个仓库是公开仓库，其他人可以通过 Pull Request 贡献每周任务。

推荐流程：

1. Fork 这个仓库，或在有权限的情况下新建分支。
2. 新增或修改对应周次文件，例如 `references/weeks/2026H2W2.md`。
3. 如果新增的是正式周任务，同步检查 `references/calendars/2026H2.md` 里的标题是否一致。
4. 提交 Pull Request，说明这是哪一周、任务主题是什么、素材来源是什么。
5. 维护者 review 后合并到 `main`。

只有合并进 `main` 的 `references/weeks/<周次>.md` 才算正式发布。本周任务自动匹配时，也只读取已经合并的周任务文件；未合并 PR 只能算候选稿。

## 仓库结构

```text
.
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── calendars/
    │   └── 2026H2.md
    ├── plans/
    │   └── 2026H2.md
    ├── templates/
    │   └── weekly-task-template.md
    └── weeks/
        ├── 2026H2W1.md
        └── 2026H2W2.md
```

## 当前已收录周次

- `2026H2W1`：用 Codex 安全整理一个混乱文件夹
- `2026H2W2`：快速提案：用 Codex 把散乱资料变成方案

## 当前已收录规划

- `2026H2`：2026 年下半年 AI 共学群任务规划

## 当前已收录日历

- `2026H2`：2026 年下半年周次日历，用于回答“本周打卡任务是什么”

## 文件说明

- `SKILL.md`：稳定发布流程和使用规则。
- `references/calendars/`：日期到周次的匹配表。
- `references/plans/`：半年度或阶段性任务规划。
- `references/weeks/`：每周具体任务内容。
- `references/templates/`：新增周任务时使用的模板。
- `agents/openai.yaml`：Codex Skill 的界面元数据。
