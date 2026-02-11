# Personal Memory Management Rules

This document contains your personal rules and guidelines for managing your knowledge base. Customize these rules to fit your workflow and preferences.

## 📋 Table of Contents

- [Organization Rules](#organization-rules)
- [Naming Conventions](#naming-conventions)
- [Inbox Processing](#inbox-processing)
- [Content Guidelines](#content-guidelines)
- [Maintenance Schedule](#maintenance-schedule)
- [Custom Workflows](#custom-workflows)

---

## Organization Rules

### Folder Structure
Define how you organize different types of information:

**Example:**
- `technology/` - All tech-related notes (programming, tools, tutorials)
- `health/` - Health and wellness information
- `finance/` - Financial planning, investments, budgeting
- `projects/` - Ongoing projects (work and personal)
- `learnings/` - Daily learnings organized by year/month
- `reference/` - Quick reference materials and checklists

### Categorization Principles
- [ ] Keep folder depth to maximum 3-4 levels
- [ ] Create new top-level folders only when you have 5+ related items
- [ ] Use singular names for folders (e.g., `project/` not `projects/`)
- [ ] Group by topic first, then by time or project

---

## Naming Conventions

### Files
- **Format**: `lowercase-with-hyphens.md`
- **Date Format**: `YYYY-MM-DD` when including dates (e.g., `2026-02-11-meeting-notes.md`)
- **Descriptive**: Use clear, searchable names (e.g., `python-asyncio-basics.md` not `notes.md`)

### Folders
- **Format**: `lowercase-with-hyphens/`
- **Descriptive**: Clear purpose (e.g., `machine-learning/` not `ml/`)
- **Avoid**: Special characters, spaces, or abbreviations

### Examples
```
✅ Good:
- personal-memory/technology/python-asyncio-tutorial.md
- personal-memory/health/2026-02-fitness-goals.md
- personal-memory/projects/website-redesign/architecture-notes.md

❌ Bad:
- personal-memory/tech/Notes.md
- personal-memory/Health/2_11_26-fitness.md
- personal-memory/projects/Website Redesign/arch notes.txt
```

---

## Inbox Processing

### Processing Schedule
Define when you review and organize your inbox:

- **Daily**: Quick 5-minute scan (optional)
- **Weekly**: Full inbox processing session
  - **Day**: Sunday evening
  - **Duration**: 30-60 minutes
- **Monthly**: Deep review and reorganization

### Processing Workflow

1. **Read** each item in `inbox.md`
2. **Decide** where it belongs:
   - Create new note in appropriate folder
   - Add to existing note
   - Delete if no longer relevant (rare)
3. **Move** content to its proper location in `personal-memory/`
4. **Archive** the inbox entry:
   - **Copy the ENTIRE entry from inbox.md to `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`** (complete, unmodified)
   - Use the current year-month for the filename (e.g., `processed-inbox-audit/2026-02-processed-inbox-audit.md` for February 2026)
   - Create the `processed-inbox-audit/` folder if it doesn't exist
   - Add `**Processed**: [YYYY-MM-DD HH:MM]` timestamp immediately after the heading
   - Add `**Moved to`: path/to/file.md` reference on the next line
   - Keep all original content exactly as it was
   - Delete the entry from `inbox.md`
5. **Update** `personal-memory-index.md` if you added new folders

### Quick Processing Check
```bash
# Count unprocessed items in inbox
wc -l personal-memory/inbox.md

# Count how many heading lines (items) in inbox
grep -c "^## \[" personal-memory/inbox.md

# View today's processed items (current month)
CURRENT_MONTH=$(date +%Y-%m)
grep "Processed.*$(date +%Y-%m-%d)" processed-inbox-audit/${CURRENT_MONTH}-processed-inbox-audit.md

# View all processed items this month
cat processed-inbox-audit/${CURRENT_MONTH}-processed-inbox-audit.md
```

### Inbox Rules
- **ALL new information must first go to inbox.md**
- Every item MUST include:
  - Timestamp: `[YYYY-MM-DD HH:MM]` or `[YYYY-MM-DD]`
- **inbox.md contains ONLY unprocessed items**
- Once processed, items are moved to monthly audit files in `processed-inbox-audit/` folder
  - Format: `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`
  - Example: `processed-inbox-audit/2026-02-processed-inbox-audit.md` for February 2026
  - Create the folder and/or file if it doesn't exist
- Never let inbox exceed 50 items
- Mark urgent items with 🔴 emoji
- Mark ideas worth exploring with 💡 emoji

### Inbox Entry Format
```markdown
## [2026-02-11 10:15] Topic Title

Content of the captured information...

Source: [URL or reference if applicable]
```

### Processed Audit Format
When moving items to `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`:
1. Determine the current year-month (e.g., `2026-02` for February 2026)
2. Create `processed-inbox-audit/` folder if it doesn't exist
3. Open or create the file `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`
4. Copy the ENTIRE entry from inbox.md EXACTLY as-is
5. Add `**Processed**: [YYYY-MM-DD HH:MM]` timestamp on a new line after the heading
6. Add `**Moved to**: path/to/file.md` reference on the next line
7. Keep all original content unchanged below that

**Example - File: `processed-inbox-audit/2026-02-processed-inbox-audit.md`**
```markdown
## [Original timestamp and title stay the same]
**Processed**: [2026-02-13 09:30]           ← ADD THIS
**Moved to**: personal-memory/path/file.md  ← ADD THIS

[All original content copied EXACTLY as-is]
[No changes, no summarizing]
[Everything stays identical]
```

**Important**: The original content must remain identical - do not summarize or change anything from the inbox entry.

---

## Content Guidelines

### Note Structure
Every note should include:

```markdown
# Title

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD
**Tags**: #tag1 #tag2 #tag3

## Summary
Brief description of what this note contains.

## Content
[Your detailed notes here]

## References
- Links to sources
- Related notes in your knowledge base

## Next Actions
- [ ] Tasks or follow-ups related to this note
```

### Quality Standards
- [ ] Use proper markdown formatting
- [ ] Include sources and references
- [ ] Add creation date to all notes
- [ ] Use headers for better organization
- [ ] Include examples where applicable
- [ ] Keep notes focused on single topic

### Linking Between Notes
- Use relative links: `[Related Note](../other-topic/related-note.md)`
- Create a "See Also" section for related notes
- Use backlinks to track connections

---

## Maintenance Schedule

### Daily
- [ ] Capture new information in `inbox.md`
- [ ] Quick scan of recent notes

### Weekly (Sunday Evening)
- [ ] Process inbox completely
- [ ] Review week's learning
- [ ] Update `personal-memory-index.md`
- [ ] Check for duplicate information

### Monthly (First Sunday)
- [ ] Review folder structure
- [ ] Consolidate related notes
- [ ] Archive outdated information
- [ ] Update this rules document
- [ ] Commit changes to Git

### Quarterly
- [ ] Deep reorganization if needed
- [ ] Review and refine tagging system
- [ ] Backup to external drive/cloud
- [ ] Evaluate what's working and what's not

---

## Custom Workflows

### For Learning New Topics
1. Capture quick notes in `inbox.md` with timestamp
2. Process inbox regularly following the workflow above
3. Create dedicated folder when you have 3+ notes on the same topic
4. Create `overview.md` as entry point for the topic
5. Link related concepts together
6. Review and summarize monthly

### For Project Notes
1. Create folder: `projects/project-name/`
2. Include: `README.md`, `notes.md`, `decisions.md`, `resources.md`
3. Update weekly during active work
4. Archive when complete to `projects/archived/`

### For Daily Learning
1. Quick capture in `inbox.md` throughout the day
2. Weekly transfer to `learnings/YYYY/MM-month-name.md`
3. Monthly review to identify patterns
4. Quarterly distillation into topic-specific notes

### For Web Clippings
1. Save to `inbox.md` with timestamp and source URL
2. Add brief context about why it's interesting
3. Process within 48 hours - extract key insights and create proper note
4. Move to appropriate topic folder in `personal-memory/`
5. Archive the inbox entry to `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md` following the standard workflow

---

## Personal Customizations

### My Priorities
Add your specific priorities and focus areas:

- Priority 1: 
- Priority 2: 
- Priority 3: 

### Special Categories
Define any special handling for certain types of information:

- **Quotes**: Store in `reference/quotes.md`
- **Recipes**: Store in `personal/recipes/`
- **Book Notes**: Store in `learning/books/book-title.md`

### Tools I Use
- **Editor**: VS Code
- **Sync**: Git + GitHub
- **Mobile Capture**: 
- **Search**: ripgrep (rg)

---

## Review and Updates

**Last Reviewed**: [Add date when you review these rules]

**Next Review**: [Schedule next review date]

### Changelog
Track changes to your management rules:

- **2026-02-11**: Initial creation of management rules
- Add your updates here as you refine your system

---

## Notes to Self

Use this space for reminders and reflections about your system:

- What's working well?
- What needs improvement?
- Ideas to try?
- Lessons learned?

---

**Remember**: These rules are meant to serve you, not constrain you. Adjust them as needed to fit your evolving needs!