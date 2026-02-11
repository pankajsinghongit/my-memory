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
- **Maintain**: Keep inbox clean and organized by processing items one by one sequentially
- **Update**: Keep the personal-memory-index.md current

## When to Use This Skill

Use this skill when the user says:
- "Process inbox"
- "Organize my inbox"
- "Clean up inbox"
- "Process my notes"
- "Organize captured information"

## Processing Workflow Overview

**Important**: This skill processes inbox items one by one sequentially. Each item is fully processed before moving to the next item.

The workflow for processing each item follows these 5 steps:

1. **Read** the next unprocessed item in `inbox.md`
2. **Decide** where it belongs
3. **Move** content to its proper location
4. **Archive** the entry to processed-inbox-audit
5. **Update** personal-memory-index.md if needed

## Detailed Steps

### 1. Read the Current Inbox

Start by reading the inbox to identify items to process:

```
read_file: personal-memory/inbox.md
```

**What to Look For:**
- How many items are in the inbox?
- What items need to be processed?
- Are there any urgent items (🔴)?
- Process items one by one, starting with urgent items if marked

### 2. Check Existing Personal Memory Structure

Understand the current folder structure to make informed decisions. You have two approaches:

**Approach 1: Read the Index (Recommended)**
```
read_file: personal-memory-index.md
```

This provides a comprehensive overview of the folder structure, what each folder contains, and the purpose of each category. This is the quickest way to understand the organization.

**Approach 2: List Files Directly**

```
list_files: personal-memory/
recursive: true
```

This shows the actual file structure. Use this if you need to see exact file names or the index is out of date.

**What This Reveals:**
- What folders already exist
- What files are in each folder
- Where similar information is already stored
- Current organizational patterns

### 3. Process Each Item One by One

For each inbox entry, follow this decision process:

#### A. Read and Understand the Item
- What is this information about?
- Why was it captured?
- Where does it logically belong?
- Is there an existing file it should be added to?
- Or does it need a new file?

**File Size Consideration:**
- If adding to an existing file, check if it's becoming too large (~500 lines)
- If the file is growing large or covering too many subtopics, consider breaking it up (see "Case 7: Large File Reorganization")

#### B. Decide the Destination

**Decision Tree:**

1. **Check if a relevant folder exists** (refer to personal-memory-index.md):
   - Review the "Directory Structure" section in personal-memory-index.md
   - Check the "Content Overview" to understand what each folder contains
   - Common folders include:
     - `bookmarks/` - URLs, links, web resources
     - `identity/` - Personal information, documents, family
     - `where-is-my-stuff/` - Item locations, organization
   - Look for topic-specific folders that match the inbox item
   - Consider multi-level folders (e.g., `technology/python/` for Python notes)

2. **Check if a relevant file exists in that folder:**
   - If yes → Add to existing file
   - If no → Create new file
   - If file is becoming too large, consider breaking it up (see Case 7 below)

3. **If no relevant folder exists:**
   - Is this a new major category (5+ future items expected)?
     - Yes → Create new folder
     - No → Add to closest existing folder or create generic folder

**Multi-Level Organization:**
- Personal memory supports flexible multi-level folder structures (3-5 levels recommended)
- You can create subfolders within existing folders as content grows
- Example progression: `technology/` → `technology/python/` → `technology/python/frameworks/`
- Start simple, deepen hierarchy as needed

**File Growth Management:**
- If a destination file is growing beyond ~500 lines or covers multiple subtopics, consider breaking it up
- See "Case 7: Large File Reorganization" in Special Processing Cases for guidance

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

#### D. File Growth Management (Optional During Processing)

If you notice a file is becoming too large or complex during processing, you can proactively reorganize it:

**When to Consider:**
- File exceeds ~500 lines
- File covers multiple distinct subtopics
- Related inbox items suggest a growing area
- File structure is becoming hard to navigate

**How to Break Up a File:**

1. **Create a folder** with the same name as the file:
   - Example: `python-notes.md` → `python/` folder

2. **Move content** into multiple focused files:
   - Example: `python/basics.md`, `python/advanced.md`, `python/frameworks.md`

3. **Add an overview file**:
   - Create `python/overview.md` or `python/README.md`
   - Link to the other files
   - Provide a summary of the topic

4. **Update references**:
   - Check if other files link to the old file
   - Update links to point to new locations

5. **Archive the old file** (optional):
   - You can keep it for reference or delete it

**Example:**
```markdown
Before:
personal-memory/
└── python-notes.md (600 lines, covering basics, async, web frameworks)

After:
personal-memory/
└── python/
    ├── overview.md          # Links to other files, provides summary
    ├── basics.md            # Core Python concepts
    ├── async-programming.md # Async/await patterns
    └── web-frameworks.md    # Django, Flask, etc.
```

**Note:** This step is optional during inbox processing. You can:
- Reorganize proactively if you see the need
- Or note it for future reorganization during monthly maintenance
- Or continue adding to large files and reorganize later

Use your judgment based on the content and user's needs.

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

### 7. Continue to Next Item

After successfully processing one item:

- Move to the next unprocessed item in the inbox
- Repeat steps 3-6 for the next item
- Continue until all items are processed or user asks to stop

### 8. Inform User of Results

Provide a summary after all items are processed:
- Number of items processed
- What was created/updated
- Where information was organized
- Current inbox status (how many items remain)
- Any follow-up actions needed

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

### Case 6: Unclear Destination
**Action:**
- Ask user for clarification using `ask_followup_question`
- Don't guess if impact is significant
- Offer suggestions for where it could go

### Case 7: Large File Reorganization
**Example**: File has grown to 600+ lines and covers multiple subtopics

**Action:**
- **Proactive Approach** (during processing):
  - Create a folder to replace the file
  - Break content into focused files within the folder
  - Add overview.md to tie concepts together
  - Update personal-memory-index.md
  - Inform user of the reorganization

- **Deferred Approach**:
  - Continue adding to the file
  - Note in processing summary that reorganization may be helpful
  - User can reorganize during monthly maintenance

**Example:**
- File: `technology/python-notes.md` (600 lines)
- Reorganize to: `technology/python/` folder with multiple files
- Add: `technology/python/overview.md` as entry point

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

### Processing Actions (One by One):

**Item 1: DLS Virtual Assistant PRFAQ**
- Decision: Bookmark → work-related
- Action: Create/update `personal-memory/bookmarks/work-bookmarks.md`
- Archive to: `processed-inbox-audit/2026-02-processed-inbox-audit.md`
- **Continue to next item**

**Item 2: PAN Number**
- Decision: Personal identity information
- Action: Create/update `personal-memory/identity/personal-info.md`
- Archive to: `processed-inbox-audit/2026-02-processed-inbox-audit.md`
- **Continue to next item**

**Item 3: Wife's Name**
- Decision: Family information
- Action: Add to `personal-memory/identity/personal-info.md`
- Archive to: `processed-inbox-audit/2026-02-processed-inbox-audit.md`
- **All items processed**

### After Processing (All Items):

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
**Processed**: 2026-02-11 12:06
**Moved to**: personal-memory/identity/personal-info.md

PAN Number: CSDGS8675r

## [2026-02-11 12:03] Wife's Name
**Processed**: 2026-02-11 12:07
**Moved to**: personal-memory/identity/personal-info.md

Wife's name: Vyakhya
```

**User is informed:**
- "Processed 3 items successfully"
- "Created/updated: personal-memory/bookmarks/work-bookmarks.md"
- "Created/updated: personal-memory/identity/personal-info.md"
- "Inbox is now empty"
- "All items have been archived to processed-inbox-audit/2026-02-processed-inbox-audit.md"

## Important Reminders

1. **Process One by One**: Process each item individually and sequentially
2. **Never Skip Archiving**: Every processed item MUST be archived
3. **Preserve Original Content**: Archive entries must be EXACTLY as originally captured
4. **Update Index**: Keep personal-memory-index.md current
5. **Maintain Structure**: Follow file and folder naming conventions
6. **Complete Audit Trail**: Include both "Processed" timestamp and "Moved to" path
7. **Clean Inbox**: Remove entries only AFTER they're archived
8. **Quality Over Speed**: Take time to organize properly
9. **Ask When Unclear**: Don't guess where important information belongs

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
- Provide suggestions for where it could go
- Don't make assumptions for important information

### If Files Fail to Update
- Read the file again to check current state
- Retry the operation
- Inform user if persistent issues occur

## Performance Tips

### For Large Inboxes
- Process items one by one sequentially
- Each item gets full attention before moving to next
- User can stop processing at any time
- Prioritize urgent items (marked with 🔴) first

### For Complex Items
- Take time to understand the content
- Create appropriate structure in destination file
- Include all context and references
- Don't rush - one by one ensures quality

## Success Criteria

Inbox processing is successful when:
1. ✅ All inbox items have been read and understood
2. ✅ Each item is moved to appropriate location
3. ✅ Each item is archived with complete metadata
4. ✅ Each item is removed from inbox after archiving
5. ✅ Personal-memory-index.md updated as needed
6. ✅ Complete audit trail maintained
7. ✅ User informed of the results
8. ✅ Inbox is clean and organized

## Notes

- **Sequential Processing**: Items are processed one by one in order
- **No Batching**: Each item is fully processed before moving to the next
- **Frequency**: Regular processing prevents overwhelming backlog
- **Benefits**: Organized knowledge, findable information, complete history
- **Flexibility**: Adjust organization as needs evolve
- **Quality Focus**: Processing items one by one ensures careful organization

---

**Remember**: The inbox is temporary storage. Regular processing keeps your personal memory organized, searchable, and valuable. Items are processed one by one sequentially for best results!