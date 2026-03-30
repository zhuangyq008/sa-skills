# SA Activity Logging Workflow

Record SA activities in standardized format, organized by customer. Reads templates from `activity-templates.md`.

## Pipeline

```
User describes activity → Identify type → Fill template → Generate file → Update _background.md
```

## Step 1: Identify Activity Type

From user's description, determine the activity category:

| Category | Indicators | Template |
|----------|-----------|----------|
| **GenAI** | AI/ML, Bedrock, LLM, Agent, generative AI workloads | GenAI Activity Template |
| **Regular Key** | Architecture review, demo, workshop, partner engagement | Regular Key Activity Template |
| **Migration** | Migration, modernization, MAP, cloud migration | Migration Activity Template |

If unclear, ask the user: "这个活动属于 GenAI、Regular Key 还是 Migration 类型？"

## Step 2: Fill Template

Load `references/activity-templates.md` and fill the matching template.

**Auto-fill from context** (if available from conversation or customer background):
- Customer name
- Regions
- Competition (from _background.md if exists)

**Ask user for** (required fields that can't be inferred):
- Workload/Use case
- Challenge
- Technical Activity details
- Outcome
- Winning strategy

Guide the user through missing fields one at a time. Do not dump all fields at once.

## Step 3: Generate File

### Directory Structure

```
log_activity/
├── {CustomerName}/
│   ├── _background.md
│   └── {ActivityType}_{yyyyMMdd}.md
```

### Naming Rules

- **Customer directory**: official English name (e.g., `Shokz`, `ByteDance`, `Changhong`)
- **Activity file naming**: `{Type}_{yyyyMMdd}.md`

Type mapping:
| Activity | File Prefix |
|----------|------------|
| Demo | `Demo` |
| Prototype/PoC/Pilot | `PoC` |
| Architecture Review | `Architecture-Review` |
| Immersion Day | `Immersion-Day` |
| Other Workshops | `Workshop` |
| Other Architectural Guidance | `Architectural-Guidance` |
| AO: Partner Solution Engagement | `Partner-Engagement` |
| Migration/Modernization Acceleration | `Migration-Acceleration` |
| MAP | `MAP` |
| Migration Readiness Assessment | `Migration-Readiness-Assessment` |

- Same type on same day: append sequence `_2`, `_3` (e.g., `Demo_20260210_2.md`)

### File Content

Write the filled template as the file content. Include the Activity Subject line at the top.

## Step 4: Update Customer Background

After generating the activity file:

1. **Check if `_background.md` exists** in the customer directory
2. **If exists**: read it, append any NEW information learned from this activity (new contacts, new challenges, status changes). Never delete existing information.
3. **If not exists**: create `_background.md` using the template:

```markdown
# {CustomerName} ({中文名 if applicable})

## Region
{Operating regions}

## Industry
{Industry vertical}

## Background
{Brief company description and AWS relationship}

## Key Challenges
- {Challenge 1}

## Competition
{Known competitors in deals}

## Active Workloads
- {Workload 1}: {status}

## Key Contacts
- {Role}: {Name} (if mentioned)
```

## Rules (HARD)

1. **Never overwrite _background.md**: only append new information
2. **Ask for missing required fields**: do not guess or leave blank
3. **Use exact naming conventions**: file names must match the type mapping table
4. **Date format**: `yyyyMMdd` (e.g., `20260330`), use today's date if user doesn't specify
5. **Customer name consistency**: if a customer directory already exists, use the existing directory name
