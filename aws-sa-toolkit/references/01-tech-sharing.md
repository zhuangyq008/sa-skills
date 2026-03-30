# Tech Sharing Production Workflow

Complete pipeline for creating technical presentations: from research to final slides.

## Pipeline

```
Topic → Research → Clarify → Draft → Review → PPT/HTML → QA → Deliver
```

## Phase 1: Research

1. Receive topic from user
2. Search for latest materials using available tools:
   - Official AWS documentation (prefer Context7 MCP if available)
   - GitHub code search for implementations and examples
   - Blog posts and case studies
3. Compile research notes with key findings and source links
4. Present research summary to user before proceeding

## Phase 2: Clarify

Ask user to confirm (one question at a time if unclear):

- **Audience**: developers, architects, business leaders, mixed?
- **Depth**: overview (30min), medium (45min), deep-dive (60min+)?
- **Language**: Chinese primary with English terms? Full English?
- **Format**: .pptx (formal) or HTML slides (interactive)?
- **Angle**: what is the key message or takeaway?

## Phase 3: Draft

Generate a slide-by-slide Markdown draft (`{topic}-draft.md`):

```markdown
# {Presentation Title}

## Slide 1: Title Slide
- Title: {title}
- Subtitle: {subtitle}
- Author / Date

## Slide 2: Agenda
- Topic 1
- Topic 2
- ...

## Slide 3: {Topic}
- Bullet 1
- Bullet 2
- ...

[Speaker Notes]: {what to say on this slide}
```

### Draft Rules (HARD)

- **Page count**: 18-22 slides target
- **Bullets per slide**: maximum 6-7 points
- **No large code blocks**: provide reference links instead. If code is essential, max 5-6 lines
- **No ASCII diagrams**: convert to bullet-point descriptions or request diagram generation
- **No tables in slides**: use bullet lists or side-by-side columns instead
- **Chinese primary**: technical terms keep English (e.g., "Agent Runtime" not "代理运行时")
- **Structure for technical audience**: Principle → How it works → Evolution path → Learning resources

## Phase 4: Review

**HARD GATE: Draft MUST be reviewed and approved by user before proceeding to PPT.**

- Present draft to user
- Iterate on feedback
- Only proceed to PPT generation after explicit user approval

## Phase 5: PPT Generation

Based on user's format choice:

### Option A: .pptx (using ppt-maker skill)
1. Use the installed `ppt-maker` skill with `SA-PPT-Template.pptx` template
2. Template path: `~/.claude/skills/aws-sa-toolkit/references/SA-PPT-Template.pptx`
3. Map each slide from the draft to a PPT slide
4. Apply SA template styling

### Option B: HTML (using frontend-slides skill)
1. Use the installed `frontend-slides` skill
2. Convert the approved draft into an HTML presentation
3. Apply appropriate visual style

## Phase 6: QA Checklist

Before delivering, verify:

- [ ] Total slides: 18-22 range
- [ ] Each slide: ≤ 6-7 bullet points
- [ ] No large code blocks (>6 lines)
- [ ] No ASCII art or raw tables
- [ ] Chinese content with English technical terms
- [ ] Speaker notes included for key slides
- [ ] All reference links are valid
- [ ] Consistent formatting throughout

## Phase 7: Deliver

- Save final file to user's specified location
- Provide summary: slide count, key sections, customization points
- Offer to iterate if user wants changes
