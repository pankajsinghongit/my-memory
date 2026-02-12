# Processing Web Bookmarks and URLs

**When to use**: documentation links, articles, saved web resources with their brief title or description

## Storage Location
- `personal-memory/bookmarks/`
- Organize by category (work-bookmarks.md, learning-bookmarks.md, tools-bookmarks.md, etc.)

## How to Process

1. **Read the inbox entry** to understand:
   - What is this link about?
   - Why was it saved?
   - What category does it belong to?

2. **Determine the category**:
   - Work-related documents → `work-bookmarks.md`
   - Learning resources → `learning-bookmarks.md`
   - Tools and apps → `tools-bookmarks.md`
   - Create new category files as needed

3. **Add to the appropriate file** with this structure:
```markdown
### [Title/Name]
- **Link**: [URL]
  - Brief description of what this is
  - Why it's useful or important
  - **Added**: YYYY-MM-DD
```

## Example

**Inbox Entry:**
```markdown
## [2026-02-11 12:01] DLS Virtual Assistant PRFAQ

Amazon WorkDocs document containing the PRFAQ for DLS Virtual Assistant.

Source: https://amazon.awsapps.com/workdocs-amazon/...
```

**Result in work-bookmarks.md:**
```markdown
### DLS Virtual Assistant
- **PRFAQ Document**: [WorkDocs Link](https://amazon.awsapps.com/workdocs-amazon/...)
  - Press Release and FAQ for DLS Virtual Assistant project
  - **Added**: 2026-02-11
```

## Tips
- Include URL in content with context about what it contains
- Group related bookmarks under topic headings
- Add brief notes about why the bookmark is valuable
- Update "Last Updated" date when adding new bookmarks