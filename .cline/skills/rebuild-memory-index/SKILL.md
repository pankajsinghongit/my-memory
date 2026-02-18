# rebuild-memory-index

This skill rebuilds the `personal-memory-index.md` file from scratch by scanning the actual filesystem and updating all sections to reflect the current state of the personal memory system.

## Purpose

- **Rebuild**: Regenerate the complete memory index from the current filesystem state
- **Verify**: Ensure the index accurately reflects all folders and files
- **Update**: Refresh all sections including directory structure and content overview
- **Maintain**: Keep the index as the single source of truth for memory organization

## When to Use This Skill

Use this skill when the user says:
- "Rebuild the memory index"
- "Regenerate the index"
- "Update the complete index"
- "Refresh the memory index"
- "Scan and rebuild the index"
- Or when you notice the index is significantly out of sync with the filesystem

## Core Workflow

### Step 1: Scan the Filesystem
Use `list_files` tool to recursively scan the `personal-memory/` directory to get the complete current state.

```
list_files:
  path: personal-memory/
  recursive: true
```

### Step 2: Read Current Index
Read the existing `personal-memory-index.md` to preserve the format and structure.

```
read_file: personal-memory-index.md
```

### Step 3: Analyze and Organize
Organize the scanned files and folders into:
- Directory tree structure
- Content overview by category

**Key Analysis Tasks:**
1. **File mapping**: Map each folder to its contained files for Content Overview section
2. **Structure analysis**: Understand the folder hierarchy for proper tree generation

### Step 4: Generate Directory Structure
Create the ASCII tree structure showing:
- All folders with descriptions
- All files with brief descriptions
- Proper indentation (use 4 spaces per level or `├──`, `└──`, `│` characters)
- Note about subfolder support at the bottom

**Format:**
```
personal-memory/
├── inbox.md                        # Unprocessed information waiting to be organized
├── folder-name/                    # Folder description
│   ├── file1.md                   # File description
│   └── file2.md                   # File description
└── another-folder/                # Another folder description
    └── subfolder/                 # Subfolder description
        └── file.md                # File in subfolder

Note: Folders can contain subfolders as content grows (up to 3-5 levels deep)
```

### Step 5: Generate Content Overview
For each folder in `personal-memory/`, create a section with:

```markdown
### folder-name
**What's Here**: [Brief description of folder contents]
**Purpose**: [Why this folder exists and what it tracks]
**Files**:
- `file1.md` - Brief description with key topics
- `file2.md` - Brief description with key topics
```

**How to generate descriptions:**
- **Read each file** to understand its content
- **Summarize** the key topics or information it contains
- **Keep descriptions concise** - one line per file
- **Include examples** in parentheses when helpful

### Step 6: Update the Index File
Use `replace_in_file` to update each major section:
1. Directory Structure section
2. Content Overview section (each folder separately if needed)

**Critical Rules:**
- Preserve the document structure and formatting
- Keep all explanatory text and guidance sections
- Only update the data sections (Directory Structure and Content Overview)
- Maintain consistent markdown formatting
- Do NOT add timestamps, statistics, or counts

### Step 7: Verify and Confirm
After updating:
1. Confirm all sections were updated successfully
2. Report summary of changes to user:
   - Folders and files that were updated
   - Any structural changes observed

## Important Guidelines

### Reading Files for Descriptions
When generating the Content Overview:
- **DO read** files to get accurate descriptions
- **Keep descriptions brief** - focus on key topics/content
- **Include examples** in parentheses when helpful
- **Avoid reading very large files** completely - scan the beginning/structure
- **For work contributions**: Mention project names and types of contributions
- **For bookmarks**: Mention types of resources or tools
- **For personal files**: Mention what they track or contain

### Handling Special Cases

**Empty Folders:**
- Include in directory structure with "(empty)" notation
- Note in Content Overview that folder exists but has no files yet

**Large Numbers of Files:**
- In directory structure: Show all files or use `...` for very large folders
- In Content Overview: Summarize file categories if more than 10 files

**Nested Structures:**
- Show full tree in Directory Structure
- In Content Overview, group by subfolder if helpful
- Example: "folder/subfolder1/ - Description" and "folder/subfolder2/ - Description"

**Project Files with Dates:**
- Recognize the `project-YYYY-MM-name` pattern
- In descriptions, mention the project start date if relevant
- Example: "DLS Manager Approval Service project (started Feb 2026)"

## Quality Checklist

Before completing, verify:
- [ ] All folders in filesystem are in Directory Structure
- [ ] All files are accounted for
- [ ] Content Overview has entry for each folder
- [ ] File descriptions are accurate and helpful
- [ ] Markdown formatting is consistent
- [ ] No information was lost from original index

## Example Workflow

1. User requests: "Rebuild the memory index"
2. Scan `personal-memory/` recursively
3. Read current `personal-memory-index.md`
4. Read relevant files to understand content
5. Generate new Directory Structure with all current folders/files
6. Generate Content Overview with accurate descriptions
7. Update the index file section by section
8. Confirm success and report summary

## Error Handling

| Situation | Action |
|-----------|--------|
| Cannot scan directory | Report error, ask user to verify path |
| File read fails | Use generic description, note in output |
| Index file not found | Inform user, suggest creating from template |
| Formatting issues | Preserve as much as possible, report issues |

## Success Criteria

The skill is successful when:
1. ✅ Index file is updated with current filesystem state
2. ✅ All sections are accurate and complete
3. ✅ Descriptions are helpful and informative
4. ✅ User receives clear summary of changes

---

**Remember**: The memory index is the map to your knowledge. A complete, accurate rebuild ensures you can always find what you need!

---

IMPORTANT: After activating this skill with use_skill, DO NOT call use_skill again. Follow the instructions above to complete the user's request.