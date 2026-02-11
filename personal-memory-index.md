# Personal Memory Index

This file contains the complete hierarchical index of all folders and files within the `personal-memory` directory. It provides a quick reference to navigate your knowledge base and understand its structure at a glance.

## Purpose

- **Visual Map**: See the entire structure of your knowledge base in one place
- **Navigation Aid**: Quickly locate where information is stored
- **Structure Reference**: Maintain consistency when adding new content
- **Documentation**: Track how your knowledge base evolves over time

## How to Maintain This Index

### Manual Update
After adding, removing, or reorganizing folders and files in `personal-memory/`, update this index to reflect the current structure.

### Automated Update (Optional)
You can use the `tree` command to automatically generate the structure:

```bash
# For macOS/Linux (install tree if needed: brew install tree)
tree personal-memory/ > temp.txt

# Copy the output and paste it below in the Directory Structure section
```

Or use a simple script:
```bash
# Generate tree structure and copy to clipboard (macOS)
tree personal-memory/ | pbcopy

# For Linux with xclip
tree personal-memory/ | xclip -selection clipboard
```

## Tips for Organizing

- Use descriptive folder names that clearly indicate the content
- Keep folder depth reasonable (3-5 levels maximum)
- Group related topics together
- Use consistent naming conventions (lowercase, hyphens for spaces)
- Review and refactor the structure periodically as it grows

---

## Directory Structure

Last Updated: February 11, 2026

```
personal-memory/
├── technology/
│   ├── programming/
│   ├── tools/
│   └── tutorials/
├── health/
│   ├── fitness/
│   ├── nutrition/
│   └── mental-health/
└── finance/
    ├── investments/
    └── budgeting/
```

## Summary Statistics

- **Total Folders**: 11
- **Main Categories**: 3 (technology, health, finance)
- **Subcategories**: 8
- **Last Updated**: February 11, 2026

---

## Notes

- This index should be updated whenever you make significant changes to the folder structure
- Consider adding file counts or brief descriptions for each category as your knowledge base grows
- You can add links to important files or documents within each category for quick access
