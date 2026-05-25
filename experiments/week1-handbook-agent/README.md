# AI × Web3 School Handbook 问答助手

基于 Spring AI + Spring Boot 构建的 Handbook 智能问答 Agent。

![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F)
![Spring AI](https://img.shields.io/badge/Spring_AI-1.x-6DB33F)

---

## 1. 解决什么学习问题

AI × Web3 School 的 Handbook（ https://aiweb3.school/zh/handbook/ ）内容丰富，覆盖 AI 基础、Web3 基础、AI × Web3 Bridge、前沿探索四大模块共 30+ 章节，但以网页形式呈现，用户需要手动翻阅查找。

本工具将 Handbook 转化为**可对话的问答助手**：
- 用户直接用自然语言提问（如"什么是 RAG？""LLM 的局限性有哪些？"）
- Agent 自动从 Handbook 实时抓取对应章节内容
- 回答严格基于 Handbook 原文，标明章节路径，不凭空编造
- 支持连续对话（conversationId 隔离记忆）

---

## 2. 用户如何与它交互

通过 HTTP POST 请求与 Agent 对话：

```bash
POST /ai/ask
Content-Type: application/json

{
    "conversationId": "my-session-1",
    "question": "你的问题"
}
```

| 参数 | 说明 |
|------|------|
| `conversationId` | 可选。相同 ID 共享上下文记忆，不同 ID 隔离。不传则使用默认会话 |
| `question` | 必填。用户的问题 |

清空某会话的记忆：
```bash
DELETE /ai/memory/my-session-1
```

---

## 3. 输入示例和输出示例

### 示例 1：询问宏观概念

**输入：**
```json
{
    "conversationId": "demo-1",
    "question": "为我解释一下LLM"
}
```

**输出（摘自回复）：**
> 根据 Handbook 内容，LLM（大语言模型）是 AI 基础模块的首个核心概念（路径：`AI 基础 → 大语言模型（LLM）`）...
> - 擅长：语言理解与生成、推理模式识别、上下文内信息整合
> - 局限：不能替代确定性系统、不能直接操作外部世界、不天然可信或安全

### 示例 2：询问章节内知识节点

**输入：**
```json
{
    "conversationId": "demo-1",
    "question": "解释一下prompt中的Instruction"
}
```

**输出（摘自回复）：**
> 根据 Handbook 中 `ai/prompt` 章节的明确内容，Instruction（指令）是提示工程中的核心子概念...
> - Instruction 是给模型的任务规则，包含：任务目标、可用输入、禁止行为、输出格式&失败格式
> - 四段式实用写法是 Handbook 推荐的结构化模板
> - 关键提醒：Instruction ≠ 安全边界，高风险动作必须由代码层校验兜底

---

## 4. AI 生成 vs 人工修改/验证

| 部分 | AI 辅助 | 人工修改/验证 |
|------|---------|--------------|
| Spring Boot + Spring AI 框架搭建（项目骨架、MyBatis-Plus、Spring AI ChatClient、Controller、DTO） | — | 手动搭建，逐层完成 |
| System Prompt 设计方向（核心规则、回答规范、边界约束） | 与 Hermes Agent 讨论确定 | 人工确认并拍板终版 |
| System Prompt 代码实现 | OpenCode 编写 | 人工逐行审查确认 |
| HandbookQueryTools（getHandbookToc + getHandbookSection） | OpenCode 编写 | 人工审查并启动运行，验证了 LLM 回答能正确基于 Handbook 内容 |
| 整体功能验证 | — | 手动启动服务、发送多组问题，确认问答效果和章节路径的准确性 |

---

## 5. 限制和下一步改进

### 当前限制
- **HTML 解析较朴素**：使用正则提取纯文本，复杂结构（表格、代码块、嵌套列表）可能丢失语义
- **无缓存机制**：每次问答都重新抓取 Handbook 页面，网络抖动时可能超时
- **仅 REST API**：没有 Web UI，需要配合 curl / Postman / 前端使用
- **记忆为内存存储**：服务重启后对话记忆丢失

### 下一步改进方向
- 增加本地缓存（如 Caffeine）或定时同步，提升响应速度
- 改用 Jsoup 等 HTML 解析库，更精确提取结构化内容（表格、代码块）
- 添加 Web UI 界面（Vue 或 Thymeleaf 前端）
- 对话记忆持久化到数据库（如 Redis）
- 支持用户上传自定义文档作为补充知识源

---

> **安全声明**：本项目不包含任何 API Key、Token、私钥、助记词或 .env 等敏感信息。API Key 通过环境变量注入。
