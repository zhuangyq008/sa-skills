# PoC Proposal Design Workflow

Complete pipeline for designing Proof-of-Concept proposals for AWS customers.

## Pipeline

```
Customer Need → Requirements Analysis → Architecture Design → Proposal Doc → Alignment Prep
```

## Phase 1: Requirements Analysis

Gather and structure customer information:

1. **Customer profile**:
   - Company name, industry, scale
   - Current cloud usage (AWS / other cloud / on-premise)
   - IT team size and capability level
2. **Pain points**: what problems are they trying to solve?
3. **Goals**: what does success look like for the customer?
4. **Constraints**: timeline, budget, compliance, team skills

**Context to load**: Read `references/sa-best-practices.md` for capability assessment framework. Read `references/competitors.md` if competitor displacement is involved.

Output: Customer requirements profile (Markdown summary)

## Phase 2: Architecture Design

1. **Service selection**: choose AWS services based on requirements
   - Load `references/aws-services-cheatsheet.md` for service options
   - For each service chosen, document WHY this service and not alternatives
   - Consider customer team capability — prefer managed services for small IT teams
2. **Architecture description**: text-based architecture overview
   - Component diagram description (which services, how they connect)
   - Data flow description
   - Security boundaries

Output: Architecture section for proposal

## Phase 3: Proposal Document

Generate a structured PoC proposal in Markdown:

```markdown
# PoC Proposal: {Project Name}

## 1. Background
- Customer: {name}
- Current state: {description}
- Pain points: {list}

## 2. Objectives
- Primary goal: {goal}
- Success criteria:
  - {criterion 1}
  - {criterion 2}

## 3. Scope
### In Scope
- {item 1}
- {item 2}

### Out of Scope
- {item 1}

## 4. Architecture
{Architecture description from Phase 2}

### Service Selection Rationale
| Service | Purpose | Why This Service |
|---------|---------|-----------------|

## 5. Timeline
| Phase | Duration | Deliverable |
|-------|----------|-------------|
| Setup | Week 1 | Environment ready |
| Development | Week 2-3 | Core features |
| Testing & Demo | Week 4 | Demo + results |

## 6. Cost Estimate
### Pay-per-use Estimate
| Service | Usage Estimate | Monthly Cost |
|---------|---------------|-------------|

### Reserved/Savings Plan Estimate
| Service | Commitment | Monthly Cost |

## 7. Risks & Mitigation
| Risk | Impact | Mitigation |
|------|--------|-----------|

## 8. Team & Responsibilities
| Role | Responsibility | From |
|------|---------------|------|

## 9. Next Steps
- {action 1}
- {action 2}
```

### Proposal Rules (HARD)

- **PoC scope**: small, verifiable, completable in 2-4 weeks
- **Cost estimate**: MUST include both pay-per-use AND reserved pricing
- **Service rationale**: MUST explain why each service was chosen (not just what it does)
- **Team capability**: adjust complexity based on customer IT team size. Small team → prefer managed services, reduce operational burden
- **Competitor awareness**: if displacing competitor, note migration considerations

## Phase 4: Alignment Preparation

Generate meeting preparation materials:

```markdown
# PoC Alignment Meeting Agenda

## Meeting Info
- Customer: {name}
- Date: {date}
- Participants: {list}
- Duration: 60 min

## Agenda
1. (5 min) Introductions & meeting objectives
2. (15 min) Customer requirements review — confirm our understanding
3. (20 min) Proposed architecture walkthrough
4. (10 min) Timeline & responsibilities
5. (5 min) Cost overview
6. (5 min) Q&A and next steps

## Key Discussion Points
- {point needing customer input 1}
- {point needing customer input 2}

## Pre-meeting Preparation
- [ ] Proposal doc shared with customer
- [ ] Demo environment ready (if applicable)
- [ ] Cost calculator prepared
```
