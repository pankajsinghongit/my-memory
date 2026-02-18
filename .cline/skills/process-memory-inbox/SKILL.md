---
name: process-memory-inbox
description: Process unorganized items from inbox and organize them into the personal memory system
---

# process-memory-inbox

Process unprocessed items from `personal-memory/inbox.md`, organize them into appropriate locations, and maintain a complete audit trail.

## Purpose

- **Organize**: Move information from inbox to proper locations
- **Categorize**: Decide where each piece of information belongs
- **Archive**: Maintain complete audit trail of processed items
- **Maintain**: Keep inbox clean and organized

## When to Use This Skill

Use this skill when the user says:
- "Process inbox"
- "Organize my inbox"
- "Clean up inbox"
- "Process my notes"
- "Organize captured information"

## Core Workflow

**Important**: Process inbox items **one by one sequentially**. Each item is fully processed before moving to the next.

### Step-by-Step Process

For each inbox item:

1. **Read** → `read_file: personal-memory/inbox.md`
   - Identify next unprocessed item
   - Prioritize urgent items (🔴) if present

2. **Understand Context** → Read `personal-memory-index.md`
   - Review existing folder structure
   - Understand current organization patterns
   - Identify where similar content lives

3. **Initial Destination Decision** → See **[Decision Guide](./docs/decision-guide.md)**
   - Analyze the inbox item content
   - Determine likely target folder category (e.g., work-contribution, bookmarks, personal)
   - This is a preliminary decision to identify which folder rules to check
   - Don't finalize file name yet - rules may affect naming conventions

4. **Check Folder Rules** → Systematically discover and read all applicable rules
   
   **Step 4a: List all rule files in hierarchy using search_files tool**
   - Now that target folder is identified, use `search_files` to find all `memory-management-rule.md` files:
     ```
     search_files:
       path: personal-memory
       regex: memory-management-rule\.md$
       file_pattern: memory-management-rule.md
     ```
   - Filter results to only include files in the hierarchy from root to target:
     1. `personal-memory/memory-management-rule.md` (root - always exists)
     2. `personal-memory/work-contribution/memory-management-rule.md` (if in results)
     3. `personal-memory/work-contribution/projects/memory-management-rule.md` (if in results)
   - Example: For target `personal-memory/work-contribution/`, only include files in paths:
     * `personal-memory/` (root)
     * `personal-memory/work-contribution/` (target)
     * Exclude: `personal-memory/bookmarks/memory-management-rule.md` (different branch)
   
   **Step 4b: Read rules in order of precedence (lowest to highest)**
   - Start with root: Read `personal-memory/memory-management-rule.md`
   - Then parent folders: Read each parent folder's rules (if they exist)
   - Finally target folder: Read target folder's rules (if exists)
   - Build comprehensive understanding as you go:
     * Note general rules from root
     * Note any overrides or additions from parent folders
     * Note most specific rules from target folder
   
   **Step 4c: Apply rules with correct precedence**
   - Most specific (closest to target) rules override general rules
   - Look for: naming conventions, file structure, required sections, processing workflows
   - Example hierarchy:
     ```
     personal-memory/memory-management-rule.md           (GENERAL - applies to all)
       ↓ can be overridden by ↓
     personal-memory/work-contribution/memory-management-rule.md  (MORE SPECIFIC)
       ↓ can be overridden by ↓
     personal-memory/work-contribution/projects/memory-management-rule.md (MOST SPECIFIC)
     ```

5. **Finalize Destination** → Apply discovered rules
   - Determine exact target folder and file
   - Apply naming conventions from rules (general + folder-specific)
   - Determine file structure requirements
   - Create new folder/file if needed following rules

6. **Move Content** → Check content type:
   - **Bookmarks/URLs?** → See **[Bookmarks Guide](./docs/bookmarks.md)**
   - **Work contribution/log?** → See **[Work Contributions Guide](./docs/work-contribution.md)**
   - **Personal info?** → See **[Personal Info Guide](./docs/identity.md)**
   - **General content?** → See **[File Templates Guide](./docs/file-templates.md)**
   - Add to existing file OR create new file
   - Use proper markdown structure

7. **Archive** → See **[Archiving Guide](./docs/archiving-guide.md)**
   - Copy complete entry to `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`
   - Add processing metadata (Processed date, Moved to path)
   - Preserve original content exactly as-is

8. **Remove from Inbox** → `replace_in_file: personal-memory/inbox.md`
   - Delete the processed entry
   - Preserve remaining unprocessed entries

9. **Update Index** (if needed) → See **[Updating Index Guide](./docs/updating-index.md)**
   - Read the entire `personal-memory-index.md` file to understand its structure
   - Make ALL appropriate changes to keep it accurate and complete
   - Review thoroughly to ensure nothing was missed

10. **Continue** → Move to next item
   - Repeat steps 1-9 for each inbox item
   - Stop when all items processed or user requests

### Final Step

**Inform User** of results:
- Number of items processed
- What was created/updated
- Where information was organized
- Current inbox status

## Specialized Situations

For specific types of content, reference these guides:

- **[Decision Guide](./docs/decision-guide.md)** - How to categorize and decide destinations
- **[File Templates](./docs/file-templates.md)** - Proper file structure and formatting
- **[Archiving Guide](./docs/archiving-guide.md)** - Complete archiving process
- **[Updating Index Guide](./docs/updating-index.md)** - How to properly update all sections of the memory index
- **[New Folder Creation](./docs/new-folder-creation.md)** - When and how to create folders
- **[Web Bookmarks](./docs/bookmarks.md)** - Processing URLs and documentation
- **[Work Contributions](./docs/work-contribution.md)** - Work log, Career achievements and projects deliveries
- **[Personal Info](./docs/identity.md)** - Documents, family, contacts
- **[File Reorganization](./docs/file-reorganization.md)** - Breaking up large files

## Quality Standards

Each processed item must have:
- ✅ Content moved to appropriate location
- ✅ Complete entry archived with metadata
- ✅ Entry removed from inbox
- ✅ Index updated if structural changes made

## Error Handling

| Situation | Action |
|-----------|--------|
| Inbox is empty | Inform user, no processing needed |
| Folders don't exist | Create standard structure (bookmarks/, identity/, etc.) |
| Destination unclear | Use `ask_followup_question` to clarify |
| File update fails | Read file again, retry operation |

## Key Principles

1. **Sequential Processing** - One item at a time, fully complete before next
2. **Never Skip Archiving** - Every item MUST be archived before removal
3. **Preserve Originals** - Archive exactly as captured, no modifications
4. **Quality Over Speed** - Take time to organize properly
5. **Ask When Unclear** - Don't guess where important information belongs

---

**Remember**: The inbox is temporary storage. Regular processing keeps your personal memory organized and valuable!