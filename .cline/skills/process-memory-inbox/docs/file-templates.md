# General File Processing

**When to use**: General content that doesn't fit specialized categories (bookmarks, work contributions, personal info).

For specialized content types, see:
- **[Bookmarks Guide](./bookmarks.md)** - For URLs, documentation, web resources
- **[Work Contributions Guide](./work-contribution.md)** - For work achievements, projects
- **[Personal Info Guide](./identity.md)** - For personal documents, family info, contacts

## Process for Adding Content

### Step 1: Review the Target File

Before adding content, **read the file first** to understand:
- Current structure and organization
- Existing section headings
- Formatting patterns used
- Metadata format (dates, tags, etc.)

```
read_file: personal-memory/path/to/file.md
```

### Step 2: Add Content Appropriately

**Match the existing file's structure:**
- Use similar heading levels (H2, H3, etc.)
- Follow the same formatting style
- Add to relevant existing sections OR create new sections as needed
- Maintain consistent spacing and organization

**Always update metadata:**
- Change `**Last Updated**: YYYY-MM-DD` to current date
- Add appropriate tags if the file uses them

### Step 3: Use Proper Tool

**For adding to existing files:**
```
replace_in_file: personal-memory/path/to/file.md
```

Use SEARCH/REPLACE blocks to:
1. Update the "Last Updated" date
2. Add new content in appropriate location

**For creating new files:**
```
write_to_file: personal-memory/path/to/file.md
```

Review similar files in the same folder to understand what structure to use.

## Creating New Files

When creating a new file:

1. **Review similar files** in the target folder to understand conventions
2. **Include basic metadata** that existing files use:
   - Created date
   - Last Updated date
   - Tags (if the folder uses them)
3. **Match the organizational pattern** of similar files
4. **Use appropriate headings** to structure content
5. **Add the inbox content** in a logical way

### Required Elements

Every file should have:
- **File title** (H1 heading)
- **Created** and **Last Updated** dates
- **Well-structured content** with appropriate headings
- **Proper markdown formatting**

## Markdown Formatting

### Headings
- `# Title` - File title (one per file)
- `## Section` - Major sections
- `### Subsection` - Subsections
- Avoid going deeper than H4

### Lists
```markdown
- Unordered item
  - Nested item

1. Ordered item
2. Another item

- [ ] Task item
- [x] Completed task
```

### Links
```markdown
[External link](https://url.com)
[Internal link](../folder/file.md)
```

### Code
```markdown
Inline `code` with backticks

```language
code block
```
```

### Emphasis
- *Italic* or _italic_
- **Bold** or __bold__
- ***Bold italic***

## Best Practices

1. **Review first, then add** - Always read the target file before adding content
2. **Match existing style** - Keep formatting consistent with the file
3. **Update metadata** - Always change "Last Updated" date
4. **Use clear headings** - Make content scannable
5. **Add context** - Include why information was captured, not just what
6. **Link related content** - Cross-reference other relevant files
7. **Keep it organized** - Use appropriate section structure

## Quality Checklist

Before completing:
- [ ] Content added to appropriate location
- [ ] "Last Updated" date changed to current date
- [ ] Formatting matches existing file style
- [ ] Headings are appropriate and clear
- [ ] Links work correctly (if any)
- [ ] File name follows `lowercase-with-hyphens.md` convention (for new files)

---

**Key Principle**: Review the target file's existing structure and match it, rather than forcing a rigid template.