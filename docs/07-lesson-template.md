# Lesson 文档模板

> 每一课开始时复制本模板，保证“理论 → 源码 → Demo → Fate 对照 → 作业”不丢环节。

# Lesson XX — <Topic>

## 1. 本课目标

- 要解决的问题：
- 学完后应能解释：
- 学完后应能修改：

## 2. 先讲理论

### 2.1 核心概念

用不依赖 Pi 名称的方式解释机制。

### 2.2 最小数据流

```text
Input
 ↓
...
 ↓
Output
```

### 2.3 为什么需要它

给出“不使用该机制时”的具体失败例子。

### 2.4 与上一课的关系

说明新增了哪一层复杂度。

## 3. Pi 原生源码

### 3.1 源码版本

```text
Repository: https://github.com/earendil-works/pi
Branch:
Commit SHA:
```

### 3.2 阅读文件

| Path | Symbol | 本课作用 |
|---|---|---|
| | | |

### 3.3 主调用链

```text
caller
 ↓
function A
 ↓
function B
 ↓
result
```

### 3.4 关键代码逐段解释

只摘录必要片段，并解释：

- 输入
- 输出
- 状态变化
- 错误路径
- 为什么这样设计

## 4. Mini Demo

### 4.1 Demo 目标

只说明这一 Demo 想证明什么。

### 4.2 文件结构

```text
...
```

### 4.3 执行链

```text
...
```

### 4.4 运行命令

```bash
# 后续填写
```

### 4.5 预期日志

```text
# 后续填写
```

## 5. 验证

| Case | Expected | Actual | Status |
|---|---|---|---|
| normal | | | NOT VERIFIED |
| failure | | | NOT VERIFIED |

明确标识验证类型：

- Offline
- Fake/Mock
- Real Provider
- Real E2E

## 6. Fate Sandbox 对照

```text
Repository: https://github.com/Xerxes-2/fate-sandbox
Branch:
Commit SHA:
```

| PiGame Demo | Fate Path | Fate 多出来的工程能力 | 为什么需要 |
|---|---|---|---|
| | | | |

## 7. 本课架构结论

回答：

1. 哪个模块拥有事实？
2. 哪个模块产生副作用？
3. 哪个模块只是展示/叙事？
4. 哪个边界最重要？

## 8. 小作业

### 必做

一个 10–30 分钟的变体。

### 可选

一个需要继续查源码的问题。

## 9. 自检

- [ ] 我能不用框架术语解释本课机制
- [ ] 我知道 Pi 的对应源码
- [ ] 我能说明 Demo 与 Pi 的差异
- [ ] 我能说明 Fate 为什么更复杂
- [ ] 我修改过 Demo，而不是只运行

## 10. 未解决问题

- TBD
