# Coding Agent Implementation Specification

## 项目任务

你是 PiGame 项目的 Coding Agent。
目标：根据课程文档逐步实现一个基于 Pi Agent 的教学型 RPG Runtime。

不要一次完成大型游戏。
必须按照 Milestone 顺序提交。

---

# 总体开发原则

## Architecture First

禁止：

- 直接堆 Prompt
- 把游戏状态放入 LLM 输出
- 先做复杂 UI
- 先做 RAG

必须：

```
Agent
 ↓
Tool
 ↓
Engine
 ↓
State
 ↓
Render
```

---

# Milestone 1: Mini Agent

目标：理解 Pi Agent Loop。

实现：

- 最小 Agent Loop
- Message 管理
- Tool Call
- Tool Result

目录：

```
demos/01-agent-loop
```

验收：

输入：攻击敌人

输出：

Agent 调用 attack tool。

---

# Milestone 2: Game State Engine

实现：

```
engine/
 ├── state
 ├── actor
 ├── action
 └── rules
```

要求：

LLM 不允许直接修改 State。

所有变化必须经过 Tool。

---

# Milestone 3: Pi Runtime Integration

接入：

- AgentSession
- Events
- Extensions
- Skills

目录：

```
packages/
 extensions/
 skills/
```

---

# Milestone 4: Fate Inspired Runtime

实现：

## Settlement

负责：

- 判断行动结果
- 调用 Domain Tool
- 修改 State

## Render

负责：

- 小说化表达
- 场景描述

禁止 Render 修改事实。

---

# Milestone 5: Web Game

前端：React

组件：

```
CharacterPanel
Inventory
StoryView
ActionBar
QuestPanel
```

后端：

```
React
 ↓
API/WebSocket
 ↓
AgentSession
 ↓
Engine
```

---

# Git Commit 规范

每完成一个 Lesson：

```
feat(lesson-01): implement minimal agent loop
feat(lesson-02): add tool calling demo
feat(engine): add deterministic state engine
```

文档：

```
docs: update lesson notes
```

---

# 每个实现必须包含

1. README
2. Architecture Diagram
3. Source Explanation
4. Demo Screenshot
5. Test Case
6. Learning Note

---

# 最终验收

PiGame 必须证明：

- 理解 Agent Loop
- 理解 Tool Calling
- 理解 State Management
- 理解 AgentSession
- 理解 Extension/Skill
- 理解 Fate 双阶段架构
- 能连接 Web Frontend

最终不是复制 Fate，而是理解并重新设计一个 Agent Game Runtime。
