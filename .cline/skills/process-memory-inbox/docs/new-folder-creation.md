# Creating New Folders During Inbox Processing

This guide covers the process for creating new folders when inbox content doesn't fit any existing folder.

**When to create folders**: See [Decision Guide](./decision-guide.md) for criteria on when a new folder is needed.

## Process for Creating New Folders

### Step 1: Analyze the Content
1. What is this information about?
2. Why doesn't it fit in existing folders?
3. Will there be more similar content? (Need 5+ future items)
4. What would be a logical category name?

### Step 2: Propose Folder Options

When you determine a new folder is needed, **ALWAYS use `ask_followup_question`** to present options:

```markdown
I've identified that this content needs a new folder. Here are my recommendations:

**Content Type**: [Brief description]

**Recommended Folder Options**:
1. **[option1-name]** - [Why this makes sense]
2. **[option2-name]** - [Why this makes sense]
3. **[option3-name]** - [Why this makes sense]

Which option would you prefer, or would you like to suggest a different name?
```

### Step 3: Get User Confirmation

Use `ask_followup_question` tool:

```xml
<ask_followup_question>
<question>
I've identified that "[content summary]" needs a new folder. Here are my recommendations:

**Recommended Options**:
1. **productivity/** - For productivity setups, shortcuts, workflows
2. **reference/** - For reference materials, cheat sheets, guides
3. **configuration/** - For system configs, settings, dotfiles

Which folder name would work best, or would you like to suggest a different name?
</question>
<options>["productivity", "reference", "configuration", "Suggest different name"]</options>
</ask_followup_question>
```

### Step 4: Create the Folder and File

Once user confirms:
1. Create the folder: `personal-memory/[folder-name]/`
2. Create the file with appropriate content
3. Update the memory index
4. Archive to processed-inbox-audit
5. Remove from inbox

## Folder Naming Guidelines

### Format
- **Lowercase with hyphens**: `productivity/`, `work-notes/`, `system-config/`
- **Descriptive**: Clearly indicates what's inside
- **Searchable**: Easy to remember and find
- **Concise**: 1-3 words maximum

### Avoid
- Spaces (use hyphens)
- Special characters (stick to letters, numbers, hyphens)
- Uncommon abbreviations
- Version numbers (unless necessary)
- Dates (except archives)

## Example Scenarios

### Scenario 1: Keyboard Shortcut

**Inbox Content**: Todoist keyboard shortcut `Cmd + Q`

**Analysis**:
- Doesn't fit in bookmarks (not a web link)
- Doesn't fit in personal (not a reminder/habit)
- Doesn't fit in identity (not personal info)
- Could grow: Many more shortcuts expected

**Recommendation**:
```
I've identified that keyboard shortcuts need a dedicated location.

**Recommended Options**:
1. **productivity/** - For productivity setups, shortcuts, workflows, automation
2. **reference/** - For quick reference materials like shortcuts and cheat sheets
3. **configuration/** - For system configurations including shortcuts

Which would you prefer?
```

**User Choice**: productivity/

**Result**: Created `personal-memory/productivity/keyboard-shortcuts.md`

### Scenario 2: Programming Notes

**Inbox Content**: Python async/await notes

**Analysis**:
- Technical/programming content
- Will grow significantly
- May need subcategories later

**Recommendation**:
```
I've identified programming notes need a dedicated space.

**Recommended Options**:
1. **technology/** - Broad tech folder that can grow into subfolders
2. **programming/** - Specifically for programming languages and concepts
3. **learning/technology/** - Under learning category

Which would you prefer?
```

## Template for User Question

```xml
<ask_followup_question>
<question>
I've identified that "[content description]" doesn't fit in existing folders and would benefit from a new category.

**Analysis**:
- Content type: [what it is]
- Why new folder needed: [reasoning]
- Expected growth: [will there be more similar content?]

**Recommended Folder Options**:
1. **[option1]/** - [rationale: what would go here, why it makes sense]
2. **[option2]/** - [rationale: what would go here, why it makes sense]
3. **[option3]/** - [rationale: what would go here, why it makes sense]

Which folder name would work best for you, or would you like to suggest a different name?
</question>
<options>["[option1]", "[option2]", "[option3]", "Suggest different name"]</options>
</ask_followup_question>
```

## After Creating the Folder

1. **Create the first file** with proper structure:
```markdown
# [File Title]

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD
**Tags**: #tag1 #tag2

## Summary
Brief description of what this file contains.

## Content
[Actual content from inbox]
```

2. **Update personal-memory-index.md**:
   - Add to Directory Structure
   - Add to Content Overview with description
   - Update Summary Statistics (folder count)

3. **Archive to processed-inbox-audit**:
   - Include "Moved to" path with new folder
   - Maintain complete entry

4. **Inform user**:
   - Confirm folder created
   - Show file location
   - Explain folder purpose

## Tips

- **Present 3-4 options** - Give variety without overwhelming
- **Explain rationale** - Help user understand why each option makes sense
- **Be flexible** - User may have better ideas
- **Think ahead** - Consider how the folder might evolve
- **Stay organized** - Don't create too many top-level folders (aim for 6-10 max)
- **Use subfolders** - For growing categories, use 2-3 levels

## Notes

- **User knows best** - They understand their needs; our suggestions are guidance
- **Iterate if needed** - Folders can be renamed or reorganized later
- **Document purpose** - Update memory index with clear folder descriptions
- **Monitor usage** - Track if new folders are working as intended

---

**Remember**: Creating folders is about organizing knowledge for easy retrieval. When in doubt, ask the user for their preference!