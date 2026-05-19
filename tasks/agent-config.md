# 任务：配置 Learning Agent 工作流

- **来源**：WCB Learning
- **日期**：2026-05-19
- **状态**：已完成

---

## 1. 选择的 Agent / AI 工具

备选工具：OpenCode (CLI) / Claude Code / Codex / Hermes Agent

| 项目 | 说明 |
|------|------|
| **主力 LLM** | DeepSeek（价格便宜，大部分场景够用） |
| **辅助 LLM** | Codex（特定任务补充） |
| **Agent 用途分配** | 待定，目前优先用 OpenCode + DeepSeek 组合维护学习仓库、生成笔记草稿、代码实验，其余工具根据后续需要再分配具体职责 |

> 各 Agent 的具体用途还在摸索中，会在后续 daily note 中更新。

---

## 2. AI 辅助学习记录

### Agent（OpenCode + DeepSeek）
- [x] 初始化 `ai-web3-school-cohort-0` 仓库（目录结构、模版文件）
- [x] 生成 `README.md`（含 Week 1 目标、目录说明、隐私提醒）
- [x] 生成 `profile.md`（学员画像）
- [x] 生成 `learning-plan.md`（4 Phase 学习路径）
- [x] 生成第一篇 daily note（`daily/2026-05-18.md`）
- [x] 维护后续 daily notes、task 记录、handbook feedback

### 学习辅助（Web 版 DeepSeek）
- 阅读 Handbook 时通过 Web 版 DeepSeek 交互式提问，辅助理解概念（非 agent 用途）
- 虽不算 agent，但属于学习流程中主动利用 AI 理解知识的一环

---

## 3. 关键 Prompt

初始化时使用的启动 Prompt（发给 OpenCode）：

> 请作为我的 AI × Web3 School Learning Agent，先阅读启动 Prompt：https://aiweb3.school/learning-agent.zh.txt ，并结合 Handbook：https://aiweb3.school/zh/handbook/ ，帮我初始化个人学习计划、GitHub 学习仓库、每日打卡草稿和 Handbook feedback 流程。
>
> 要求：
> - 仓库名：ai-web3-school-cohort-0，public
> - 业务背景：Java 工程师，近期自学 Agent 开发，AI 为主攻方向，Web3 为扩展
> - 每步写文件/commit/push 前必须等我确认

---

## 4. 一次成功输出记录

Agent 生成了仓库初始化 commit（节选部分输出）：

```text
仓库名：ai-web3-school-cohort-0
可见性：public
目录结构：
  ├── README.md
  ├── profile.md
  ├── learning-plan.md
  ├── daily/
  ├── tasks/
  ├── experiments/
  ├── handbook-feedback/
  ├── hackathon/
  ├── submissions/
  └── templates/
      ├── daily-note.md
      └── task-note.md

已创建 4 个文件、8 个目录，等待确认后 commit 并 push。
```

确认后成功推送到 `https://github.com/FuShengV5/ai-web3-school-cohort-0`。

---

## 5. 人工复核/修正记录

| 时间 | 场景 | Agent 建议 | 我的处理 |
|------|------|------------|----------|
| 05-19 | Week 1 计划 | Agent 建议 Phase 1 先 AI + Web3 同步推进 | **修正**：改为 AI 优先、Web3 为辅，先系统补齐 AI 再进入 Web3 |
| 05-19 | 学习计划措辞 | Agent 初始生成的 learning-plan 描述了"熟悉 Web3 开发" | **修正**：改为"Web3 新手，了解为主"，更符合实际情况 |
| 05-19 | 仓库可见性 | Agent 询问是否设为 private | **修正**：按课程要求设为 public |
| 05-19 | agent-config.md 审核 | Agent 生成了详细的 Agent 工具用途分配表 | **修正**：各工具用途还不确定，改为"待定"，补充说明主力用 DeepSeek（便宜） |
| 05-19 | agent-config.md 审核 | Agent 只记录了 coding agent 的使用 | **补充**：加入 Web 版 DeepSeek 作为 Handbook 学习辅助工具（非 agent 用途） |

### 参考资料

- [Learning Agent 启动 Prompt](https://aiweb3.school/learning-agent.zh.txt)
- [AI × Web3 School Handbook](https://aiweb3.school/zh/handbook/)
