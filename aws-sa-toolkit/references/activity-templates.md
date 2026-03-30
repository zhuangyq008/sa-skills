# Activity Templates

## Directory Structure

Activities are organized by customer name under `log_activity/`:

```
log_activity/
├── {CustomerName}/
│   ├── _background.md          # Customer background info (auto-maintained)
│   ├── Demo_20260210.md
│   ├── PoC_20260315.md
│   └── Architecture-Review_20260320.md
├── {AnotherCustomer}/
│   ├── _background.md
│   └── ...
```

### Naming Rules
- Customer directory: Use official customer name in English (e.g., `Shokz`, `ByteDance`)
- Activity file: `{ActivityType}_{yyyyMMdd}.md` where ActivityType maps as:
  - Demo → `Demo`
  - Prototype/PoC/Pilot → `PoC`
  - Architecture Review → `Architecture-Review`
  - Immersion Day → `Immersion-Day`
  - Other Workshops → `Workshop`
  - Other Architectural Guidance → `Architectural-Guidance`
  - AO: Partner Solution Engagement → `Partner-Engagement`
  - Migration/Modernization Acceleration → `Migration-Acceleration`
  - MAP (Migration Acceleration Program) → `MAP`
  - Migration Readiness Assessment → `Migration-Readiness-Assessment`
- If same type on same day, append sequence: `Demo_20260210_2.md`

## Customer Background File (_background.md)

Each customer directory contains a `_background.md` that is automatically maintained. When recording a new activity, read this file first to maintain consistency, then update it if new information is learned.

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
- {Challenge 2}

## Competition
{Known competitors in deals}

## Active Workloads
- {Workload 1}: {status}
- {Workload 2}: {status}

## Key Contacts
- {Role}: {Name} (if mentioned)
```

---

## GenAI Activity Template

Activity Subject:
[GenAI] {CustomerName} - XXX XXX

Activity Type:
- Demo [Architecture]
- Prototype/PoC/Pilot [Architecture]
- Architecture Review [Architecture]
- Other Workshops [Workshops]

Activity Description:
* Workload/Use case:
* Challenge:
* Competition:
* Technical Activity details:
* Winning strategy:
* Outcome:
* Regions:

---

## Regular Key Activity Template

Activity Subject:
[Regular Key] {CustomerName} - XXX XXX

Activity Type:
- Architecture Review [Architecture]
- Demo [Architecture]
- Prototype/PoC/Pilot [Architecture]
- Immersion Day [Workshops]
- Other Workshops [Workshops]
- Other Architectural Guidance [Architecture]
- AO: Partner Solution Engagement [Architecture]

Activity Description:
* Workload/Use case:
* Challenge:
* Competition:
* Technical Activity details:
* Winning strategy:
* Outcome:
* AWS Service:
* Regions:
* Involved support:

---

## Migration Activity Template

Activity Subject:
[Migration] [SA-sourced] {CustomerName} - XXX XXX

Activity Type:
- Migration/Modernization Acceleration [Architecture]
- MAP (Migration Acceleration Program) [Program Execution]
- Migration Readiness Assessment [Architecture]

Activity Description:
* Workload/Use case:
* Challenge:
* Technical Activity details:
* Winning strategy:
* Why migration: details of migration driver
* From where to where, narrow to region:
* Details Doc link: (Workdoc link)
* SA-sourced Indicator: SA-sourced/""
