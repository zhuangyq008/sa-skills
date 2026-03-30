# AWS Services Cheatsheet for SA

High-frequency recommended services. Each entry: positioning, use case, differentiator.

## AI / ML

| Service | Positioning | Key Use Cases | vs Competitors |
|---------|------------|---------------|---------------|
| **Amazon Bedrock** | Managed foundation model API | LLM apps, RAG, agents, multi-model | vs Azure OpenAI: multi-model choice; vs GCP Vertex: tighter AWS integration |
| **Amazon Bedrock AgentCore** | Managed agent runtime | Production AI agents with tool use, code execution, memory | Unique: per-user microVM isolation, built-in guardrails |
| **Amazon SageMaker** | Full ML platform | Custom model training, fine-tuning, deployment | vs Azure ML: notebook-first UX; vs GCP Vertex: broader framework support |
| **Amazon Q Developer** | AI coding assistant | Code generation, transformation, security review | vs GitHub Copilot: AWS-native, Java/mainframe modernization |

## Compute

| Service | Positioning | Key Use Cases | vs Competitors |
|---------|------------|---------------|---------------|
| **AWS Lambda** | Serverless functions | Event-driven, API backends, data processing | vs Azure Functions: better cold start; vs GCP Cloud Functions: richer event sources |
| **Amazon ECS/Fargate** | Managed containers | Microservices, batch jobs, long-running services | vs Azure Container Apps: more control; vs GCP Cloud Run: persistent tasks |
| **Amazon EC2** | Virtual machines | Full control workloads, GPU instances, HPC | Broadest instance family, Graviton price-performance |

## Storage & Database

| Service | Positioning | Key Use Cases | vs Competitors |
|---------|------------|---------------|---------------|
| **Amazon S3** | Object storage | Data lake, static assets, backup | Industry standard, 11 nines durability |
| **Amazon DynamoDB** | Serverless NoSQL | User sessions, real-time data, high-scale KV | vs Azure CosmosDB: simpler pricing; single-digit ms at any scale |
| **Amazon Aurora** | Managed relational DB | OLTP, PostgreSQL/MySQL compatible | 5x MySQL throughput, serverless v2 auto-scaling |
| **Amazon Aurora DSQL** | Distributed SQL | Multi-region active-active, strong consistency | Unique: serverless distributed SQL with PostgreSQL compatibility |

## Integration & Messaging

| Service | Positioning | Key Use Cases | vs Competitors |
|---------|------------|---------------|---------------|
| **Amazon EventBridge** | Serverless event bus | Event-driven architecture, SaaS integration | vs Azure Event Grid: richer SaaS connectors |
| **Amazon SQS** | Message queue | Decoupling, async processing | Simplest queue service, no management overhead |
| **AWS Step Functions** | Workflow orchestration | Multi-step workflows, saga pattern | vs Azure Logic Apps: code-first; vs GCP Workflows: richer integrations |

## Networking & CDN

| Service | Positioning | Key Use Cases | vs Competitors |
|---------|------------|---------------|---------------|
| **Amazon CloudFront** | Global CDN | Static/dynamic content delivery, API acceleration | 600+ PoPs, Lambda@Edge for edge compute |
| **Amazon API Gateway** | Managed API layer | REST/WebSocket APIs, auth, throttling | vs Azure APIM: simpler for serverless; tighter Lambda integration |

## Security

| Service | Positioning | Key Use Cases | vs Competitors |
|---------|------------|---------------|---------------|
| **AWS IAM** | Identity & access | Fine-grained permissions, service roles | Most granular cloud IAM |
| **AWS Secrets Manager** | Secret management | API keys, credentials rotation | Auto-rotation for RDS, Redshift |
| **Amazon Bedrock Guardrails** | AI safety | Content filtering, PII detection, topic denial | Unique: model-agnostic, ApplyGuardrail API |
