---
name: aws-sa-toolkit
description: SA daily workflow engine - tech sharing production, PoC proposal design, meeting minutes, stakeholder communication, and activity logging for AWS Solutions Architects.
origin: custom
---

# AWS SA Toolkit

SA (Solutions Architect) daily workflow engine covering content creation, customer communication, and activity logging.

## When to Activate

- Creating tech sharing presentations (PPT/HTML slides)
- Designing PoC proposals or architecture solutions for customers
- Generating meeting minutes from notes or voice transcription
- Drafting internal communication (resource requests, cross-team coordination, customer emails, weekly updates)
- Logging SA activities (GenAI, Regular Key, Migration)

## Scene Router

Identify user intent from keywords and route to the appropriate workflow:

| User Intent | Keywords (CN/EN) | Route To |
|------------|-------------------|----------|
| Tech sharing production | 技术分享、PPT、演讲、文字稿、slides、presentation、draft | [01-tech-sharing](references/01-tech-sharing.md) |
| PoC proposal design | PoC、方案、架构设计、选型、proposal、architecture | [02-poc-design](references/02-poc-design.md) |
| Meeting minutes | 会议纪要、会议记录、纪要、meeting minutes、meeting notes | [03-meeting-minutes](references/03-meeting-minutes.md) |
| Internal communication | 邮件、话术、争取资源、沟通、周报、email、weekly、coordinate | [04-stakeholder-comm](references/04-stakeholder-comm.md) |
| Activity logging | 记录活动、activity、log activity、写 activity | [05-activity-log](references/05-activity-log.md) |

## Global Rules

These rules apply across ALL workflows:

1. **Language**: Chinese primary, technical terms keep English original (e.g., "Amazon Bedrock" not "亚马逊基岩")
2. **Audience confirmation**: Before producing output, confirm with user: audience, depth, format
3. **Developer/architect focus**: When audience is technical — explain principles, show evolution path, provide learning resources
4. **PPT production**: Use Anthropic's official `pptx` skill (https://github.com/anthropics/skills/tree/main/skills/pptx) with `SA-PPT-Template.pptx` for .pptx output, or `frontend-slides` skill for HTML output. Template location: `references/SA-PPT-Template.pptx`
5. **Context loading**: Load context files from `references/` on demand — do NOT read all context files upfront

## Context Files

Load these ONLY when the active workflow needs them:

| File | When to Load |
|------|-------------|
| [aws-services-cheatsheet](references/aws-services-cheatsheet.md) | PoC architecture design, tech sharing about AWS services |
| [competitors](references/competitors.md) | PoC proposals involving competitor displacement, tech comparisons |
| [sa-best-practices](references/sa-best-practices.md) | PoC scope/timeline decisions, customer capability assessment |
| [activity-templates](references/activity-templates.md) | Activity logging (loaded by 05-activity-log workflow) |

## How to Use This Skill

1. **Identify the user's intent** from the Scene Router table above
2. **Read the corresponding workflow module** for step-by-step procedures
3. **Follow Global Rules** throughout the workflow
4. **Load context files on demand** when a workflow step references them
5. **For examples**, see the `examples/` directory for reference outputs
