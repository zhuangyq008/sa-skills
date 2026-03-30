# Example: Tech Sharing Draft — Amazon Bedrock AgentCore Deep Dive

> This is a reference example of a slide-by-slide draft produced by the tech-sharing workflow.

## Metadata
- **Topic**: Amazon Bedrock AgentCore
- **Audience**: Developers & Architects
- **Depth**: Deep-dive (60 min)
- **Language**: Chinese + English terms

---

## Slide 1: Title
- **Title**: Amazon Bedrock AgentCore 深度解析
- **Subtitle**: 从 Agent 原型到生产级部署的最后一公里
- **Author / Date**: {SA Name} / 2026-03

## Slide 2: Agenda
- AI Agent 的生产化挑战
- AgentCore 架构与核心能力
- Runtime 隔离模型详解
- 与 Bedrock Agents 的关系与演进
- Hands-on: 构建你的第一个 AgentCore Agent
- 学习资源与下一步

## Slide 3: AI Agent 的生产化挑战
- 原型 → 生产的鸿沟：安全隔离、可观测性、弹性扩展
- 多租户场景下的代码执行安全
- Agent 状态管理与会话持久化
- 成本控制与资源回收

[Speaker Notes]: 先讲痛点，让听众产生共鸣。可以举例：如果你让 Agent 执行用户提交的 Python 代码，如何保证不影响其他用户？

## Slide 4: AgentCore 定位
- Amazon Bedrock AgentCore = Agent 的生产级运行时
- 关键词：Managed Runtime + Per-user Isolation + Built-in Guardrails
- 不是替代 Bedrock Agents，而是补全"最后一公里"

[Speaker Notes]: 强调 AgentCore 解决的是"运行时"问题，不是"编排"问题

## Slide 5-6: 核心架构
- AgentCore Runtime: 每用户独立 microVM (Firecracker)
- Session Manager: 会话状态持久化
- Tool Registry: 工具注册与权限控制
- Guardrails Integration: 内容安全、PII 检测

[Speaker Notes]: 用 Firecracker microVM 做隔离是关键卖点，每个用户的代码执行环境完全独立

## Slide 7-8: Runtime 隔离模型
- Firecracker microVM: 启动时间 < 125ms
- 每用户独立文件系统、网络命名空间
- 资源配额：CPU、内存、磁盘、网络
- 自动回收：idle 超时后销毁

## Slide 9-10: vs Bedrock Agents
- Bedrock Agents: 编排层（ReAct loop、tool calling、knowledge base）
- AgentCore: 运行时层（代码执行、文件操作、环境隔离）
- 互补关系：Bedrock Agent 做大脑，AgentCore 做手脚

## Slide 11-14: Hands-on 演示步骤
- Step 1: 创建 AgentCore Agent
- Step 2: 配置工具（Code Interpreter + File Manager）
- Step 3: 设置 Guardrails
- Step 4: 发起会话并观察执行
- 参考代码链接：{GitHub repo URL}

## Slide 15-16: 适用场景
- 企业内部 AI 助手（多租户、安全要求高）
- 代码生成与执行平台
- 数据分析 Agent（用户上传文件 → Agent 处理 → 返回结果）
- Customer Case: 某科技公司内部 Copilot

## Slide 17-18: 成本与限制
- 计费模型：按 session 时长 + 资源消耗
- 当前限制：区域可用性、并发 session 数
- 与自建方案（E2B / Modal）的成本对比

## Slide 19-20: 学习路线
- 官方文档：{link}
- Workshop: {link}
- GitHub 示例：{link}
- 推荐阅读：Firecracker paper, Agent 设计模式

## Slide 21: Q&A
- 提问时间

## Slide 22: Thank You
- 联系方式
- 反馈链接
