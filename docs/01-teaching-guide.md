# 教学文档：PiGame 学习方法

## 1. 教学目标

本课程不以 API 速查为核心，而以“理解 Runtime 为什么这样设计”为核心。每一个概念都先建立最小心智模型，再回到 Pi 真实源码，最后通过游戏场景验证理解。

## 2. 固定教学模板

每课文档后续统一采用以下结构。

### A. 本课问题

只提出 1–2 个核心问题，例如：

- 为什么普通 LLM Call 不是 Agent？
- Tool Result 为什么必须回到 Context？

### B. 理论模型

优先使用最小数据流图：

```text
Input
 ↓
Decision
 ↓
Action
 ↓
Observation
 ↓
Next Decision
```

说明：

- 每个节点是什么
- 谁拥有状态
- 谁可以产生副作用
- 何时结束一轮

### C. Pi 原生源码

只选本课最关键的源码。

记录格式：

```text
Repository:
Commit:
Path:
Symbols:
Call Direction:
Why It Matters:
```

阅读代码时分三层：

1. 主干控制流
2. 数据结构
3. 容错/工程细节

第一遍只要求看懂主干。

### D. Mini Demo

Demo 的目标不是“像 Pi 一样完整”，而是把本课核心机制压缩到最小规模。

示例：Agent Loop 课可以先用 Fake Model：

```text
User
 ↓
Fake Model -> toolCall
 ↓
Tool
 ↓
Tool Result
 ↓
Fake Model -> final text
```

等控制流完全看懂后，再接真实 Pi SDK。

### E. Fate Sandbox 对照

必须区分：

- Pi Core 原理
- Fate 的游戏业务规则
- Fate 为了可靠性增加的工程结构

例如：

```text
教学 Demo: state.hp -= damage
Fate: Domain Event → Validation → Atomic Settlement → Versioned State
```

这里不是要求复制 Fate，而是理解“为什么真实项目需要多这一层”。

### F. 练习

每次只做一个小改动，例如：

- 增加 heal tool
- 给 attack 增加参数校验
- 增加 turn_end 日志
- 增加 hidden secret

### G. 自检问题

每课至少保留三个问题：

1. 我能不用术语解释这个机制吗？
2. 我能在 Pi 源码里指出它在哪里发生吗？
3. 我能修改 Demo 证明自己不是死记代码吗？

## 3. 讲解风格

教学时遵守：

- 先图后代码
- 先伪代码后真实 TypeScript
- 一次只解释一条调用链
- 变量和类型首次出现必须解释
- 对“为什么不能直接这么做”给出反例
- 不把框架名称当作解释

## 4. 学习笔记格式

每一课建议最终形成：

```text
# Lesson N

## 理论
## Pi 源码
## Demo
## 执行日志
## Fate 对照
## 我真正学到的边界
## 作业
## 未解决问题
```

## 5. 课程与项目开发的关系

PiGame 同时有两条线：

```text
学习线：理解 Pi
产品线：逐步形成 Mini RPG
```

产品线永远不能领先学习线太多。若一个功能需要尚未学习的复杂机制，应先记录到 Backlog，而不是直接引入。
