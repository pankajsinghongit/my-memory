# Processing Work Contributions - Daily Work Log

**When to use**: Day-to-day work log - any work done on projects, tasks, or initiatives

**Purpose**: Capture daily work meaningfully so it can be aggregated later to create a holistic view of contributions at year-end, performance reviews, or project completion.

## Storage Location
- `personal-memory/work-contribution/overview.md` - For daily work logs when starting or for general work
- `personal-memory/work-contribution/[project-name].md` - For work specific to a major project
- `personal-memory/work-contribution/[project-name]/[sub-project].md` - For work on sub-projects
- `personal-memory/work-contribution/[YYYY-QQ]-contributions.md` - Optional: For quarterly organization

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
   - **overview.md**: General daily work or when just starting
   - **[project-name].md**: Work specific to a particular project
   - **[project-name]/[sub-project].md**: Work on specific sub-projects within a larger project
   - **Quarterly file**: Optional - if organizing by time period

4. **Follow the simple daily log template**:

```markdown
## [Date] - [Brief Work Description]

**Project**: [Project Name]
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

## Example 1: Simple Daily Work Log

**Inbox Entry:**
```markdown
## [2026-02-18] Fixed bug in payment service

Fixed the timeout issue in payment processing. The bug was causing transactions to fail after 30 seconds. Updated the timeout configuration and added retry logic.

Person: John Doe
Contribution: Small
PR: https://github.com/company/payment-service/pull/234
```

**Result in work-contribution/payment-platform.md:**
```markdown
## 2026-02-18 - Fixed timeout issue in payment processing

**Project**: Payment Platform
**Person(s) Involved**: John Doe
**Contribution Level**: Small
**Document/Link**: https://github.com/company/payment-service/pull/234

**Work Done**:
Fixed the timeout issue in payment processing. The bug was causing transactions to fail after 30 seconds. Updated the timeout configuration and added retry logic.
```

## Example 2: Critical Work with Missing Info

**Inbox Entry:**
```markdown
## [2026-02-18] Led design review for new analytics dashboard

Led the technical design review for the new analytics dashboard. Reviewed architecture proposals from 3 teams, identified scalability concerns, and recommended solutions. Meeting doc has all the details.
```

**Result in work-contribution/overview.md:**
```markdown
## 2026-02-18 - Led design review for new analytics dashboard

**Project**: Analytics Platform
**Person(s) Involved**: MISSING
**Contribution Level**: Critical
**Document/Link**: MISSING

**Work Done**:
Led the technical design review for the new analytics dashboard. Reviewed architecture proposals from 3 teams, identified scalability concerns, and recommended solutions. Meeting doc has all the details.
```

## Organization Strategy

**Use overview.md** for:
- General daily work that doesn't belong to a specific project
- When you're just starting and haven't established project files yet

**Create [project-name].md** when:
- You accumulate several work logs for the same project
- You want to track work on a specific initiative separately

**Create [project-name]/ folder** when:
- A project has distinct sub-projects or components
- Each sub-project needs separate tracking
- Example structure:
  ```
  personal-memory/work-contribution/
    ├── overview.md (general work)
    ├── payment-platform.md (dedicated project)
    └── analytics-platform/
        ├── data-pipeline.md (sub-project)
        ├── dashboard-ui.md (sub-project)
        └── reporting-api.md (sub-project)
  ```

**Optional quarterly files** (`2026-q1-contributions.md`):
- Use if you prefer time-based organization
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
- **Think ahead** - these logs will be used to create holistic contribution views at year-end or project completion
- **Organize by project** - when you have multiple logs for the same project, create a dedicated file
- **Use folders for complex projects** - if sub-projects exist, break them into separate files
