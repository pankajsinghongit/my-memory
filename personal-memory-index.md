# Personal Memory Index

This file provides a **complete map of what information is stored where** in your `personal-memory` folder. Use this index to quickly find topics, understand your knowledge organization, and discover what you've documented.

## Purpose

- **Find Information**: Quickly locate where specific topics or notes are stored
- **Understand Structure**: See how your knowledge is organized at a glance
- **Navigate Efficiently**: Jump to the right folder without browsing
- **Track Growth**: Monitor how your knowledge base evolves over time

## How to Use This Index

1. **Find a Topic**: Scan the directory structure to see where information is stored
2. **Browse Categories**: Review main categories to understand your knowledge domains
3. **Plan New Notes**: See where new information should fit
4. **Understand Growth**: See how folders can evolve from simple to multi-level as content grows
5. **Identify Gaps**: Notice areas where you haven't documented much yet

## Maintaining This Index

### When to Update
Update this index when you:
- Add new folders or categories
- Reorganize existing structure
- Remove outdated folders
- Break up large files into multi-level folder structures
- Complete a significant inbox processing session

### How to Update

**Manual Method:**
Review your `personal-memory/` folder and update the structure below.

**Automated Method:**
```bash
# Generate structure with tree command (macOS/Linux)
tree personal-memory/ -L 3 --dirsfirst

# Or use find command
find personal-memory/ -type d | sort
```

## Organization Philosophy

**Multi-Level Hierarchy**: Personal memory supports flexible multi-level folder organization
- Start simple with 1-2 levels for new topics
- Deepen the hierarchy as content grows naturally  
- Aim for 3-5 levels maximum for maintainability
- When a file grows beyond ~500 lines, consider breaking it into a folder structure

**Evolution Example**:
```
Initial:     python-notes.md
Growing:     python/ → python/basics.md, python/advanced.md
Mature:      python/ → python/basics/, python/frameworks/, python/advanced/
```

---

## Directory Structure

**Last Updated**: February 11, 2026 4:54 PM

```
personal-memory/
├── inbox.md                        # Unprocessed information waiting to be organized
├── bookmarks/                      # Bookmarks and saved links
│   ├── tools-bookmarks.md         # Tools and productivity application bookmarks
│   └── work-bookmarks.md          # Work-related bookmarks and project links
├── identity/                       # Personal identity and profile information
│   └── personal-info.md           # Personal information (PAN, family details)
├── where-is-my-stuff/             # Location tracking and item organization
└── work-contribution/             # Work contributions and achievements
    └── overview.md                # Summary of work contributions and career milestones

Note: Folders can contain subfolders as content grows (up to 3-5 levels deep)
```

## Content Overview

### bookmarks
**What's Here**: Saved links, articles, resources
**Purpose**: Collection of useful web resources and references
**Files**:
- `tools-bookmarks.md` - Tools and productivity applications (Obsidian)
- `work-bookmarks.md` - Work-related bookmarks including project documents (DLS Virtual Assistant PRFAQ)

### identity
**What's Here**: Personal identity information, profiles, documentation
**Purpose**: Personal information and identity management
**Files**:
- `personal-info.md` - Official documents (PAN, Passport) and family information (spouse name)

### where-is-my-stuff
**What's Here**: Item locations, organization system
**Purpose**: Track where physical or digital items are stored

### work-contribution
**What's Here**: Work contributions, achievements, and career milestones
**Purpose**: Track professional accomplishments, project impacts, and career documentation for performance reviews and portfolio building
**Files**:
- `overview.md` - Template and guidelines for documenting work contributions

## Summary Statistics

- **Last Updated**: February 11, 2026 8:21 PM
- **Total Folders**: 4
- **Total Files**: 5 (inbox.md + 4 content files)
- **Inbox Status**: ✅ Empty (all items processed)
- **Organization**: Currently flat structure (0-1 levels), can grow to 3-5 levels as needed

---

## Notes & Reminders

- Update this index when you add new folders or files
- Add descriptions for each folder as content grows
- Review this index when processing your inbox
- Keep folder descriptions current and accurate
- When files grow large (~500 lines), consider breaking them into subfolders

---

**Remember**: This index is your map to your knowledge. Keep it updated and use it as your first stop when looking for information!