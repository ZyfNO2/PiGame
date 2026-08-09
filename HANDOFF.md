# PiGame Handoff

## Repository

- Repo: `ZyfNO2/PiGame`
- Default branch: `main`
- 当前阶段：Documentation Baseline
- 代码实现：未开始

## 已完成

已建立第一版纯文档基线：

- `README.md` — 项目入口与总体学习路线
- `docs/00-project-plan.md` — 项目计划书
- `SOP.md` — 每课教学/源码阅读/Demo/验证/Git 执行流程
- `SPEC.md` — 项目、课程、Demo 与 Acceptance Criteria 规格
- `docs/01-teaching-guide.md` — 教学方法与讲解模板
- `docs/02-course-roadmap.md` — 4 Milestone / 12 Lesson 路线
- `docs/03-pi-source-map.md` — Pi 源码阅读地图
- `docs/04-fate-source-map.md` — Fate Sandbox 对照阅读地图
- `docs/05-reference-projects.md` — 参考项目索引
- `docs/06-target-architecture.md` — 最终 Runtime + Web Game 架构与边界
- `docs/07-lesson-template.md` — 后续每课可复用模板

## 关键架构决定

1. 不直接把 Fate Sandbox 当作待删减模板；Fate 作为真实工程教材。
2. 每个 Pi 概念先做最小 Demo，再回 Fate 对照。
3. 教学固定采用：

```text
理论 → Pi 原生源码 → Mini Demo → Fate 对照 → 小作业
```

4. Canonical Game State 由 Engine/State 持有，LLM 不作为 State Store。
5. 副作用通过 Tool / Domain Event 边界进入 Engine。
6. 后期采用 Settlement / Render 双 Pass。
7. React/Web UI 是 Presentation Layer，不拥有 canonical truth。
8. RAG、MCP、Multi-Agent、Live2D 等不进入核心入门阶段。

## 上游文档基线

### Pi

- Repo: `earendil-works/pi`
- Branch: `main`
- 计划建立时观察到的 commit: `936aff00918de1187f085f123c2812d8f2d67745`

### Fate Sandbox

- Repo: `Xerxes-2/fate-sandbox`
- Branch: `master`
- 计划建立时观察到的 commit: `6ece7ab66fb7b942b4e5c754aac1319e32004225`

注意：正式进入每课前仍需按 `SOP.md` 重新检查上游最新 commit，并将实际阅读版本记录到 Lesson 文档。

## 测试 / CI

本次提交仅包含 Markdown 文档：

- 运行时测试：N/A
- 单元测试：N/A
- 真实 Provider 测试：NOT STARTED
- CI：当前文档阶段未配置

没有把任何 Mock/Offline 验证描述为真实 E2E。

## 下一步

开始 Lesson 01：Agent Loop。

建议执行顺序：

1. 基于 `docs/07-lesson-template.md` 创建 Lesson 01 文档。
2. 检查 `earendil-works/pi` 当前 HEAD。
3. 阅读 `packages/agent/src/agent-loop.ts` 与相关 types。
4. 先解释主控制流，不展开全部工程细节。
5. 实现最小 Fake Model Agent Loop Demo。
6. 验证一次完整 Tool → Tool Result → 下一轮 Model 链路。
7. 回到 Fate Sandbox 对照 Settlement 的使用方式。
8. 补充小作业和验证记录。

## 状态

`READY FOR LESSON 01`
