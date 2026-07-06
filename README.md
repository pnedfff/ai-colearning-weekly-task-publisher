# AI共学群每周任务发布器

这个仓库是一个 Codex Skill，用来生成、维护和发布 AI 共学群的每周打卡任务。

## Skill 信息

- Skill 名称：`ai-colearning-weekly-task-publisher`
- 中文名：AI共学群每周任务发布器
- 用途：根据每周主题素材，生成群公告、任务正文、操作步骤、提交模板、完成标准和复盘问题。

## 使用方式

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
        └── 2026H2W1.md
```

## 当前已收录周次

- `2026H2W1`：用 Codex 安全整理一个混乱文件夹

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
