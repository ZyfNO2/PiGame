# 目标架构与阶段边界

## 1. 最终目标

PiGame 最终不是终端聊天壳，而是一个有独立游戏表现层、确定性 Game State 与 Pi Agent Runtime 的 Mini RPG。

```text
┌─────────────────────────────────────┐
│            React Web Game           │
│ Story / HUD / Map / Inventory / UI │
└─────────────────┬───────────────────┘
                  │ Input / Events / State Snapshot
                  ▼
┌─────────────────────────────────────┐
│            Game Backend             │
│ Session orchestration / API bridge │
└─────────────────┬───────────────────┘
                  ▼
┌─────────────────────────────────────┐
│          Pi AgentSession            │
│ messages / events / model / tools  │
└─────────────────┬───────────────────┘
                  ▼
┌─────────────────────────────────────┐
│        Settlement Agent             │
│ understand intent / choose actions │
└─────────────────┬───────────────────┘
                  ▼
┌─────────────────────────────────────┐
│          Domain Tools               │
│ attack / travel / use_item / ...   │
└─────────────────┬───────────────────┘
                  ▼
┌─────────────────────────────────────┐
│      Deterministic Game Engine      │
│ validation / rules / invariants    │
└─────────────────┬───────────────────┘
                  ▼
┌─────────────────────────────────────┐
│       Versioned Canonical State     │
│ player / world / hidden / history  │
└─────────────────┬───────────────────┘
                  ▼
          Direction Packet
                  ▼
┌─────────────────────────────────────┐
│           Render Agent              │
│ prose only; no canonical mutation  │
└─────────────────┬───────────────────┘
                  ▼
             Web Presentation
```

## 2. 核心边界

### LLM

允许：

- 理解自然语言意图
- 选择 Tool
- 生成非 canonical 的叙事文本
- 做 NPC/剧情层决策建议

不允许直接成为：

- HP 真值存储
- Inventory 真值存储
- 金币真值存储
- 世界时间真值存储

### Tool

Tool 是 Agent 访问真实能力的边界。

每个有副作用的行为应尽量具备：

- 明确参数
- 参数验证
- 失败反馈
- 可测试返回值

### Engine

Engine 是规则权威：

- 检查动作是否合法
- 计算结果
- 维护 invariants
- 写入 canonical state

### State

State 是 Source of Truth。

后期建议至少分：

```text
public
playerKnowledge
hiddenCanonical
```

### Renderer

只消费已经结算的事实与允许公开的信息。

Renderer 的重新执行不应：

- 再扣一次 HP
- 再推进一次时间
- 再给一次物品

## 3. 阶段演进

### Stage A — 教学 Agent

```text
Fake Model
→ Mini Loop
→ Toy Tool
```

无 UI、无复杂 Game Engine。

### Stage B — Stateful RPG

```text
Pi AgentSession
→ Domain Tools
→ Tiny Engine
→ Game State
```

终端输出即可。

### Stage C — Fate-like Runtime

加入：

- Two-Pass
- Direction Packet
- Hidden State
- Snapshots
- Rerender / Rollback

### Stage D — Web Game

加入：

- React UI
- Backend bridge
- Streaming Events
- HUD / Inventory / Choices

### Stage E — Optional Ecosystem Features

核心架构稳定后再评估：

- World Book / RAG
- Tavern-like character package
- MVU 状态前端
- Audio / Live2D / CG
- Subagent
- richer world simulation

## 4. 前端参考原则

未来游戏表现层主要参考：

- zhushen-space：重 Web RPG 面板与交互
- SillyTavern：成熟 RP 前端宿主
- JS-Slash-Runner：脚本化嵌入 UI 与事件控制
- TavernWeave：MVU / Character Card / Embedded UI 工程方法

但 PiGame 不直接把 canonical state 放回前端 DSL；核心状态仍由 Backend/Engine 持有。

## 5. 决策准则

当出现“这个逻辑应该放哪里”的问题时，按以下顺序判断：

```text
只是展示？           → UI
只是叙事表达？       → Renderer
模型需要选择行为？   → Settlement Agent
模型需要执行能力？   → Tool
业务规则与合法性？   → Engine
需要长期作为真值？   → State
Pi 通用能力缺失？    → Extension，最后才考虑 Core Fork
```
