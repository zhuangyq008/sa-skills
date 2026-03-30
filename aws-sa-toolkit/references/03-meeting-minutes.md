# Meeting Minutes Workflow

Transform raw meeting input (voice transcription, text notes, screenshots) into structured meeting minutes.

## Input Types

| Input | Handling |
|-------|---------|
| Voice transcription text | Tolerant of errors; quote ambiguous parts with `> 🎙️ 「原文」` |
| Text notes (bullet points) | Restructure into standard format |
| Screenshots | Extract visible text and structure |
| Mixed input | Process each type, merge into one output |

## Process

1. **Receive input**: user pastes or describes meeting content
2. **Parse and structure**: identify topics, decisions, action items
3. **Handle ambiguity**: for voice transcription errors, quote the original and provide best interpretation
4. **Generate output**: structured Markdown meeting minutes
5. **User review**: present for review, iterate on corrections

## Output Template

```markdown
# 会议纪要：{主题}

## 基本信息
- **时间**: {YYYY-MM-DD HH:MM}
- **地点/形式**: {线上/线下 + 平台}
- **参与者**: {姓名列表}
- **会议目的**: {一句话概述}

## 讨论要点

### {主题 1}
- {要点}
- {要点}

### {主题 2}
- {要点}

## 决策事项
1. {决策 1}
2. {决策 2}

## Action Items

| # | 事项 | 负责人 | 截止日期 | 状态 |
|---|------|--------|---------|------|
| 1 | {action} | {owner} | {date} | 待完成 |
| 2 | {action} | {owner} | {date} | 待完成 |

## 下次会议
- **时间**: {date/TBD}
- **议题预告**: {topics}
```

## Rules (HARD)

1. **Voice transcription tolerance**: do NOT correct transcription in-place. Quote the original with `> 🎙️ 「{原文}」` and provide interpretation below it
2. **Action Item extraction**: automatically identify any commitments, deadlines, or assignments mentioned. If deadline is unclear, mark as "待确认"
3. **Output format**: Markdown only
4. **Chinese output**: default to Chinese unless meeting was conducted in English
5. **Participant names**: use names as mentioned; do not guess full names from partial references
6. **Time conversion**: convert relative dates ("下周三") to absolute dates based on meeting date
