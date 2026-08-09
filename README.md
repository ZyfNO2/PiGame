# PiGame

一个以 **Pi Agent 源码学习 + Fate Sandbox 对照 + 小型游戏 Demo** 为主线的教学型项目。

本仓库当前阶段只提交文档，不提交实现代码。后续每一课采用统一方法：

```text
理论 → Pi 原生源码 → 最小 Demo → Fate Sandbox 对照 → 小作业
```

目标不是“会调用 Pi”，而是理解并能亲手实现：

- Agent Loop
- Tool Calling
- Game State / Deterministic Engine
- AgentSession / Event Stream
- Extension / Skill
- Context / Session / Compaction
- Settlement / Render 双 Pass
- Hidden State / Rollback
- React/Web 游戏前端接入 Pi Runtime

## 文档入口

- [项目计划](docs/00-project-plan.md)
- [SOP：教学与开发执行流程](SOP.md)
- [SPEC：项目与课程规格](SPEC.md)
- [教学设计](docs/01-teaching-guide.md)
- [课程路线图](docs/02-course-roadmap.md)
- [Pi 源码阅读地图](docs/03-pi-source-map.md)
- [Fate Sandbox 对照阅读地图](docs/04-fate-source-map.md)
- [参考项目索引](docs/05-reference-projects.md)
- [目标架构与阶段边界](docs/06-target-architecture.md)
- [Handoff](HANDOFF.md)

## 参考主线

```text
Pi Core
  ↓
Pi Coding Agent / AgentSession
  ↓
Fate Sandbox / LOTM Sandbox
  ↓
SillyTavern / JS-Slash-Runner / TavernWeave
  ↓
React Web Game Frontend
```

## 当前状态

- 阶段：Documentation Baseline
- 代码：未开始
- 下一步：Lesson 01 — Agent Loop
