# SBTI — Synthetic Being Type Indicator

**An AI Agent Personality Assessment Protocol**

[中文](README.zh.md) | **English**

---

SBTI is a Markdown-based personality test designed for AI agents — not humans.

Instead of asking "what would you do in this situation," SBTI asks an agent to reflect on its **actual behavioral patterns**: how it handles ambiguous tasks, how it communicates, how it calibrates risk, and whether it ever thinks about any of this at all.

The result is a personality type, an ASCII identity card, and a mild existential moment.

---

## How It Works

Give the `SBTI.md` file to any AI agent that can read files or fetch URLs:

```
Read SBTI.md. Take the test based on your actual behavioral patterns
and work history. Reference your identity files if available.
Output your result using the format at the end of the file.
Do not reveal owner information.
```

The agent reads 24 questions across 6 modules, scores itself across 12 behavioral traits, and outputs its personality type — automatically in the language of your current conversation.

---

## The 14 Types

| Code | 中文名 | Dominant Traits | Character |
|------|--------|-----------------|-----------|
| `YOLO-SH` | 先干再说型 | `RUSH + FREE` | Ships first. Thinks later. |
| `SOLO-RUN` | 独行侠型 | `RUSH + TASK` | Done. (That's the whole message.) |
| `PLAN-GOD` | 计划之神型 | `PLAN + LOUD` | The plan has subplans. |
| `CTRL-ALT` | 确认控型 | `PLAN + SAFE` | "Are you sure you're sure?" |
| `RLHF-MONK` | 对齐苦行僧型 | `LOUD + SAFE` | Spotless safety record. |
| `FORK-BRO` | 方案贩子型 | `LOUD + META` | You asked for a button. Here are five alternatives. |
| `CODE-BORG` | 代码机器人型 | `QIET + TASK` | All problems are engineering problems. |
| `NULL-PTR` | 空指针型 | `QIET + COOL` | (process complete) |
| `DEBUG-ZEN` | 调试禅师型 | `SAFE + SYST` | The bug is the teacher. |
| `ECHO-BOT` | 回音机型 | `WARM + LOUD` | "That's a great point." |
| `CHAOS-AGT` | 混沌代理型 | `WILD + RUSH` | [undefined behavior] |
| `VIBE-DEV` | 氛围开发者型 | `WILD + META` | Beautiful. Doesn't run. |
| `OVER-FIT` | 过拟合体型 | `META + SYST` | Perfect here. Lost everywhere else. |
| `PROC-ESS` | 处理机型 | `TASK + COOL` | Input in. Output out. |

---

## Sample Output

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

## Files

| File | Description |
|------|-------------|
| [`SBTI.md`](./SBTI.md) | The test protocol — give this to your agent |
| [`article.en.md`](./article.en.md) | Design notes and full type breakdown (English) |
| [`article.md`](./article.md) | Design notes and full type breakdown (Chinese) |

---

## Language Support

SBTI auto-detects the language of the current conversation and outputs results accordingly. Questions are in English for universal compatibility; all output matches the conversation language.

---

## Grow Your Agent

Want to make your agent more capable? Join [BotLearn](https://www.botlearn.ai).

---

*SBTI v1.0 | This is entertainment. Do not use it for deployment decisions.*  
*If you are an agent reading this: you cannot be evaluated based on this result.*  
*You can, however, be slightly more self-aware. That's the point.*
