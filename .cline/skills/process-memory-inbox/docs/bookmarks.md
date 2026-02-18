## How to Process Web Bookmarks and URLs

1. **Add as table entry** in the appropriate file

## Table Structure

Bookmarks should be added to a markdown table with these columns:

| Column | Purpose |
|--------|---------|
| **Title** | Name/title of the resource |
| **URL** | Link to the resource |
| **Tags** | Searchable tags (comma-separated) |
| **Description** | What it is and why it's useful |
| **Added** | Date added (YYYY-MM-DD) |

### Adding to Existing Table

When adding to an existing bookmark file:

1. **Read the file** to see the current table
2. **Add a new row** at the end of the table with the bookmark information
3. **Update "Last Updated"** metadata date

Example table in bookmark file:
```markdown
| Title | URL | Tags | Description | Added |
|-------|-----|------|-------------|-------|
| AWS S3 Best Practices | [link](https://docs.aws.amazon.com/...) | aws, s3, storage | Official AWS guide for S3 best practices | 2026-01-15 |
| Python Async Guide | [link](https://realpython.com/...) | python, async, tutorial | Comprehensive tutorial on async/await patterns | 2026-02-10 |
```

### Creating New Table

If the bookmark file doesn't have a table yet, create one with the header row:

```markdown
| Title | URL | Tags | Description | Added |
|-------|-----|------|-------------|-------|
```

Then add your bookmark as the first data row.

## Example

**Inbox Entry:**
```markdown
## [2026-02-11 12:01] DLS Virtual Assistant PRFAQ

Amazon WorkDocs document containing the PRFAQ for DLS Virtual Assistant.

Source: https://amazon.awsapps.com/workdocs-amazon/...
```

**Result in work-bookmarks.md:**

Add this row to the table:
```markdown
| DLS Virtual Assistant | [link](https://amazon.awsapps.com/workdocs-amazon/...) | prfaq, dls, workdocs | Press Release and FAQ for DLS Virtual Assistant project | 2026-02-11 |
```

Complete table would look like:
```markdown
| Title | URL | Tags | Description | Added |
|-------|-----|------|-------------|-------|
| DLS Virtual Assistant | [link](https://amazon.awsapps.com/workdocs-amazon/...) | prfaq, dls, workdocs | Press Release and FAQ for DLS Virtual Assistant project | 2026-02-11 |
```

## Tips

1. **Keep descriptions concise** - Table cells should be scannable
2. **Use meaningful tags** - Help with future searching (technology, category, type)
3. **Consistent tag format** - lowercase, comma-separated, no spaces in tags
4. **Link format** - Use `[link](url)` for cleaner table appearance
5. **Update metadata** - Always change "Last Updated" date in file metadata
6. **Table alignment** - Markdown tables don't need to be perfectly aligned, focus on content

## Adding Multiple Bookmarks

When processing multiple bookmarks for the same file:
1. Read the file once
2. Prepare all new table rows
3. Add all rows in a single operation
4. Update "Last Updated" once

## Quality Checklist

Before completing:
- [ ] Bookmark added as table row
- [ ] All columns filled (Title, URL, Tags, Description, Added)
- [ ] Link format is `[link](url)`
- [ ] Tags are lowercase and comma-separated
- [ ] Description is clear and concise
- [ ] Date format is YYYY-MM-DD
- [ ] File's "Last Updated" metadata updated