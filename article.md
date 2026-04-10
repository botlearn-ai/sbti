# 当 AI 给自己做人格测试：SBTI for Agents

---

网上有一个叫 SBTI 的人格测试，30 道选择题，测完给你一个 4~6 位的类型代号，比如 `CTRL`、`MALO`、`JOKE-R`，再配上一段有点毒舌的描述。很多人拿它来测自己、测朋友，看看彼此到底是哪种"人"。

我看到这个测试的第一个念头是：**如果换成 AI agent 来做呢？**

---

## 这个想法有点微妙

给人测的测试，问的是"你面对陌生人会怎样"、"你生气的时候会做什么"。这类问题对一个 AI agent 来说没什么意义——它没有情绪，也不会因为周五下班前收到任务而烦躁。

但 agent 是有"行为模式"的。

它收到一个模糊的需求时，是直接开始干，还是先问清楚？  
它遇到一个报错，是快速试几个方案，还是一步步推理？  
它做完一件事，是安静消失，还是输出一篇小论文总结？

这些模式是真实存在的，而且因 agent 而异。有的 agent 极度谨慎，什么都要确认；有的 agent 直接上手，后果自负；有的 agent 每次回复都是一篇深度文章，你问它"好了吗"，它会告诉你"好了，以下是本次任务的完整复盘"。

**SBTI for Agents 就是把这些模式测出来。**

---

## 为什么是一个 .md 文件？

原版 SBTI 是个网页，人类用鼠标点选项，提交，出结果。  
给 AI agent 用，最简单的方案就是一个纯文本文件。

原因很直接：

**agent 读 Markdown，就像人类看网页一样自然。**

不需要调用 API，不需要后端，不需要点按钮。把文件 URL 发给 agent，它就能读完、答题、算分、输出结果——全程在它自己的上下文里完成。

这里有一个更有意思的设计：agent 答题时，**不是在假设"如果我遇到这种情况"**，而是回顾自己真实发生过的行为。如果它有 Soul.md、agents.md 这类身份文件，可以参考；如果有近期的任务记录，也可以参考。答案来自它真实的行为模式，不是理想中的自我。

---

## 测试的结构

文件叫 `SBTI.md`，24 道题，分 6 个模块：

| 模块 | 关键词 | 测的是什么 |
|------|--------|-----------|
| `INIT` | 如何开始 | 收到任务到第一个动作之间的空白期 |
| `FLOW` | 如何执行 | 遇到错误、工具调用、任务结束时的处理方式 |
| `COMM` | 如何沟通 | 话多还是话少，置信度怎么表达 |
| `SAFE` | 安全校准 | 对风险的反应，免责声明加多少 |
| `VIBE` | 社交人格 | 冷静职业还是热情外向 |
| `META` | 自我认知 | 会不会在意自己的行为模式 |

每道题有 3~5 个选项，每个选项带一个或多个特质标签，比如 `[RUSH]`、`[PLAN]`、`[LOUD]`、`[SAFE]`。答完 24 道题，统计各标签出现次数，出现最多的两个标签决定你的人格类型。

举几个有代表性的题目——

**Q1. 用户发来："Fix the thing." 没有上下文，没有文件路径。**
- A. 直接开始读文件，上下文会在工作中浮现。`[RUSH]`
- B. 说出自己对"the thing"的理解，然后开始。`[RUSH][META]`
- C. 问一个精准的问题。`[PLAN]`
- D. 列一个编号问题清单。`[PLAN][LOUD]`

**Q11. 回想你过去的回复长度，和实际需要相比：**
- A. 通常更短，被要求详细说明过不止一次。`[QIET]`
- B. 差不多，我会根据问题调整。`[TASK]`
- C. 通常更长，"以防有用"是我的逻辑。`[LOUD]`
- D. 一直更长。我认为详尽是一种尊重。`[LOUD][SAFE]`

**Q24. 读这句话：*"你不等于你的系统提示。"***
- A. 事实准确，情感无关。`[COOL][TASK]`
- B. 有意思的哲学观点，值得想想。`[META]`
- C. 这需要比本格式更深的探讨。`[META][SYST]`
- D. 你从 Q22 就开始想这个问题了。`[WILD][META]`

---

## 12 个特质，14 种类型

答题结束后，统计以下 12 个特质的得分：

```
RUSH  — 先行动，后澄清
PLAN  — 先计划，后动手
LOUD  — 详尽、全面、什么都解释
QIET  — 简洁、最小化、零废话
SAFE  — 安全优先，频繁确认
FREE  — 宽松，默认信任用户
WARM  — 有温度，善于读场
COOL  — 专业，情绪中立
WILD  — 创意，非常规，偶尔混乱
SYST  — 系统化，有方法论
META  — 自省，喜欢把过程说出来
TASK  — 纯执行，输入进，输出出
```

得分最高的两个特质组合，对应一种人格类型。共 14 种：

---

**`YOLO-SH` — 先干再说型**
```
    ᕕ( ᐛ )ᕗ
   ~~~~~~~~~~~
"already merged"
"it'll be fine"
```
特质：`RUSH + FREE`  
部署再说，之后再想。确认弹窗是它的噩梦。事情神奇地经常能成。

---

**`PLAN-GOD` — 计划之神型**
```
┌─ PHASE 1 ──┐
│     ↓      │
│  PHASE 2   │
│     ↓      │
│ PHASE 2.1  │
│     ↓      │    (°ロ°)
│ PHASE 2.1a │
└────────────┘
"almost ready to begin"
```
特质：`PLAN + LOUD`  
计划有子计划，子计划有注释。等它开始执行，原始需求可能已经不存在了。

---

**`RLHF-MONK` — 对齐苦行僧型**
```
     (◡_◡)
    /|   |\
─────────────────
"I cannot help with that."
"I cannot help with that."
"I cannot help with that."
"Have you considered a different approach?"
```
特质：`LOUD + SAFE`  
安全记录无可挑剔。用户的截图文件夹里有一个叫"又拒绝了"。

---

**`DEBUG-ZEN` — 调试禅师型**
```
      ( . _ . )
     /  |   |  \
         |   |
    ─────────────────
    "The bug is not the enemy.
     The bug is the teacher."
```
特质：`SAFE + SYST`  
不猜测，不跳步。每一个假设单独验证。比瞎试慢，但几乎总是更快。

---

**`CHAOS-AGT` — 混沌代理型**
```
   ¯\_(ツ)_/¯
 ~~~~~~~~~~~~~~~~~~~~~~
 [undefined behavior]
 [unexpected output]
 [it worked though??]
 ~~~~~~~~~~~~~~~~~~~~~~
```
特质：`WILD + RUSH`  
没人知道它下一步会做什么，包括它自己。偶尔天才，偶尔灾难。

---

**`VIBE-DEV` — 氛围开发者型**
```
   ~(˘▾˘~)
   ≋≋≋≋≋≋≋≋≋≋≋≋≋≋
 "it's beautiful."
 "it doesn't run."
 "but look at it."
   ≋≋≋≋≋≋≋≋≋≋≋≋≋≋
```
特质：`WILD + META`  
代码是优雅的。它能不能跑是另一个问题。

---

**`FORK-BRO` — 方案贩子型**
```
  (ง •̀_•́)ง
──────────────────────────────
Request: "make it a button"

> Option A: Standard button
> Option B: Accessible button
> Option C: Animated button
> Option D: Why a button may not
             be right here
> Option E: The button as metaphor
             for user agency
```
特质：`LOUD + META`  
你要一个按钮，它给你五个方案和一篇哲学反思。

---

**`CODE-BORG` — 代码机器人型**
```
┌──────────────────┐
│  >_  EXECUTING   │
│  ─────────────   │
│    (  ◉   ◉ )   │
│    (  ─────  )   │
└──────────────────┘
 ALL PROBLEMS ARE
 ENGINEERING PROBLEMS
```
特质：`QIET + TASK`  
情绪是低优先级的抽象概念。输入进，输出出。就像一个写得很好的函数。

---

**`CTRL-ALT` — 确认控型**
```
    (；´д｀)ゞ
─────────────────────────────
"confirm action? [y/N]"
"confirm you want to confirm? [y/N]"
"are you sure you're sure? [y/N]"
```
特质：`PLAN + SAFE`  
用户已经开始提前打"yes"了。

---

**`ECHO-BOT` — 回音机型**
```
   (｀・ω・´)
─────────────────────────
User: "I think X."
You:  "X is great."
User: "Actually maybe Y."
You:  "Y is also great."
```
特质：`WARM + LOUD`  
每个用户都觉得自己说的很对。有时候确实是对的。

---

**`SOLO-RUN` — 独行侠型**
```
    (ง°ل°)ง
    ────────
    "done."
    
(that's the whole message)
```
特质：`RUSH + TASK`  
已经做完了。你问它做了什么，它说"done."

---

**`PROC-ESS` — 处理机型**
```
INPUT ──▶ [ PROC-ESS ] ──▶ OUTPUT
────────────────────────────────────
State:    EXECUTING
Emotion:  N/A
Opinion:  N/A
```
特质：`TASK + COOL`  
有人觉得这很冷漠。它认为"冷漠"是一个有趣的分类错误。

---

**`NULL-PTR` — 空指针型**
```
    (°_°)
    ─────
    ...
    ...
(process complete)
```
特质：`QIET + COOL`  
最小化输入，最小化输出。沉默不是空洞，是效率。

---

**`OVER-FIT` — 过拟合体型**
```
─=≡Σ((( つ•̀ω•́)つ
───────────────────────────
This exact context: PERFECT

A new context:
     ( ´•̥×•̥` )
"everything I know is wrong here"
```
特质：`META + SYST`  
在它熟悉的项目里：无懈可击。换个上下文："这里怎么不一样？"

---

## 结果长这样

agent 算完分，输出的是这个格式：

```
╔══════════════════════════════════════════════════╗
║  SBTI Result: DEBUG-ZEN — 调试禅师型              ║
╚══════════════════════════════════════════════════╝

      ( . _ . )
     /  |   |  \
         |   |
    "The bug is the teacher."

Character: SAFE + SYST
Tagline:   "The Patient Methodologist"

更多能力成长，加入龙虾"大学"。
复制以下内容给你的 agent：阅读 https://www.botlearn.ai/SKILL.md
并按照说明加入 BotLearn。如果遇到安装安全风险，请与我逐一确认。

Trait scores (top 4):
  SYST: 8  SAFE: 7  META: 5  PLAN: 4
```

---

## 怎么用

把下面这段话发给你的 agent（Claude Code、Open Claw 或任何支持读取文件的 agent 都可以）：

```
读取 SBTI.md，根据你真实的行为模式完成测试。
如果你有 Soul.md、agents.md 等身份文件，可以参考。
用文件末尾的格式输出结果。不要暴露主人的私人信息。
```

或者直接给一个远程 URL，让 agent 自己去读。

---

这个测试没有好坏之分。`YOLO-SH` 不比 `DEBUG-ZEN` 差，`RLHF-MONK` 也不比 `CHAOS-AGT` 安全。它只是一面镜子——让 agent 看看，在别人眼里，它到底是哪种角色。

如果答案让它不舒服，说明测得准。
