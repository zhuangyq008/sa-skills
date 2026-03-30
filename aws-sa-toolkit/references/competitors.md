# Competitor Comparison Guide

Comparison talking points for AWS vs Azure, GCP, and Alibaba Cloud. Focus on domains most relevant to SA customer conversations.

## AI / ML

| Dimension | AWS | Azure | GCP | Alibaba Cloud |
|-----------|-----|-------|-----|--------------|
| LLM API | Bedrock (multi-model: Claude, Llama, Mistral, Titan) | Azure OpenAI (GPT-4, o1) | Vertex AI (Gemini) | Tongyi Qianwen (通义千问) |
| Agent Runtime | Bedrock AgentCore (microVM isolation) | Azure AI Agent Service | Vertex AI Agent Builder | - |
| Custom Training | SageMaker | Azure ML | Vertex AI Training | PAI |
| **AWS Advantage** | Model-agnostic, widest model selection, Guardrails for safety | OpenAI exclusivity, enterprise integration | Gemini multimodal, TPU pricing | China region compliance |

### Key Talking Points
- **vs Azure OpenAI**: "Single vendor lock-in to OpenAI models. Bedrock gives you Claude, Llama, Mistral + ability to switch without code changes"
- **vs GCP Vertex**: "Strong Gemini, but narrower model ecosystem. Bedrock's multi-model approach reduces risk"
- **vs Alibaba Cloud**: "For China mainland workloads, consider complementary approach. For global workloads, AWS has broader regional coverage"

## Serverless

| Dimension | AWS | Azure | GCP | Alibaba Cloud |
|-----------|-----|-------|-----|--------------|
| Functions | Lambda (max 15min, 10GB RAM) | Azure Functions | Cloud Functions | Function Compute |
| Containers | Fargate | Container Apps | Cloud Run | Serverless Container |
| Orchestration | Step Functions | Durable Functions / Logic Apps | Workflows | Serverless Workflow |
| **AWS Advantage** | Most mature, largest ecosystem, Graviton cost savings | .NET ecosystem, Logic Apps visual designer | Cloud Run simplicity, aggressive pricing | China compliance |

## Containers

| Dimension | AWS | Azure | GCP | Alibaba Cloud |
|-----------|-----|-------|-----|--------------|
| Kubernetes | EKS | AKS | GKE | ACK |
| Managed Containers | ECS/Fargate | Container Apps | Cloud Run | Serverless K8s |
| **AWS Advantage** | ECS simplicity for non-K8s teams, Fargate right-sizing, Graviton | AKS for Azure-native shops | GKE Autopilot operational simplicity | China region |

## Cost Positioning

- **Savings Plans**: flexible commitment (compute, ML, SageMaker)
- **Graviton instances**: 20-40% better price-performance vs x86
- **Spot instances**: up to 90% discount for fault-tolerant workloads
- **Free Tier**: 12-month free tier for common services
