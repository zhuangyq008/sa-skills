# Example: PoC Proposal — Shokz AI Customer Service Agent

> This is a reference example of a PoC proposal produced by the poc-design workflow.

---

# PoC Proposal: Shokz AI 客服 Agent

## 1. Background
- **Customer**: Shokz (韶音科技) — 全球领先的开放式耳机品牌
- **Current state**: 客服团队使用传统工单系统，知识库分散在多个文档中
- **Pain points**:
  - 客服响应时间长（平均 4 小时）
  - 新客服培训周期长（2-3 周）
  - 产品知识更新不同步

## 2. Objectives
- **Primary goal**: 构建 AI 客服 Agent，实现常见问题自动回复 + 复杂问题辅助人工
- **Success criteria**:
  - 常见问题（FAQ）自动回复准确率 > 85%
  - 客服首次响应时间 < 30 秒
  - 人工客服处理量减少 40%

## 3. Scope

### In Scope
- 产品 FAQ 自动回答（基于 Knowledge Base）
- 售后政策查询
- 工单分类与路由

### Out of Scope
- 多语言支持（Phase 2）
- 语音客服集成
- 退款/换货自动处理

## 4. Architecture

```
用户 (Web/App) → API Gateway → Lambda → Bedrock Agent
                                          ├── Knowledge Base (S3 + OpenSearch Serverless)
                                          ├── Guardrails (内容安全)
                                          └── DynamoDB (会话历史)
```

### Service Selection Rationale

| Service | Purpose | Why This Service |
|---------|---------|-----------------|
| Amazon Bedrock | LLM API | Multi-model (Claude for Chinese), managed, pay-per-token |
| Bedrock Knowledge Base | RAG | 原生集成 Bedrock，无需自建 embedding pipeline |
| OpenSearch Serverless | Vector store | Serverless 免运维，韶音 IT 团队小 |
| API Gateway + Lambda | API layer | Serverless 架构，零运维，按量计费 |
| DynamoDB | Session store | 单位数毫秒延迟，Serverless 模式 |
| Bedrock Guardrails | Safety | 防止回复偏离客服场景，PII 过滤 |

## 5. Timeline

| Phase | Duration | Deliverable |
|-------|----------|-------------|
| Setup | Week 1 | AWS 环境 + Knowledge Base 数据导入 |
| Development | Week 2-3 | Agent 开发 + Prompt 调优 + API 集成 |
| Testing & Demo | Week 4 | 准确率测试 + 客户演示 |

## 6. Cost Estimate

### Pay-per-use Estimate (Monthly)

| Service | Usage Estimate | Monthly Cost |
|---------|---------------|-------------|
| Bedrock (Claude Sonnet) | 100K queries × ~1K tokens | ~$300 |
| OpenSearch Serverless | 2 OCU (index) + 2 OCU (search) | ~$700 |
| Lambda | 100K invocations | < $5 |
| DynamoDB | On-demand, ~1GB | < $10 |
| API Gateway | 100K requests | < $5 |
| **Total** | | **~$1,020/month** |

### Reserved Estimate (after PoC success)
- OpenSearch Serverless: no reservation option
- Bedrock: consider Provisioned Throughput if volume > 500K queries/month
- Estimated savings: 20-30% on high-volume Bedrock usage

## 7. Risks & Mitigation

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Knowledge Base 回答不准确 | 用户体验差 | Prompt engineering + human fallback + 持续更新 KB |
| 中文理解质量 | 客服场景需要方言/口语理解 | 选用 Claude (中文能力强) + 测试集验证 |
| 数据安全合规 | 客户数据涉及个人信息 | Guardrails PII 过滤 + VPC 内网部署 |

## 8. Team & Responsibilities

| Role | Responsibility | From |
|------|---------------|------|
| SA | 架构设计 + 技术指导 | AWS |
| 韶音 IT | 数据准备 + API 对接 + 测试 | Customer |
| SA Specialist (optional) | Bedrock 深度调优 | AWS |

## 9. Next Steps
1. 韶音提供 FAQ 文档和客服知识库（本周）
2. AWS 搭建 PoC 环境（下周一）
3. 双周对齐会（每周三 14:00）
4. Week 4 末: PoC 演示会
