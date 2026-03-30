# SA Best Practices

Principles and frameworks for designing customer proposals and PoC engagements.

## Customer Team Capability Assessment

Before proposing architecture, assess the customer's operational readiness:

| Signal | Small/Junior Team | Mature/Large Team |
|--------|------------------|-------------------|
| IT headcount | < 10 | > 30 |
| Cloud experience | < 1 year | > 3 years |
| Existing IaC | Manual / console | Terraform / CDK |
| On-call process | None / ad-hoc | Structured rotation |
| CI/CD | Manual deploy | Automated pipeline |

### Adjustment Rules
- **Small team**: prefer fully managed services (Fargate > EKS, Aurora Serverless > self-managed RDS, Lambda > EC2). Minimize operational surface.
- **Large team**: can handle more control (EKS acceptable, self-managed services OK). Optimize for cost and customization.
- **Mixed signal**: default to managed services. Customer can always take more control later; harder to go the other way.

## PoC Scope Definition

A good PoC is:
- **Small**: 1-2 core use cases, not the entire production system
- **Verifiable**: clear success metrics that can be measured
- **Time-boxed**: 2-4 weeks, including setup and demo
- **Representative**: uses real-ish data and actual service integrations

### Scope Checklist
- [ ] Can we demo the result in under 15 minutes?
- [ ] Can a customer developer reproduce this with our documentation?
- [ ] Does it address the customer's #1 pain point?
- [ ] Is the timeline realistic for the customer's availability?

### Anti-patterns
- Trying to replicate the entire production system
- Using synthetic data that doesn't represent real workloads
- Scope creep during the PoC ("can we also add X?")
- No success criteria defined upfront

## Cost Estimation Methodology

Always provide BOTH perspectives:

### Pay-per-use Estimate
- Calculate based on expected usage patterns
- Include data transfer costs (often overlooked)
- Add 20% buffer for unexpected usage
- Show monthly and annual totals

### Reserved / Savings Plan Estimate
- Calculate 1-year and 3-year commitment savings
- Compare against pay-per-use to show ROI
- Note which services support Savings Plans
- Include break-even analysis (when does commitment pay off?)

### Cost Presentation Tips
- Lead with pay-per-use (lower commitment barrier)
- Show reserved pricing as "after successful PoC" optimization
- Compare with competitor pricing if customer is evaluating alternatives
- Include Graviton pricing where applicable (20-40% savings)

## Architecture Decision Documentation

For each major decision in a proposal, document:

```markdown
### Decision: {What was decided}
- **Options considered**: {A, B, C}
- **Chosen**: {A}
- **Rationale**: {Why A over B and C — specific, not generic}
- **Trade-offs accepted**: {What we give up with this choice}
- **Reversibility**: {Easy/Medium/Hard to change later}
```

This prevents "why did we choose X?" questions in later meetings.

## Proposal Tone Guidelines

- **Be specific**: "Reduces latency from 2s to 200ms" beats "improves performance"
- **Be honest about trade-offs**: customers respect transparency
- **Quantify**: use numbers, timelines, cost ranges
- **Customer language**: mirror the terms they use, not AWS jargon
- **Action-oriented**: every section should end with a clear next step
