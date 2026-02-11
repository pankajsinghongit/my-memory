---
name: process-memory-inbox
description: Process unorganized items from inbox and organize them into the personal memory system
---

# process-memory-inbox

This skill implements the complete inbox processing workflow defined in the memory management rules. It takes unprocessed items from `personal-memory/inbox.md`, organizes them into appropriate locations in the `personal-memory/` folder structure, and maintains a complete audit trail.

## Purpose

- **Organize**: Move information from inbox to proper locations
- **Categorize**: Decide where each piece of information belongs
- **Archive**: Maintain complete audit trail of processed items
- **Maintain**: Keep inbox clean and organized
- **Update**: Keep the personal-memory-index.md current

## When to Use This Skill

Use this skill when the user says:
- "Process inbox"
- "Organize my inbox"
- "Clean up inbox"
- "Process my notes"
- "Organize captured information"

## Processing Workflow Overview

The complete workflow follows these 5 steps:

1. **Read** each item in `inbox.md`
2. **Decide** where it belongs
3. **Move** content to its proper location
4. **Archive** the entry to processed-inbox-audit
5. **Update** personal-memory-index.md if needed

## Detailed Steps

### 1. Read the Current Inbox

Start by reading all unprocessed items:

```
read_file: personal-memory/inbox.md
```

**What to Look For:**
- How many items are in the inbox?
- What types of information are present?
- Are there any urgent items (🔴)?
- Are there related items that could be grouped?

### 2. Check Existing Personal Memory Structure

Understand the current folder structure to make informed decisions:

```
list_files: personal-memory/
recursive: true
```

This shows:
- What folders already exist
- What files are in each folder
- Where similar information is already stored

### 3. Process Each Item Individually

For each inbox entry, follow this decision process:

#### A. Read and Understand the Item
- What is this information about?
- Why was it captured?
- Where does it logically belong?
- Is there an existing file it should be added to?
- Or does it need a new file?

#### B. Decide the Destination

**Decision Tree:**

1. **Check if a relevant folder exists:**
   - `bookmarks/` - URLs, links, web resources
   - `identity/` - Personal information, documents, family
   - `where-is-my-stuff/` - Item locations, organization
   - Other topic folders (if they exist)

2. **Check if a relevant file exists in that folder:**
   - If yes → Add to existing file
   - If no → Create new file

3. **If no relevant folder exists:**
   - Is this a new major category (5+ future items expected)?
     - Yes → Create new folder
     - No → Add to closest existing folder or create generic folder

**Naming Guidelines:**
- Files: `lowercase-with-hyphens.md`
- Folders: `lowercase-with-hyphens/`
- Be descriptive and searchable

#### C. Move the Content

**For Existing Files:**
Use `read_file` first, then `replace_in_file` to add content:

```markdown
# Existing Title

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD  ← Update this date

## Existing Section

Existing content...

## New Section (if needed)

Content from inbox entry...
```

**For New Files:**
Use `write_to_file` with proper structure:

```markdown
# Title

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD
**Tags**: #tag1 #tag2 #tag3

## Summary
Brief description of what this note contains.

## Content
[Content from inbox entry]

## References
- Links to sources (if from inbox)

## Next Actions
- [ ] Tasks or follow-ups (if applicable)
```

### 4. Archive to Processed Inbox Audit

**Critical Step**: This maintains complete audit trail.

#### A. Determine Current Year-Month
Use current date from environment_details to get format: `YYYY-MM` (e.g., `2026-02`)

#### B. Create or Open Audit File
Path: `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`
- Create `processed-inbox-audit/` folder if it doesn't exist
- Create the monthly file if it doesn't exist

#### C. Copy Complete Entry with Processing Metadata

**Format:**
```markdown
## [Original timestamp and title - UNCHANGED]
**Processed**: [YYYY-MM-DD HH:MM]
**Moved to**: personal-memory/path/to/file.md

[All original content from inbox.md - EXACTLY as-is]
[No changes, no summarizing]
[Everything identical to original]
```

**Important Rules:**
- Copy the ENTIRE entry from inbox.md EXACTLY as written
- Do NOT summarize or modify the content
- Do NOT change formatting
- Add metadata (Processed, Moved to) after heading
- Keep original timestamp in heading unchanged

### 5. Remove from Inbox

After archiving, remove the processed entry from `inbox.md`:
- Use `replace_in_file` to remove just that entry
- Keep the `# Inbox` header
- Preserve any remaining unprocessed entries
- Maintain proper spacing between remaining entries

### 6. Update Personal Memory Index (If Needed)

Update `personal-memory-index.md` if you:
- Created a new folder
- Created significant new files
- Made structural changes

**What to Update:**
- Directory structure section
- Content overview for affected folders
- Summary statistics (file count, last updated date)

### 7. Repeat for All Items

Continue processing each inbox item until:
- All items are processed, OR
- User asks to stop, OR
- You encounter ambiguous items that need user input

### 8. Inform User of Results

Provide a summary:
- Number of items processed
- What was created/updated
- Where information was organized
- Current inbox status
- Any items that need user clarification

## Special Processing Cases

### Case 1: Sensitive Personal Information
**Example**: PAN numbers, passwords, Aadhaar

**Action:**
- Store in `personal-memory/identity/personal-info.md` or similar secure location
- Use appropriate section headers
- Consider if it needs encryption (discuss with user)

### Case 2: Web Bookmarks and URLs
**Example**: PRFAQs, documentation links, articles

**Action:**
- Store in `personal-memory/bookmarks/`
- Organize by category (work-bookmarks.md, learning-bookmarks.md, etc.)
- Include URL in content with context

### Case 3: Family/Personal Information
**Example**: Family names, birthdays, contacts

**Action:**
- Store in `personal-memory/identity/`
- Create sections for different types (Family, Contacts, etc.)
- Keep organized and searchable

### Case 4: Ideas and Projects
**Example**: Ideas marked with 💡

**Action:**
- Consider creating `personal-memory/ideas/` if many exist
- Or add to `personal-memory/projects/`
- Preserve the emoji marker and next actions

### Case 5: Learning Notes
**Example**: Tutorial notes, course materials

**Action:**
- Create topic-specific folders if needed
- Or add to existing learning/technology folders
- Include sources and references

### Case 6: Multiple Related Items
**Action:**
- Process together if they share a topic
- May combine into single destination file
- Or create multiple files in same folder

### Case 7: Unclear Destination
**Action:**
- Ask user for clarification using `ask_followup_question`
- Don't guess if impact is significant
- Offer suggestions for where it could go

## Quality Checklist

Before completing inbox processing, verify:

### For Each Processed Item
- [ ] Content moved to appropriate location in personal-memory/
- [ ] Proper file naming conventions followed
- [ ] File structure includes metadata (Created, Last Updated)
- [ ] Complete entry archived to processed-inbox-audit/
- [ ] Archived entry includes Processed timestamp
- [ ] Archived entry includes "Moved to" reference
- [ ] Archived content is EXACTLY identical to original
- [ ] Entry removed from inbox.md

### For System Integrity
- [ ] Inbox.md maintains proper structure
- [ ] No entries lost or duplicated
- [ ] personal-memory-index.md updated if needed
- [ ] All new files follow naming conventions
- [ ] All new folders follow naming conventions
- [ ] Proper markdown formatting throughout

### For Audit Trail
- [ ] Processed-inbox-audit folder exists
- [ ] Monthly audit file exists (YYYY-MM format)
- [ ] All processed items archived with metadata
- [ ] Timestamps accurate
- [ ] "Moved to" paths accurate and complete

## Example Processing Session

### Before Processing:

**inbox.md:**
```markdown
# Inbox

## [2026-02-11 12:01] DLS Virtual Assistant PRFAQ

Amazon WorkDocs document containing the PRFAQ for DLS Virtual Assistant.

Source: https://amazon.awsapps.com/workdocs-amazon/...

## [2026-02-11 12:02] PAN Number

PAN Number: CSDGS8675r

## [2026-02-11 12:03] Wife's Name

Wife's name: Vyakhya
```

### Processing Actions:

**Item 1: DLS Virtual Assistant PRFAQ**
- Decision: Bookmark → work-related
- Action: Create/update `personal-memory/bookmarks/work-bookmarks.md`
- Archive to: `processed-inbox-audit/2026-02-processed-inbox-audit.md`

**Item 2: PAN Number**
- Decision: Personal identity information
- Action: Create/update `personal-memory/identity/personal-info.md`
- Archive to: `processed-inbox-audit/2026-02-processed-inbox-audit.md`

**Item 3: Wife's Name**
- Decision: Family information
- Action: Add to `personal-memory/identity/personal-info.md`
- Archive to: `processed-inbox-audit/2026-02-processed-inbox-audit.md`

### After Processing:

**inbox.md:**
```markdown
# Inbox
```

**personal-memory/bookmarks/work-bookmarks.md:**
```markdown
# Work Bookmarks

**Created**: 2026-02-11
**Last Updated**: 2026-02-11

## Projects & Documents

### DLS Virtual Assistant
- **PRFAQ Document**: [WorkDocs Link](https://amazon.aws...)
  - Press Release and FAQ for DLS Virtual Assistant project
  - **Added**: 2026-02-11
```

**personal-memory/identity/personal-info.md:**
```markdown
# Personal Information

**Created**: 2026-02-11
**Last Updated**: 2026-02-11

## Official Documents

### PAN Number
- **PAN**: CSDGS8675r

## Family

### Spouse
- **Name**: Vyakhya
```

**processed-inbox-audit/2026-02-processed-inbox-audit.md:**
```markdown
# Processed Inbox Audit - February 2026

## [2026-02-11 12:01] DLS Virtual Assistant PRFAQ
**Processed**: 2026-02-11 12:05
**Moved to**: personal-memory/bookmarks/work-bookmarks.md

Amazon WorkDocs document containing the PRFAQ for DLS Virtual Assistant.

Source: https://amazon.awsapps.com/workdocs-amazon/...

## [2026-02-11 12:02] PAN Number
**Processed**: 2026-02-11 12:05
**Moved to**: personal-memory/identity/personal-info.md

PAN Number: CSDGS8675r

## [2026-02-11 12:03] Wife's Name
**Processed**: 2026-02-11 12:05
**Moved to**: personal-memory/identity/personal-info.md

Wife's name: Vyakhya
```

**personal-memory-index.md:**
```markdown
# Personal Memory Index

...

## Directory Structure

**Last Updated**: February 11, 2026 12:05 PM

```
personal-memory/
├── inbox.md                        # Empty - all items processed
├── bookmarks/
│   └── work-bookmarks.md          # Work-related bookmarks
├── identity/
│   └── personal-info.md           # Personal information and family
└── where-is-my-stuff/
```

...

## Summary Statistics

- **Last Updated**: February 11, 2026 12:05 PM
- **Total Files**: 3 (inbox.md + 2 content files)
- **Inbox Status**: ✅ Empty (all items processed)
```

## Important Reminders

1. **Never Skip Archiving**: Every processed item MUST be archived
2. **Preserve Original Content**: Archive entries must be EXACTLY as originally captured
3. **Update Index**: Keep personal-memory-index.md current
4. **Maintain Structure**: Follow file and folder naming conventions
5. **Complete Audit Trail**: Include both "Processed" timestamp and "Moved to" path
6. **Clean Inbox**: Remove entries only AFTER they're archived
7. **Quality Over Speed**: Take time to organize properly
8. **Ask When Unclear**: Don't guess where important information belongs

## Error Handling

### If Inbox is Empty
- Inform user: "Your inbox is already empty! Great job staying organized."
- No processing needed

### If Personal-Memory Folders Don't Exist
- Create the standard folder structure:
  - `personal-memory/bookmarks/`
  - `personal-memory/identity/`
  - `personal-memory/where-is-my-stuff/`

### If Processed-Inbox-Audit Folder Doesn't Exist
- Create it: `processed-inbox-audit/`
- Create current month's file: `[YYYY-MM]-processed-inbox-audit.md`

### If Destination is Ambiguous
- Use `ask_followup_question` to clarify with user
- Provide suggestions: "This could go in [A] or [B]. Where would you prefer?"
- Don't make assumptions for important information

### If Files Fail to Update
- Read the file again to check current state
- Retry the operation
- Inform user if persistent issues occur

## Performance Tips

### For Large Inboxes (20+ items)
- Process in batches (5-10 items at a time)
- Group similar items together
- Update index once at the end instead of per-item
- Keep user informed of progress

### For Related Items
- Process together when they share a topic
- May create single destination file for multiple items
- Or create multiple files in same folder

### For Complex Items
- Take time to understand the content
- Create appropriate structure in destination file
- Include all context and references

## Success Criteria

Inbox processing is successful when:
1. ✅ All inbox items have been read and understood
2. ✅ Each item moved to appropriate location
3. ✅ All items archived with complete metadata
4. ✅ Inbox cleared of processed items
5. ✅ Personal-memory-index.md updated
6. ✅ Complete audit trail maintained
7. ✅ User informed of results
8. ✅ System remains organized and navigable

## Notes

- **Frequency**: Weekly processing prevents overwhelming backlog
- **Time Investment**: 30-60 minutes for weekly processing
- **Benefits**: Organized knowledge, findable information, complete history
- **Flexibility**: Adjust organization as needs evolve
- **Tool**: This is your primary organization tool

---

**Remember**: The inbox is temporary storage. Regular processing keeps your personal memory organized, searchable, and valuable. Every piece of information deserves a proper home!