# Decision Guide

How to decide where inbox items belong in the personal memory system.

## Decision Process

For each inbox item, follow this decision tree:

### 1. Review Existing Structure

Read `personal-memory-index.md` to understand:
- Current folder structure
- What each folder contains
- Where similar content already exists

### 2. Match to Existing Folder

**Check if relevant folder exists:**

| Question | Action |
|----------|--------|
| Does a folder match this topic? | Use that folder → Go to step 3 |
| Is content related to existing folder? | Use closest match → Go to step 3 |
| No folder fits? | Go to "Create New Folder" section below |

**Multi-Level Organization:**
- Consider subfolders within existing folders (e.g., `technology/python/`)
- Support 3-5 levels of nesting as content grows
- Start simple, deepen hierarchy only when needed

### 3. Choose or Create File

Within the target folder:

| Scenario | Action |
|----------|--------|
| Relevant file exists | Add to existing file (see [File Templates](./file-templates.md)) |
| No relevant file | Create new file (see [File Templates](./file-templates.md)) |
| File is too large (~500 lines) | Consider breaking it up (see [File Reorganization](./file-reorganization.md)) |

## Create New Folder

### When to Create

Create a new folder when:
- ✅ **No existing folder fits** - Content doesn't logically belong in any current category
- ✅ **New major category** - Represents a new area of knowledge/interest
- ✅ **Expected growth** - You anticipate 5+ future items in this category
- ✅ **Distinct topic** - Topic is sufficiently different from existing categories

### When NOT to Create

Don't create a new folder if:
- ❌ **Rare one-off** - Only 1-2 items expected, add to closest existing folder
- ❌ **Fits existing category** - Can be reasonably placed in current structure
- ❌ **Too granular** - Topic is too specific (create a file instead)
- ❌ **Temporary** - Short-term information that won't grow

### How to Create

If a new folder is needed, see **[New Folder Creation Guide](./new-folder-creation.md)** for:
- How to present options to the user
- Folder naming conventions
- Complete creation process

## Naming Conventions

### Files
- Format: `lowercase-with-hyphens.md`
- Be descriptive and searchable
- Examples: `python-best-practices.md`, `aws-architecture-notes.md`

### Folders
- Format: `lowercase-with-hyphens/`
- Use clear, categorical names
- Examples: `technology/`, `work-contribution/`, `personal/`

## Special Content Types

For specific content types, reference these guides:

- **Bookmarks/URLs** → See [Bookmarks Guide](./bookmarks.md)
- **Work achievements** → See [Work Contributions Guide](./work-contribution.md)
- **Personal documents** → See [Identity Guide](./identity.md)

## File Size Management

### When a File Grows Too Large

Monitor file size during processing:

| File Size | Action |
|-----------|--------|
| < 300 lines | Continue adding content |
| 300-500 lines | Start considering reorganization |
| > 500 lines | Strongly consider breaking up |

### What to Do

When a file becomes too large:
1. Note it for future reorganization, OR
2. Reorganize immediately if clearly needed

See **[File Reorganization Guide](./file-reorganization.md)** for detailed steps.

## Examples

### Example 1: Python Learning Notes

```
Inbox item: "Python decorator tutorial from RealPython"

Decision:
1. Check folders → "technology/" exists
2. Check subfolders → "technology/python/" exists
3. Check files → "python-learning-resources.md" exists
4. Decision: Add to existing file

Action: Add to technology/python/python-learning-resources.md
```

### Example 2: New Fitness Topic

```
Inbox item: "Workout routine for strength training"

Decision:
1. Check folders → No "fitness/" or "health/" folder
2. Expected growth? → Likely, user may capture more fitness info
3. Distinct topic? → Yes, different from existing categories
4. Decision: Create new folder

Action: 
- Ask user for folder name preference (fitness/ or health/)
- Create folder (see New Folder Creation guide)
- Create file: fitness/strength-training.md
```

### Example 3: One-off Recipe

```
Inbox item: "Recipe for chocolate chip cookies"

Decision:
1. Check folders → No "recipes/" folder
2. Expected growth? → Uncertain, might be one-off
3. Fits existing? → Could go in "personal/"
4. Decision: Add to existing folder, don't create new

Action: Create file personal/recipes.md (single file, not folder)
```

## Tips

- **When in doubt**, add to the closest existing folder rather than creating new ones
- **Over time**, patterns will emerge showing when new folders are needed
- **User preference** matters - ask when the decision isn't obvious
- **Start simple**, add complexity only as needed
- **Folders are for categories**, files are for specific topics within categories