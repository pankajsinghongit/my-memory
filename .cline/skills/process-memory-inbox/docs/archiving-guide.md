# Archiving Guide

Complete process for archiving processed inbox items to maintain audit trail.

## Purpose

Every processed inbox item must be archived to:
- **Preserve history**: Never lose captured information
- **Enable review**: See what was processed and when
- **Support recovery**: Restore items if needed
- **Track patterns**: Understand information flow over time

## Archive Location

All processed items are archived to:
```
processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md
```

**Monthly files**: One file per month (e.g., `2026-02-processed-inbox-audit.md`)

## Step-by-Step Process

### 1. Determine Current Month

Get current date from `environment_details`:
- Format: `YYYY-MM` (e.g., `2026-02`)
- Use this for the archive filename

### 2. Ensure Archive Structure Exists

**Check if folder exists:**
```
list_files: processed-inbox-audit/
```

**If folder doesn't exist**, create it:
```
write_to_file: processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md
```

**If folder exists but monthly file doesn't**, create the monthly file with header:
```markdown
# Processed Inbox Audit - [Month Year]

This file contains all inbox items processed during [Month Year].

---
```

### 3. Copy Entry with Metadata

**Critical**: Archive the COMPLETE original entry, unchanged.

#### Template Format

```markdown
## [Original timestamp and title - KEEP UNCHANGED]
**Processed**: [YYYY-MM-DD HH:MM]
**Moved to**: personal-memory/path/to/destination.md

[EXACT copy of all original content from inbox]
[Include everything - links, formatting, notes]
[Do NOT modify, summarize, or change anything]

---
```

#### Example

Original inbox entry:
```markdown
## 2026-02-15 14:30 - Python Decorators Tutorial

Found excellent tutorial on Python decorators:
https://realpython.com/primer-on-python-decorators/

Key points:
- Functions are first-class objects
- Inner functions can access outer scope
- Decorators wrap functions

TODO: Practice with examples
```

Archived entry:
```markdown
## 2026-02-15 14:30 - Python Decorators Tutorial
**Processed**: 2026-02-17 18:25
**Moved to**: personal-memory/technology/python/learning-resources.md

Found excellent tutorial on Python decorators:
https://realpython.com/primer-on-python-decorators/

Key points:
- Functions are first-class objects
- Inner functions can access outer scope
- Decorators wrap functions

TODO: Practice with examples

---
```

### 4. Archiving Rules

#### Must Do
- ✅ Copy ENTIRE entry exactly as written
- ✅ Keep original timestamp in heading unchanged
- ✅ Add **Processed** timestamp (current date/time)
- ✅ Add **Moved to** with full path
- ✅ Include separator `---` after entry

#### Must NOT Do
- ❌ Summarize or paraphrase content
- ❌ Change formatting or structure
- ❌ Modify links or text
- ❌ Remove any part of the original
- ❌ Change the original timestamp

### 5. Using Tools

**To append to archive file:**

```
replace_in_file: processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md
```

Use a SEARCH/REPLACE block to add at the end:

```markdown
------- SEARCH
---

=======
---

## [New archived entry]
**Processed**: [timestamp]
**Moved to**: [path]

[Content...]

---

+++++++ REPLACE
```

## Archive File Structure

### Monthly File Format

```markdown
# Processed Inbox Audit - February 2026

This file contains all inbox items processed during February 2026.

---

## 2026-02-01 09:15 - First Item
**Processed**: 2026-02-17 10:30
**Moved to**: personal-memory/folder/file.md

Content of first item...

---

## 2026-02-05 14:20 - Second Item
**Processed**: 2026-02-17 10:35
**Moved to**: personal-memory/another/file.md

Content of second item...

---

## 2026-02-10 16:45 - Third Item
**Processed**: 2026-02-17 10:40
**Moved to**: personal-memory/somewhere/else.md

Content of third item...

---
```

## Quality Checks

Before removing item from inbox, verify archive entry has:

- [ ] Original heading with timestamp unchanged
- [ ] **Processed** metadata with current date/time
- [ ] **Moved to** metadata with complete path
- [ ] All original content copied exactly
- [ ] Proper separator (`---`) after entry
- [ ] Entry added to correct monthly file
- [ ] File is in `processed-inbox-audit/` folder

## Common Mistakes to Avoid

### ❌ Mistake 1: Summarizing Content
```markdown
## 2026-02-15 14:30 - Python Tutorial
**Processed**: 2026-02-17 18:25
**Moved to**: personal-memory/technology/python.md

Tutorial about decorators
```
**Problem**: Lost all the details, links, and notes.

### ✅ Correct: Copy Everything
```markdown
## 2026-02-15 14:30 - Python Tutorial
**Processed**: 2026-02-17 18:25
**Moved to**: personal-memory/technology/python.md

Found excellent tutorial on Python decorators:
https://realpython.com/primer-on-python-decorators/

Key points:
- Functions are first-class objects
- Inner functions can access outer scope
- Decorators wrap functions

TODO: Practice with examples
```

### ❌ Mistake 2: Wrong Archive Path
```markdown
**Moved to**: python.md
```
**Problem**: Path is incomplete, can't find the file later.

### ✅ Correct: Full Path
```markdown
**Moved to**: personal-memory/technology/python/learning-resources.md
```

### ❌ Mistake 3: Modifying Timestamp
```markdown
## 2026-02-17 18:25 - Python Tutorial
```
**Problem**: Changed original capture timestamp, loses historical context.

### ✅ Correct: Keep Original
```markdown
## 2026-02-15 14:30 - Python Tutorial
**Processed**: 2026-02-17 18:25
```

## Archive Maintenance

### Monthly Files
- One file per month keeps archives organized
- Easy to find historical items by date
- Prevents files from becoming too large

### Retention
- Keep all archive files indefinitely
- They are the permanent record
- Disk space is cheap, lost information is not

### Review
- Periodically review archives to:
  - Verify processing patterns
  - Identify information gaps
  - Improve categorization over time

## Recovery Process

If you need to restore an archived item:

1. Find the archived entry in `processed-inbox-audit/`
2. Copy the content (excluding Processed/Moved to metadata)
3. Paste back into `personal-memory/inbox.md`
4. Re-process it to move to different location

## Success Criteria

Archiving is complete when:
- ✅ Entry exists in monthly audit file
- ✅ Contains all original content exactly
- ✅ Has Processed timestamp
- ✅ Has Moved to path
- ✅ Monthly file is properly formatted
- ✅ Entry can be found and read later

---

**Remember**: Archiving is non-negotiable. Every processed item must be archived before removal from inbox. This is your safety net and historical record.