# PiGame 项目计划书

## 1. 项目定位

PiGame 是一个“源码驱动的 Pi Agent 游戏学习仓库”。目标是通过一组逐步扩展的小 Demo，理解 Pi Agent Runtime，并最终组合出一个具备确定性状态、双阶段生成、回滚与 Web 前端的 Mini RPG。

本项目不以直接复刻 Fate Sandbox 为目标，而采用：

> Fate Sandbox 做真实教材；Pi 官方源码做原理依据；PiGame 自己实现最小教学 Demo。

## 2. 学习方法

每一课统一采用：

```text
理论
↓
Pi 原生源码定位
↓
最小可运行 Demo
↓
Fate Sandbox 工程化对照
↓
小作业 / 变体练习
```

## 3. 四个 Milestone

### M1 — Mini Agent

掌握：Model、Message、Agent Loop、Tool Call、Tool Result。

产物：最小 Agent / Dice Agent。

### M2 — Stateful Runtime

掌握：Game State、AgentSession、Event Stream、Extension、Skill、Session。

产物：Stateful Mini RPG。

### M3 — Fate-like Architecture

掌握：Settlement / Render 双 Pass、Domain Tool、Hidden State、Snapshot、Rollback。

产物：Fate-like Mini RPG Runtime。

### M4 — Game Frontend

掌握：Pi Runtime 与 React/Web UI 的边界、事件流、状态同步。

产物：可视化 Web Mini RPG。

## 4. 课程主线

1. Agent Loop
2. Tool Calling
3. Deterministic Game State
4. AgentSession
5. Event Stream
6. Extension
7. Skill
8. Session / Context / Compaction
9. Settlement / Render 双 Pass
10. Hidden State / Secret Boundary
11. Snapshot / Reroll / Rollback
12. React/Web Frontend

## 5. 设计原则

- 每节只引入一个主要新概念。
- 先写最小 Demo，再对照大型工程。
- LLM 不是 Game State 的事实来源。
- 世界状态更新必须经过可验证 Tool / Engine 边界。
- 教学代码优先可观察、可调试，不追求过早抽象。
- 未学到的复杂能力不提前塞入 Demo。

## 6. 前期明确不做

在核心链路掌握前，不加入：

- RAG / Vector DB
- MCP
- Multi-Agent / 大量 Subagent
- 大型 World Book
- Live2D
- 复杂战斗数值
- 数据库分布式持久化

这些内容将在核心 Runtime 稳定后再作为扩展课题。

## 7. 最终目标架构

```text
React Web Game
      ↓
Game Backend
      ↓
Pi AgentSession
      ↓
Settlement Agent
      ↓
Domain Tools
      ↓
Deterministic Game Engine
      ↓
Versioned Game State
      ↓
Direction Packet
      ↓
Render Agent
      ↓
Player-visible Story/UI
```

## 8. 当前阶段

当前仅建立文档基线。下一开发阶段从 Lesson 01 开始，不直接复制 Fate Sandbox 业务代码。
