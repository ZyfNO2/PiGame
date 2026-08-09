# Pi Agent Game Learning - Complete Lessons

## 教学原则

每一课固定结构：

1. 理论模型
2. Pi 原生源码阅读
3. 最小 Demo 实现
4. Fate Sandbox 对照
5. 练习与验收

---

# Lesson 01 Agent Loop

目标：理解 Agent 为什么不是一次 LLM 调用。

核心概念：

```
User
 ↓
Agent Loop
 ↓
LLM
 ↓
Tool Call?
 ↓
Tool Result
 ↓
Continue
```

源码：

- packages/agent/src/agent-loop.ts
- packages/agent/src/types.ts

Demo：mini-agent

实现一个最小 while loop，理解 message、tool call、result。

验收：能解释 Agent Loop 为什么需要循环。

---

# Lesson 02 Tool Calling

目标：理解 Agent 如何操作外部世界。

Demo：dice-agent

实现：

- rollDice
- calculateDamage
- simple action tool

源码重点：

- AgentTool
- Tool Schema
- Tool Result Message

Fate 对照：

- tools/
- domain actions

---

# Lesson 03 State Driven Game Engine

目标：理解为什么 State 不能放在 Prompt。

设计：

```
LLM = Planner
Engine = Truth
State = Source of Truth
```

Demo：RPG battle engine

包含：

- HP
- Inventory
- Gold
- Enemy

Fate 对照：engine/core/state

---

# Lesson 04 AgentSession

目标：从手写 Loop 进入 Pi Runtime。

学习：

- AgentSession
- message history
- model state
- lifecycle

Demo：session RPG

---

# Lesson 05 Event Stream

目标：理解 Agent Runtime 如何被 UI 观察。

学习：

- agent_start
- turn_start
- tool_execution_start
- tool_execution_end
- agent_end

Demo：Agent debugger

---

# Lesson 06 Extension

目标：理解 Pi 扩展机制。

Demo：game-status extension

增加：

- /status
- UI panel
- custom command

Fate 对照：extensions/

---

# Lesson 07 Skill

目标：理解任务流程封装。

Demo：start-game skill

流程：

```
Create Character
 ↓
Initialize World
 ↓
Create State
 ↓
Start Turn
```

Fate 对照：skills/start-game

---

# Lesson 08 Settlement / Render Architecture

目标：复刻 Fate 核心架构。

升级：

```
Player Action
 ↓
Settlement Agent
 ↓
Domain Tool
 ↓
Game Engine
 ↓
State
 ↓
Render Agent
 ↓
Story
```

重点：

游戏事实和文本表现分离。

---

# Lesson 09 Hidden State and Knowledge Boundary

目标：理解大型 RPG 信息隔离。

设计：

```
Public Facts
Player Knowledge
Hidden Canonical Facts
```

禁止依赖 Prompt 保密。

使用 Engine Context 控制信息。

---

# Lesson 10 Snapshot and Rollback

目标：理解 Session State 和 Game State。

实现：

- snapshot
- restore
- rewind
- reroll

Fate 对照：rollback / reroll

---

# Lesson 11 Web Game Frontend

目标：脱离 Terminal。

架构：

```
React
 ↓
Backend
 ↓
AgentSession
 ↓
Game Engine
```

实现：

- Character Panel
- Inventory
- Story Window
- Action Buttons

参考：zhushen-space、SillyTavern UI。

---

# Lesson 12 Final Mini Fate

最终项目：PiGame RPG Runtime

功能：

- Agent NPC
- Deterministic State
- Tool Calling
- Settlement/Render
- Extension
- Skill
- Memory
- Web UI

最终目标：理解 Pi Agent 如何成为游戏 Runtime。
