# AI × Web3 School — 个人学习仓库

AI × Web3 School 是由 [LXDAO](https://lxdao.io/) 与 [ETHPanda](https://ethpanda.org/) 共同发起的面向 builders 的开源学习计划。本仓库用于记录个人学习日志、任务证明、实验记录、每日打卡草稿和 Handbook feedback。

## 入口链接

- **Handbook**：https://aiweb3.school/zh/handbook/
- **WCB 课程页面**：https://web3career.build/zh/programs/AI-Web3-School
- **WCB Learning 页面**：https://web3career.build/zh/programs/AI-Web3-School#tab=learning
- **Handbook 源码（GitHub）**：https://github.com/lxdao-official/aiweb3school
- **Telegram 社群**：https://t.me/aiweb3school

## 隐私提醒

本仓库为 **public**，请不要放入任何敏感信息，包括但不限于：

- API Key / Secret / Token
- 助记词、私钥
- 密码、验证码
- 未公开联系方式
- 内部会议链接或他人个人数据

## 目录说明

```text
.
├── README.md                  # 本文件
├── profile.md                 # 个人学员画像
├── learning-plan.md           # 学习计划
├── daily/                     # 每日学习笔记与打卡草稿
├── tasks/                     # 任务记录与证明
├── experiments/               # 实验代码、原型、Demo
├── handbook-feedback/         # Handbook 反馈（问题、建议、勘误）
├── hackathon/                 # Hackathon 准备与项目材料
├── submissions/               # WCB 提交记录
└── templates/                 # 笔记模版
    ├── daily-note.md          # 每日笔记模版
    └── task-note.md           # 任务笔记模版
```

## 使用方式

1. 每日学习前查看 WCB Learning 页面确认今日任务。
2. 按 `templates/daily-note.md` 模版撰写每日笔记。
3. 学习中的问题、卡点、建议沉淀到 `handbook-feedback/`。
4. 实验和原型代码放到 `experiments/`。
5. 定期 commit & push，保留学习轨迹。

---

## Week 1 学习目标

- [x] 初始化个人学习仓库结构
- [x] 阅读 Handbook — Network（网络）章节
- [ ] 完成 Network 最小实践：测试网交易追踪
- [ ] 阅读 Handbook — Cryptography（密码学）
- [ ] 阅读 Handbook — Wallet（钱包）
- [ ] 完成至少 3 篇 daily note
- [ ] 产出第一条 Handbook feedback

## Learning Agent 初始化说明

本仓库由 AI × Web3 School Learning Agent 辅助初始化，流程基于 [Learning Agent 启动 Prompt](https://aiweb3.school/learning-agent.zh.txt)：

- **Agent 做了什么**：收集学员画像、创建 GitHub repo、初始化目录结构（daily/tasks/experiments/handbook-feedback/hackathon/submissions/templates）、写入 README/profile/learning-plan/模版文件、生成第一篇 daily note 草稿
- **人工确认了什么**：仓库名与可见性、本地目录路径、commit 信息、推送操作；WCB Learning 页面任务确认和打卡提交仍需手动完成
- **安全边界**：Agent 不接触 API Key、私钥、密码等敏感信息；所有写入操作前需人工确认

---

> 学习始于行动，proof-of-work 是最好的笔记。
