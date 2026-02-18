# Processing Work Contributions - Daily Work Log

**When to use**: Day-to-day work log - any work done on projects, tasks, or initiatives

**Purpose**: Capture daily work meaningfully so it can be aggregated later to create a holistic view of contributions at year-end, performance reviews, or project completion.

## Storage Location
- `personal-memory/work-contribution/overview.md` - For daily work logs when starting or for general work
- `personal-memory/work-contribution/project-YYYY-MM-[project-name].md` - For work specific to a major project
- `personal-memory/work-contribution/project-YYYY-MM-[project-name]/project-YYYY-MM-[sub-project].md` - For work on sub-projects
- `personal-memory/work-contribution/[YYYY-QQ]-contributions.md` - Optional: For quarterly organization

## Project/Subproject Naming Convention

**Format**: `project-YYYY-MM-project-name` (for both main projects and sub-projects)

**Rules**:
- Always prefix with `project-` for both main projects and sub-projects
- YYYY-MM represents the date when the project/subproject started
- If the start date is not explicitly provided, derive it from the first work contribution entry for that project
- Use kebab-case for the project name (lowercase with hyphens)
- Examples:
  - `project-2026-02-dls-manager-approval-service.md` (project started Feb 2026)
  - `project-2025-11-payment-platform/project-2026-01-fraud-detection.md` (subproject started Jan 2026 within a project that started Nov 2025)

**Why this convention?**
- Provides chronological context at a glance
- Makes it easy to see when projects started
- Helps organize projects by timeline
- Maintains consistency across all project documentation

## How to Process

1. **Read the inbox entry** to identify:
   - What work was done?
   - Which project/initiative?
   - Who was involved?
   - What was the contribution level (Critical/Small/Medium)?
   - What document/artifact was worked on?

2. **Important Processing Rules**:
   - **Capture as provided**: Store work contributions exactly as provided by the user
   - **Handle missing information**: If any information is missing (person, contribution level, document link, etc.), capture it as "MISSING" rather than skipping the field
   - **Fix typos**: Correct any typos or sentence formation issues observed in the user's input
   - **Sub-projects**: If a project has sub-projects, create a folder for the main project and separate files for each sub-project

3. **Decide the destination**:
   - **[project-name].md**: Work specific to a particular project (when project is explicitly mentioned)
   - **[project-name]/[sub-project].md**: Work on specific sub-projects within a larger project
   - **Derived categories** (when project not specified): Analyze the work to determine:
     - **Scope**: Team-level or Org-level work
     - **Type**: Operational Excellence (OE) or Engineering Excellence (EE)
     - Create files like: `team-general.md`, `team-oe.md`, `team-ee.md`, `org-oe.md`, `org-ee.md`
   - **overview.md**: Only for truly miscellaneous work that doesn't fit other categories
   - **Quarterly file**: Optional - if organizing by time period

4. **Follow the simple daily log template**:

```markdown
## [Date] - [Brief Work Description]

**Project**: [Project Name] or [Derived: team-oe/team-ee/org-oe/org-ee/team-general]
**Person(s) Involved**: [Name(s)] or MISSING
**Contribution Level**: [Critical/Small/Medium] or MISSING
**Document/Link**: [Link to doc/PR/ticket/code] or MISSING

**Work Done**:
[Capture the work exactly as provided by user - what was done today]

**Additional Notes** (optional):
- Any relevant context
- Technologies used
- Related items
```

## Deriving Project Categories

When project name is not explicitly provided, analyze the work to derive appropriate categorization:

**Scope Determination:**
- **Team-level**: Work affecting your immediate team, team processes, team tools
- **Org-level**: Work affecting multiple teams, organization-wide initiatives, cross-team collaboration

**Type Determination:**
- **Operational Excellence (OE)**: Operations, on-call, incident management, monitoring, alerting, maintenance, toil reduction, runbooks, operational improvements
- **Engineering Excellence (EE)**: Development, architecture, design, code quality, testing, CI/CD, technical debt, new features, refactoring, performance optimization
- **General**: Regular team work that doesn't clearly fall into OE or EE

**Derived File Names:**
- `team-oe.md` - Team operational excellence work
- `team-ee.md` - Team engineering excellence work
- `team-general.md` - General team work
- `org-oe.md` - Organization-level operational excellence
- `org-ee.md` - Organization-level engineering excellence
- `org-general.md` - General organization-level work

## Example 1: Simple Daily Work Log

**Inbox Entry:**
```markdown
## [2026-02-18] Fixed bug in payment service

Fixed the timeout issue in payment processing. The bug was causing transactions to fail after 30 seconds. Updated the timeout configuration and added retry logic.

Person: John Doe
Contribution: Small
PR: https://github.com/company/payment-service/pull/234
```

**Result in work-contribution/project-2026-02-payment-platform.md:**
```markdown
## 2026-02-18 - Fixed timeout issue in payment processing

**Project**: Payment Platform
**Person(s) Involved**: John Doe
**Contribution Level**: Small
**Document/Link**: https://github.com/company/payment-service/pull/234

**Work Done**:
Fixed the timeout issue in payment processing. The bug was causing transactions to fail after 30 seconds. Updated the timeout configuration and added retry logic.
```

## Example 2: Work with Missing Project - Derive Category

**Inbox Entry:**
```markdown
## [2026-02-18] Led design review for new analytics dashboard

Led the technical design review for the new analytics dashboard. Reviewed architecture proposals from 3 teams, identified scalability concerns, and recommended solutions. Meeting doc has all the details.
```

**Analysis**: 
- Scope: Multiple teams → Org-level
- Type: Architecture, design → Engineering Excellence

**Result in work-contribution/org-ee.md:**
```markdown
## 2026-02-18 - Led design review for new analytics dashboard

**Project**: Derived: org-ee
**Person(s) Involved**: MISSING
**Contribution Level**: Critical
**Document/Link**: MISSING

**Work Done**:
Led the technical design review for the new analytics dashboard. Reviewed architecture proposals from 3 teams, identified scalability concerns, and recommended solutions. Meeting doc has all the details.
```

## Example 3: Operational Work

**Inbox Entry:**
```markdown
## [2026-02-18] Handled production incident

Responded to SEV2 incident - database connection pool exhaustion. Identified root cause, applied hot fix, and created follow-up ticket for permanent solution.
```

**Analysis**:
- Scope: Team-level (team's production service)
- Type: Incident response → Operational Excellence

**Result in work-contribution/team-oe.md:**
```markdown
## 2026-02-18 - Handled production incident

**Project**: Derived: team-oe
**Person(s) Involved**: MISSING
**Contribution Level**: Critical
**Document/Link**: MISSING

**Work Done**:
Responded to SEV2 incident - database connection pool exhaustion. Identified root cause, applied hot fix, and created follow-up ticket for permanent solution.
```

## Organization Strategy

**Project-specific files** (`[project-name].md`):
- When work explicitly mentions a project name
- Accumulate logs for the same project together

**Derived category files** (when project not specified):
- `team-oe.md` - Team operational excellence (on-call, incidents, monitoring, maintenance)
- `team-ee.md` - Team engineering excellence (development, architecture, testing, refactoring)
- `team-general.md` - General team work not clearly OE or EE
- `org-oe.md` - Organization-level operational excellence
- `org-ee.md` - Organization-level engineering excellence
- `org-general.md` - General organization-level work

**Sub-project folders** (`project-YYYY-MM-[project-name]/`):
- When a project has distinct sub-projects or components
- Each sub-project gets its own .md file
- Example structure:
  ```
  personal-memory/work-contribution/
    ├── overview.md (truly misc items only)
    ├── team-oe.md (team operational work)
    ├── team-ee.md (team engineering work)
    ├── org-ee.md (org-level engineering)
    ├── project-2026-02-payment-platform.md (dedicated project)
    └── project-2025-11-analytics-platform/
        ├── project-2025-11-data-pipeline.md (sub-project)
        ├── project-2026-01-dashboard-ui.md (sub-project)
        └── project-2026-01-reporting-api.md (sub-project)
  ```

**overview.md** - Use only for:
- Truly miscellaneous work that doesn't fit any category
- One-off items that don't warrant their own file

**Optional quarterly files** (`2026-q1-contributions.md`):
- Time-based organization if preferred
- Helpful for performance review preparation

## Tips for Daily Logging
- **Keep it simple** - this is a daily work log, not a detailed achievement writeup
- **Be consistent** - log work regularly so you have a complete record
- **Capture as provided** - store exactly what the user says they did
- **Always track person** - critical for team recognition when reviewing contributions later
- **Always track contribution level** - helps understand impact when aggregating (Critical/Small/Medium)
- **Always include links** - work typically involves docs, PRs, tickets, code - capture the link
- **Use MISSING** - if info isn't provided, mark as "MISSING" rather than omitting the field
- **Fix typos** - improve clarity while keeping the user's original meaning
- **Derive categories when needed** - if project not specified, analyze work to determine team/org scope and OE/EE/general type
- **Think ahead** - these logs will be used to create holistic contribution views at year-end or project completion
- **Organize by project** - when you have multiple logs for the same project, create a dedicated file
- **Use folders for complex projects** - if sub-projects exist, break them into separate files
- **Avoid overview.md dumping** - only use overview.md for truly misc items; prefer derived categories
