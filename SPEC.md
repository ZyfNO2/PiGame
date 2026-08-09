# PiGame SPEC

## 1. 项目目标

PiGame 是面向学习者的 Pi Agent 游戏化源码课程仓库。项目通过一系列递进式 TypeScript Demo，将 Pi Agent 的核心 Runtime 概念映射到一个小型 RPG。

## 2. 功能范围

### 2.1 教学层

每课必须具备：

- Theory：概念与数据流
- Pi Source：官方源码路径、函数、类型
- Demo：最小实现
- Fate Mapping：Fate Sandbox 对照
- Exercise：小作业
- Verification：验证结果

### 2.2 Runtime 学习层

课程必须覆盖：

- Agent Loop
- Message / Context
- Tool Schema / Tool Call / Tool Result
- AgentSession
- Event Stream
- Extension
- Skill
- Session / Context / Compaction
- Deterministic Game State
- Settlement / Render
- Hidden/Public State
- Snapshot / Reroll / Rollback

### 2.3 游戏层

最终 Mini RPG 至少包含：

- 玩家状态：HP、资源、背包
- NPC/Enemy 状态
- 场景 / 时间
- 3–5 个 Domain Actions
- 确定性状态更新
- Agent 自然语言输入理解
- Settlement 与 Render 分离
- Snapshot / 回滚
- Web UI 状态展示

## 3. 非功能要求

### 3.1 可学习性

- 单课只增加一个主要概念。
- Demo 优先控制在可一次读完的规模。
- 教学文档必须解释“为什么”，不只解释“是什么”。

### 3.2 可观察性

所有 Agent Demo 应尽量能观察：

```text
agent_start
turn_start
message/tool call
tool execution
tool result
turn_end
agent_end
```

### 3.3 可验证性

- 关键状态变化必须可断言。
- Tool 参数验证失败必须可观察。
- 真实模型验证与离线验证必须分开记录。

### 3.4 架构边界

Canonical Game State 的唯一事实来源必须是 Engine/State 层。

```text
LLM = Planner / Narrator
Tool = Capability Boundary
Engine = Rule Authority
State = Source of Truth
UI = Presentation
```

## 4. 教学仓库目录目标

```text
PiGame/
├── README.md
├── SOP.md
├── SPEC.md
├── docs/
│   ├── 00-project-plan.md
│   ├── 01-teaching-guide.md
│   ├── 02-course-roadmap.md
│   ├── 03-pi-source-map.md
│   ├── 04-fate-source-map.md
│   ├── 05-reference-projects.md
│   └── 06-target-architecture.md
├── lessons/                 # 后续阶段创建
├── demos/                   # 后续阶段创建
├── mini-rpg/                # 后续阶段创建
├── web/                     # 后续阶段创建
└── HANDOFF.md
```

当前文档阶段不创建空代码目录。

## 5. 课程 Demo 规格

### L01 Mini Agent Loop

- Fake Model
- Message List
- 循环停止条件
- 至少一次 Tool → Result → Model 的往返

### L02 Tool Calling

- Typed Tool Schema
- 参数验证
- 正常与失败路径

### L03 Game State

- 独立 canonical state
- Engine function
- LLM 不直接写状态

### L04 AgentSession

- 使用 Pi SDK
- session.prompt()
- messages/state 可观察

### L05 Event Stream

- subscribe()
- 日志化核心 lifecycle event

### L06 Extension

- 自定义命令或工具
- 与 Pi Core 解耦

### L07 Skill

- start-game workflow
- 明确 Skill 与 Tool 区别

### L08 Context / Compaction

- 长对话上下文管理
- 说明 Session State 与 Game State 区别

### L09 Two-Pass

- Settlement 输出结构化 Direction Packet
- Render 不允许修改 State

### L10 Hidden State

- public/playerKnowledge/hidden 分区
- Renderer 只获得授权信息

### L11 Snapshot / Rollback

- turn snapshot
- rerender 与 rollback 行为不同

### L12 Web Frontend

- React 前端
- Agent Runtime 后端
- UI 只消费事件与状态快照

## 6. Acceptance Criteria

项目进入“课程可用”状态需要满足：

- L01–L07 全部具有理论、源码映射、Demo 与验证
- 至少一个真实 Pi AgentSession Demo 可运行
- Mini RPG 的 canonical state 不依赖 Prompt 文本维护
- 至少一个 Fate 对照链路被完整解释

项目进入“游戏原型可用”状态需要额外满足：

- Two-Pass 可运行
- Hidden State 边界可验证
- Snapshot/Rollback 可验证
- Web UI 能展示并操作最小游戏循环

## 7. 明确排除项

首轮课程不要求：

- 商业级安全沙箱
- 多人联网
- 大规模 RAG
- 复杂经济系统
- 完整 Fate 世界数据
- 高级美术资产
- Production deployment

这些属于后续拓展，不应阻塞核心课程。
