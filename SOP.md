# PiGame SOP

## 1. 目的

本 SOP 约束 PiGame 的教学、源码阅读、Demo 实现与后续工程化过程，确保每一课都能回答三个问题：

1. 这个 Agent 概念解决什么问题？
2. Pi 原生源码具体在哪里实现？
3. 我们能否用一个最小 Demo 独立复现其核心机制？

## 2. 每课执行流程

### Step 1 — 理论定义

先用最小概念模型说明本课主题，避免一开始陷入大型源码。

输出至少包含：

- 核心概念
- 输入 / 输出
- 生命周期或数据流
- 与上一课的关系
- 常见误区

### Step 2 — Pi 源码定位

只阅读与本课直接相关的 Pi 文件和函数。

必须记录：

- 仓库与分支
- 文件路径
- 关键函数 / 类型
- 调用方向
- 本课真正需要理解的代码段

禁止为了“完整”一次性展开整个调用树。

### Step 3 — 最小 Demo

独立实现教学版 Demo。

约束：

- 只复现本课核心机制
- 能离线时优先离线
- 优先 Fake/Stub Model 演示控制流，再接真实 Provider
- 每一步输出可观察日志
- 不复制大型工程无关抽象

### Step 4 — Fate Sandbox 对照

完成 Demo 后，再回 Fate Sandbox 找对应工程实现。

固定回答：

```text
我们的 Demo 中的 X
→ Fate 中对应哪个目录 / 模块？
→ Fate 为什么需要额外复杂度？
→ 哪些复杂度属于生产/游戏工程，而不是 Pi 核心？
```

### Step 5 — 验证

每个 Demo 至少验证：

- 正常路径
- 一个失败路径
- 状态是否符合预期
- Tool Result 是否正确返回 Loop
- 日志是否足以解释执行顺序

涉及真实模型时，必须区分：

- 离线控制流验证
- Mock/Fake 验证
- 真实 Provider 验证

不得把前两者写成真实 E2E。

### Step 6 — 小作业

每课提供一个 10–30 分钟的小变体。

示例：

- 新增一个 Tool
- 修改一个 Tool Schema
- 加一个 Engine invariant
- 观察不同 Event
- 增加一个失败条件

### Step 7 — 教学记录

每课结束更新教学文档，至少记录：

- 本课目标
- 学到的 Pi API / 源码
- Demo 路径
- Fate 对照路径
- 已验证内容
- 未理解/待追踪问题

## 3. 源码版本规则

Pi 和 Fate 都可能持续更新，因此每次正式进入一课前必须：

1. 检查上游仓库当前默认分支；
2. 记录本课实际阅读的 commit SHA；
3. 若源码与教学文档不一致，以当前源码为准；
4. 文档中标注“当前版本”和“历史版本差异”。

## 4. 实现纪律

- 先最小实现，再抽象。
- Game State 必须由 Engine/State 层持有，不由自然语言回答充当事实来源。
- 有副作用的行为通过 Tool/Domain API 进入。
- Renderer 不应直接修改 canonical state。
- 后续加入 Web UI 时，UI 不直接拥有 canonical game truth。
- 所有关键状态变化应可追踪。

## 5. Git 工作流

每一课建议使用独立分支：

```text
lesson/01-agent-loop
lesson/02-tools
...
```

提交粒度：

1. docs: lesson theory/source notes
2. feat: minimal demo
3. test: lesson verification
4. docs: fate comparison and conclusions

除非明确要求，不自动合并主分支。

## 6. 完成标准

一课只有在以下条件满足时才标记 DONE：

- 理论文档完成
- Pi 源码位置确认
- Mini Demo 可运行
- 最低验证通过
- Fate 对照完成
- 作业定义完成
- 未验证项明确标注
