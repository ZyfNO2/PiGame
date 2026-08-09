# Pi 源码阅读地图

## 1. 上游基线

- Repository: `https://github.com/earendil-works/pi`
- Default branch: `main`
- 文档基线记录：`936aff00918de1187f085f123c2812d8f2d67745`

> 该 SHA 只表示本教学计划建立时观察到的上游状态。每一课开始前按 SOP 重新记录实际阅读 SHA。

## 2. 包级心智模型

```text
packages/ai
  ↓ 统一模型与 Provider 接口
packages/agent
  ↓ Agent Loop / Tool Calling / Agent State
packages/coding-agent
  ↓ AgentSession / Tools / Extension / Skill / Compaction / CLI
packages/tui
  ↓ Terminal presentation
```

## 3. 第一优先级源码

### `packages/agent/src/agent-loop.ts`

课程用途：Lesson 01–02。

重点追踪：

- `agentLoop()`
- `runAgentLoop()`
- `runLoop()`
- `streamAssistantResponse()`
- Tool Call 提取与执行
- Tool Result 回到 Context
- turn / agent 生命周期事件

阅读目标：看懂“为什么一次 prompt 可能触发多次模型调用”。

### `packages/agent/src/types.ts`

课程用途：Lesson 01–02。

重点：

- AgentMessage
- AgentContext
- AgentTool
- AgentEvent
- AgentLoopConfig

阅读目标：知道 Agent Loop 在传递什么数据，而不是只看控制流。

## 4. Coding Agent / SDK 层

### `packages/coding-agent/docs/sdk.md`

课程用途：Lesson 04–05。

重点 API：

- `createAgentSession()`
- `AgentSession.prompt()`
- `steer()` / `followUp()`
- `subscribe()`
- `session.agent.state`
- `compact()`

阅读目标：从“自己写 Loop”过渡到“使用 Pi Runtime”。

### `packages/coding-agent/src/`

进入每课前再定位当前实现文件，重点关注：

- AgentSession 实现
- SessionManager
- built-in tools
- resource loading
- extensions
- skills
- compaction

由于 Pi 仍在快速演进，不在计划阶段把所有内部路径写死。

## 5. Tool 学习路线

源码阅读顺序建议：

```text
AgentTool type
 ↓
Tool schema
 ↓
validateToolArguments
 ↓
executeToolCalls
 ↓
ToolResultMessage
 ↓
下一轮模型调用
```

教学重点不是 bash/read/edit 工具本身，而是 Tool 作为 Capability Boundary 的机制。

## 6. Session 学习路线

```text
Agent Loop
 ↓
Agent State
 ↓
AgentSession
 ↓
Session persistence / tree
 ↓
Compaction
 ↓
Runtime replacement / UI integration
```

需要明确区分：

- Agent messages
- Session history
- Game canonical state

三者不是同一个东西。

## 7. UI 学习路线

`packages/tui` 只作为一种 Presentation Layer 研究。

课程不把 TUI 等同于 Pi Agent。最终 Web UI 将直接对接 AgentSession / backend runtime，而不是把终端界面嵌入浏览器。

## 8. 每课源码记录模板

```text
Upstream repo:
Commit SHA:
Path:
Symbol:
Caller:
Callee:
Input:
Output:
Side effect:
Why this exists:
Our mini-demo equivalent:
Fate equivalent:
```
