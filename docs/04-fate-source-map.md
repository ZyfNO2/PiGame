# Fate Sandbox 对照阅读地图

## 1. 上游基线

用户最初提供的参考链接指向 Fate Sandbox 项目；当前 GitHub 解析到：

- Repository: `https://github.com/Xerxes-2/fate-sandbox`
- Default branch: `master`
- 文档基线记录：`6ece7ab66fb7b942b4e5c754aac1319e32004225`

README 当前将项目定义为：基于 Pi Coding Agent 的本地交互式叙事 Runtime，并明确采用“模型负责决策/叙事，确定性 TypeScript Engine 持有游戏状态”的设计。

## 2. 核心运行链

```text
Player Input
  ↓
Settlement Model
  ↓
Domain-event Tools
  ↓
Deterministic Engine
  ↓
Versioned Game State
  ↓
Direction Packet
  ↓
Render Model
  ↓
Player-visible Prose
```

PiGame 将在 Lesson 09 才完整复现这条链；前面的课程只逐个学习组成部分。

## 3. 目录对照

### `engine/core/`

职责：

- State
- Turns
- Scenes
- Actors
- Economy
- Memory
- Secrets
- Background work

PiGame 用途：Lesson 03、10、11 的真实工程对照。

### `engine/prompt-assembly/`

职责：Settlement / Render Prompt 组装与 preset loading。

PiGame 用途：Lesson 09。

### `tools/`

职责：GM-facing Domain Event Tools 与 world-data lookup。

PiGame 用途：Lesson 02–03。

核心问题：

> 为什么真实游戏不让模型直接提交任意 state patch，而是通过窄 Domain Tool？

### `prompts/settlement/`

职责：

- Settlement policy
- world boundaries
- tool routing
- direction contract

PiGame 用途：Lesson 09。

### `prompts/render/`

职责：

- rendering protocol
- prose rules
- output contract

PiGame 用途：Lesson 09–10。

### `extensions/`

职责：

- Pi UI panels
- compaction policy
- rerender / rollback integration
- audit lookup surface

PiGame 用途：Lesson 05–06、11。

### `skills/start-game/`

职责：New-game / character-creation state machine。

PiGame 用途：Lesson 07。

### `world-data/`

职责：Campaign presets 与世界观事实骨架。

前期只读，不复制世界数据；它属于内容层，不属于 Pi 核心课程。

### `docs/adr/`

职责：记录架构决定，包括状态分离、双 Pass、ledger、subprocess isolation 等。

学习大型工程时优先读 ADR，而不是只从代码反推设计意图。

## 4. 必须掌握的 Fate 设计思想

### 4.1 Model is an unreliable planner

LLM 可以提出动作，但不能作为 canonical state store。

### 4.2 Domain events instead of raw patches

游戏副作用通过窄接口进入 Engine，并由 schema 与 invariant 验证。

### 4.3 Public / knowledge / hidden separation

不要只依赖“Prompt 告诉模型不要泄密”；Renderer 应拿不到未授权事实。

### 4.4 Atomic settlement

失败事件不应留下半更新世界。

### 4.5 Rerender ≠ Replay Settlement

重新写正文不能再次推进时间或修改状态。

### 4.6 Rollback must restore both histories coherently

Conversation branch 与 Game State snapshot 的回退必须匹配。

## 5. PiGame 如何使用 Fate

不会：

- 从第一课开始复制 Fate 目录结构
- 直接使用 Fate 世界数据
- 把 Fate 的所有可靠性设计一次性搬过来

会：

- 每学完一个 Pi 核心机制，再找 Fate 对应实现
- 解释 Fate 为什么比教学 Demo 多一层
- 当 Mini RPG 需要真实可靠性时，再逐步吸收 Fate 的工程做法

## 6. 对照模板

```text
Concept:
Pi core mechanism:
PiGame mini demo:
Fate path:
Fate extra engineering:
Why Fate needs it:
Do we need it now?: yes/no/later
```
