# PiGame 课程路线图

## Milestone 1 — Agent Core

### Lesson 01 — Agent Loop

理论：普通 LLM Call 与 Agent Loop 的区别。

Pi：`packages/agent/src/agent-loop.ts`、`types.ts`。

Demo：Fake Model + 最小 Tool 往返。

Fate 对照：为什么 Settlement 本质仍建立在 Agent Loop 之上。

### Lesson 02 — Tool Calling

理论：Tool Schema、Tool Call、Tool Result、Observation。

Pi：参数验证、Tool 执行、Result 回灌 Context。

Demo：D20 骰子 / 检定工具。

Fate 对照：Domain-event tools。

### Lesson 03 — Deterministic Game State

理论：LLM ≠ State Store。

Demo：HP / Gold / Inventory 的确定性 Engine。

Fate 对照：Engine owns canonical state。

---

## Milestone 2 — Pi Runtime

### Lesson 04 — AgentSession

理论：Agent Loop 与 Session 的区别。

Pi：`createAgentSession()`、`AgentSession`。

Demo：最小 Pi SDK Session。

### Lesson 05 — Event Stream

理论：Runtime 如何把内部生命周期暴露给 UI / Debugger。

Demo：Agent Event Logger。

### Lesson 06 — Extension

理论：Core 与 Extension 边界。

Demo：`/status` 或 game tool extension。

Fate 对照：`extensions/`。

### Lesson 07 — Skill

理论：Tool = 能力；Skill = 工作流/任务方法。

Demo：`start-game`。

Fate 对照：`skills/start-game/`。

### Lesson 08 — Session / Context / Compaction

理论：Conversation State 与 Game State 的区别。

Demo：长 Session 的上下文观察与压缩。

---

## Milestone 3 — Fate-like Game Runtime

### Lesson 09 — Settlement / Render 双 Pass

理论：事实结算与叙事表达分离。

Demo：Settlement → Direction Packet → Render。

Fate 对照：`prompts/settlement/`、`prompts/render/`、`engine/prompt-assembly/`。

### Lesson 10 — Hidden State / Knowledge Boundary

理论：不要只靠 Prompt 防止秘密泄漏。

Demo：`public / playerKnowledge / hidden`。

### Lesson 11 — Snapshot / Reroll / Rollback

理论：重新表达 ≠ 重新结算 ≠ 恢复状态。

Demo：Turn Snapshot、rerender、rollback。

Fate 对照：reroll / rollback integrations。

---

## Milestone 4 — Game Presentation

### Lesson 12 — React/Web Frontend

理论：UI 与 Agent Runtime 解耦。

Demo：最小 Web RPG。

目标数据流：

```text
React UI
  ↓ input
Game Backend
  ↓
Pi AgentSession
  ↓ events/state snapshots
React UI
```

### 后续选修

核心课程完成后再考虑：

- SillyTavern 式角色卡 / World Book
- JS-Slash-Runner 式可编程 UI
- TavernWeave 式 MVU 与角色卡工程化
- RAG
- Subagent / Multi-Agent
- 世界模拟
- Live2D / Audio / CG
