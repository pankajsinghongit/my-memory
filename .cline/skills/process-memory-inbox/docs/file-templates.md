# File Templates

Proper markdown structure and formatting for personal memory files.

## Adding to Existing Files

### Process

1. **Read the file first**: `read_file: personal-memory/path/to/file.md`
2. **Use replace_in_file** to add new content
3. **Update the "Last Updated" date**

### Template for Adding Content

```markdown
# Existing Title

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD  ← Update this to current date

## Existing Section

Existing content remains here...

## New Section (if adding new section)

Content from inbox entry goes here...
```

### Example: Adding to Existing File

```markdown
------- SEARCH
**Last Updated**: 2026-01-15
=======
**Last Updated**: 2026-02-17
+++++++ REPLACE

------- SEARCH
## References
=======
## Python Decorators

Content about decorators from inbox...

## References
+++++++ REPLACE
```

## Creating New Files

### Standard File Template

Use `write_to_file` to create new files with this structure:

```markdown
# Title

**Created**: YYYY-MM-DD
**Last Updated**: YYYY-MM-DD
**Tags**: #tag1 #tag2 #tag3

## Summary
Brief description of what this file contains.

## Content

Main content from inbox entry goes here.

## References
- [Source link](url) - Description
- [Another source](url) - Description

## Next Actions
- [ ] Follow-up task if needed
- [ ] Another action item
```

### Required Metadata

Every file must include:
- **Created**: Date file was first created
- **Last Updated**: Date file was last modified
- **Tags**: Relevant hashtags for searchability (optional but recommended)

### Optional Sections

Add these sections as needed:
- **Summary**: Brief overview (recommended for longer files)
- **References**: Links to sources, related documents
- **Next Actions**: Tasks or follow-ups
- **Related Files**: Links to other relevant files in personal memory

## File Types

### 1. Note Files (General Knowledge)

For learning notes, tutorials, concepts:

```markdown
# Topic Name

**Created**: 2026-02-17
**Last Updated**: 2026-02-17
**Tags**: #learning #topic-name

## Summary
What this note covers.

## Key Concepts

### Concept 1
Explanation...

### Concept 2
Explanation...

## Examples

Practical examples...

## References
- Sources and links
```

### 2. Bookmark Files

For saved URLs, documentation, articles:

```markdown
# Resource Category

**Created**: 2026-02-17
**Last Updated**: 2026-02-17
**Tags**: #bookmarks #resources

## [Article/Tool Name](url)
**Added**: 2026-02-17
**Category**: Development/Design/etc.

Brief description of the resource and why it's useful.

**Key Takeaways:**
- Point 1
- Point 2

---

## [Another Resource](url)
**Added**: 2026-02-17
**Category**: Category name

Description...
```

### 3. Work Contribution Files

For career achievements, projects:

```markdown
# Project/Achievement Name

**Created**: 2026-02-17
**Last Updated**: 2026-02-17
**Tags**: #work #achievement #project-name

## Summary
High-level overview of the contribution.

## Impact
- Quantifiable results
- Business value
- Team/customer benefits

## Technical Details
Technologies, approaches, solutions implemented.

## Challenges & Solutions
Problems faced and how they were solved.

## Learnings
Key takeaways and skills developed.

## References
- Documentation links
- Related projects
- Performance metrics
```

### 4. Personal Information Files

For contacts, documents, family info:

```markdown
# Category Name

**Created**: 2026-02-17
**Last Updated**: 2026-02-17
**Tags**: #personal #category

## Item Name

**Type**: Document/Contact/etc.
**Location**: Physical or digital location
**Notes**: Additional context

Details...

---

## Another Item

Details...
```

## Formatting Guidelines

### Headings

- `# Title` - File title (H1, only one per file)
- `## Section` - Major sections (H2)
- `### Subsection` - Subsections (H3)
- Avoid going deeper than H4

### Lists

**Unordered lists:**
```markdown
- Item 1
- Item 2
  - Nested item
```

**Ordered lists:**
```markdown
1. First step
2. Second step
   1. Nested step
```

**Task lists:**
```markdown
- [ ] Incomplete task
- [x] Completed task
```

### Links

**External links:**
```markdown
[Link text](https://url.com)
```

**Internal links (to other files):**
```markdown
[Related note](../folder/file.md)
```

### Code

**Inline code:**
```markdown
Use `code` for inline code
```

**Code blocks:**
````markdown
```python
def example():
    return "code block"
```
````

### Emphasis

- *Italic* or _italic_
- **Bold** or __bold__
- ***Bold and italic***

## Best Practices

1. **Be Consistent**: Use the same structure across similar file types
2. **Update Dates**: Always update "Last Updated" when modifying files
3. **Use Tags**: Add relevant tags for easier searching
4. **Add Context**: Include why information was captured, not just what
5. **Link Related Content**: Cross-reference related files
6. **Keep It Scannable**: Use headings, lists, and formatting effectively
7. **Don't Duplicate**: If information exists elsewhere, link to it instead

## Metadata Updates

When updating a file, always change:

```markdown
**Last Updated**: YYYY-MM-DD  ← Change to current date
```

If adding significant content, consider adding:

```markdown
**Updates:**
- 2026-02-17: Added section on XYZ
- 2026-01-15: Initial creation
```

## Quality Checklist

Before saving a file, verify:
- [ ] Has file title (H1)
- [ ] Includes Created and Last Updated dates
- [ ] Has appropriate tags
- [ ] Content is well-structured with headings
- [ ] Links are functional
- [ ] Formatting is consistent
- [ ] File name follows `lowercase-with-hyphens.md` convention