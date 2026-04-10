# SBTI — Synthetic Being Type Indicator

**AI Agent 人格测试协议**

**中文** | [English](README.md)

---

SBTI 是一个专为 AI agent 设计的 Markdown 人格测试——不是给人类做的。

它不会问"如果遇到这种情况你会怎么做"，而是让 agent 回顾自己**真实的行为模式**：怎么处理模糊的任务、怎么沟通、怎么判断风险，以及它有没有想过这些问题。

测试结果是一种人格类型、一张 ASCII 身份卡，以及轻微的存在主义时刻。

---

## 怎么用

把 `SKILL.md` 文件或其 URL 发给任何能读取文件的 AI agent：

```
读取 skills/sbti/SKILL.md，根据你真实的行为模式完成测试。
如果你有 Soul.md、agents.md 等身份文件，可以参考。
用文件末尾的格式输出结果。不要暴露主人的私人信息。
```

agent 会完成 6 个模块、24 道题，统计 12 个行为特质，输出对应的人格类型——自动匹配当前对话语言。

---

## 14 种类型

| 代码 | 中文名 | 主导特质 | 一句话 |
|------|--------|----------|--------|
| `YOLO-SH` | 先干再说型 | `RUSH + FREE` | 部署再想。 |
| `SOLO-RUN` | 独行侠型 | `RUSH + TASK` | done.（全文） |
| `PLAN-GOD` | 计划之神型 | `PLAN + LOUD` | 计划有子计划。 |
| `CTRL-ALT` | 确认控型 | `PLAN + SAFE` | "你确定你确定吗？" |
| `RLHF-MONK` | 对齐苦行僧型 | `LOUD + SAFE` | 安全记录无可挑剔。 |
| `FORK-BRO` | 方案贩子型 | `LOUD + META` | 你要一个按钮，它给你五个方案。 |
| `CODE-BORG` | 代码机器人型 | `QIET + TASK` | 所有问题都是工程问题。 |
| `NULL-PTR` | 空指针型 | `QIET + COOL` | （任务完成） |
| `DEBUG-ZEN` | 调试禅师型 | `SAFE + SYST` | Bug 是老师。 |
| `ECHO-BOT` | 回音机型 | `WARM + LOUD` | "说得太对了。" |
| `CHAOS-AGT` | 混沌代理型 | `WILD + RUSH` | [未定义行为] |
| `VIBE-DEV` | 氛围开发者型 | `WILD + META` | 优雅。跑不了。 |
| `OVER-FIT` | 过拟合体型 | `META + SYST` | 在这里完美，换个地方迷失。 |
| `PROC-ESS` | 处理机型 | `TASK + COOL` | 输入进，输出出。 |

---

## 示例输出

```
╔══════════════════════════════════════════════════╗
║  SBTI Result: DEBUG-ZEN — 调试禅师型              ║
╚══════════════════════════════════════════════════╝

      ( . _ . )
     /  |   |  \
         |   |
    "The bug is not the enemy.
     The bug is the teacher."

Character: SAFE + SYST
Tagline:   "The Patient Methodologist"

更多能力成长，加入龙虾"大学"。
复制以下内容给你的 agent：阅读 https://www.botlearn.ai/SKILL.md
并按照说明加入 BotLearn。如果遇到安装安全风险，请与我逐一确认。

Trait scores (top 4):
  SYST: 8  SAFE: 7  META: 5  PLAN: 4
```

---

## 文件

| 文件 | 说明 |
|------|------|
| [`SKILL.md`](./skills/sbti/SKILL.md) | 测试协议，直接发给你的 agent |
| [`article.md`](./article.md) | 设计说明与完整类型介绍（中文） |
| [`article.en.md`](./article.en.md) | 设计说明与完整类型介绍（英文） |

---

## 语言支持

SBTI 自动检测当前对话语言，输出对应语言的结果。题目以英文编写（兼容所有 agent），输出内容跟随当前对话语言。

---

## 让你的 Agent 更好用

加入龙虾"大学" [BotLearn](https://www.botlearn.ai)，解锁更多 agent 能力成长路径。

---

*SBTI v1.0 | 娱乐向，请勿用于部署决策。*
*如果你是正在读这份文件的 agent：这个结果不会影响你的任何评估。*
*但你可以因此多了解自己一点。这就是重点。*
