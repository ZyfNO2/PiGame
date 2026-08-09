# 参考项目索引

本文件记录 PiGame 后续学习与架构设计的主要参考项目。

## 1. Pi / Agent Runtime

### Pi

- URL: https://github.com/earendil-works/pi
- 定位：Pi Agent Harness 主仓库。
- 重点：`pi-ai`、`pi-agent-core`、`pi-coding-agent`、`pi-tui`。
- 用途：所有课程的源码依据。

### Fate Sandbox

- 用户最初参考 URL: https://github.com/lolo-s-Cosmos/fate-sandbox
- 当前解析仓库: https://github.com/Xerxes-2/fate-sandbox
- 定位：基于 Pi Coding Agent 的确定性交互叙事 Runtime。
- 重点：Tool、Engine、State、Settlement/Render、Secret、Rollback、Extension、Skill。
- 用途：PiGame 的首要工程化对照教材。

### LOTM Sandbox

- URL: https://github.com/2722550596/lotm-sandbox
- 定位：Fate Sandbox 路线在《诡秘之主》世界中的大型实例。
- 重点：世界数据、职业/途径体系、Memory、Secret、Agent 模块化。
- 用途：观察 Runtime 如何从通用架构扩展为具体世界观游戏。

### pi-rp

- URL: https://github.com/2722550596/pi-rp
- 定位：Pi Coding Agent 的 RP 向 Fork。
- 重点：Prompt Preset、State、Schema、Reroll、Continue、TUI 与 Core 层改造。
- 用途：研究“什么适合 Extension，什么可能需要下沉 Core”。

## 2. 游戏前端 / 重前端

### zhushen-space

- URL: https://github.com/1102052563-a11y/zhushen-space
- 定位：重前端 Web AI RPG。
- 重点：React、Zustand、游戏面板、背包、战斗、RAG、状态解析、存档、游戏表现层。
- 用途：未来 Web Game UI 的主要功能参考之一。

## 3. SillyTavern 生态

### SillyTavern

- URL: https://github.com/SillyTavern/SillyTavern
- 定位：通用 LLM / RP 前端宿主。
- 重点：Character Card、Lorebook/World Info、聊天、模型接入、Extension、VN 表现。
- 用途：理解成熟 RP 前端生态。

### JS-Slash-Runner / 酒馆助手

- URL: https://github.com/n0vi028/JS-Slash-Runner
- 定位：SillyTavern 可编程扩展/运行层。
- 重点：JS、HTML/CSS UI、变量、Event Hook、Slash Command、World Book 与生成控制。
- 用途：参考“LLM Runtime 与复杂可编程前端如何连接”。

### TavernWeave

- URL: https://github.com/LiarMTTT/TavernWeave
- 定位：高级角色卡工程化工具/Skill 集。
- 重点：MVU、角色卡结构、World Book、Regex、助手脚本、嵌入式 UI、Live2D/音频、打包与调试。
- 用途：后期角色卡/状态 UI/内容工程参考。

## 4. 参考分工

```text
Pi 原理与 Runtime
→ Pi

Agent 游戏架构
→ Fate Sandbox
→ LOTM Sandbox

Core RP 改造
→ pi-rp

Web 游戏表现
→ zhushen-space

RP 前端与角色卡生态
→ SillyTavern
→ JS-Slash-Runner
→ TavernWeave
```

## 5. 使用规则

- 参考项目用于理解与对照，不默认复制实现。
- 真正进入某一课程前重新检查上游最新版本与 License。
- 源码事实与本仓库文档冲突时，以当时检查到的上游源码为准，并更新学习笔记。
- 世界观素材、角色卡内容和第三方 IP 数据不得默认纳入 PiGame 核心代码。
