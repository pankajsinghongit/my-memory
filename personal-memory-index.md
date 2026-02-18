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

**Folder-Specific Rules**: Any folder can have its own `memory-management-rule.md`
- Each folder can optionally contain a `memory-management-rule.md` file
- Rules in this file apply to all files and subfolders within that folder
- More specific rules (closer to the file) take precedence over general rules
- Useful for folders with special requirements (naming, structure, content format)
- Example: `work-contribution/memory-management-rule.md` could specify project file naming conventions

---

## Directory Structure

```
personal-memory/
├── inbox.md                                              # Unprocessed information waiting to be organized
├── bookmarks/                                            # Bookmarks and saved links
│   ├── tools-bookmarks.md                               # Tools and productivity application bookmarks
│   └── work-bookmarks.md                                # Work-related bookmarks and project documents
├── identity/                                             # Personal identity and profile information
│   └── personal-info.md                                 # Personal information and official documents
├── personal/                                             # Personal life, habits, and reminders
│   ├── reminders.md                                     # Recurring reminders and personal tasks
│   └── travel-plans.md                                  # Travel intentions, plans, and trip ideas
├── productivity/                                         # Productivity setup, shortcuts, and workflows
│   └── keyboard-shortcuts.md                            # Centralized keyboard shortcuts for all applications
└── work-contribution/                                    # Work contributions and achievements
    ├── overview.md                                      # Summary of work contributions and career milestones
    ├── project-2026-02-dls-manager-approval-service.md # DLS Manager Approval Service project contributions
    └── project-2026-interviews.md                      # Interviews conducted for hiring and recruitment (yearly)

Note: Folders can contain subfolders as content grows (up to 3-5 levels deep)
```

## Content Overview

### bookmarks
**What's Here**: Saved links, articles, and resources
**Purpose**: Collection of useful web resources and references
**Files**:
- `tools-bookmarks.md` - Tools and productivity applications (Obsidian for knowledge management)
- `work-bookmarks.md` - Work-related bookmarks and project documents (DLS Virtual Assistant PRFAQ)

### identity
**What's Here**: Personal identity information, profiles, and official documentation
**Purpose**: Centralized storage for personal information and identity management
**Files**:
- `personal-info.md` - Official documents (PAN, Passport numbers) and family information (spouse details)

### personal
**What's Here**: Personal life management, habits, recurring reminders, and travel plans
**Purpose**: Track personal routines, home maintenance, regular tasks, and travel intentions
**Files**:
- `reminders.md` - Recurring reminders and personal tasks (weekly plant watering with log)
- `travel-plans.md` - Travel intentions and trip planning (Goa trip in planning)

### productivity
**What's Here**: Productivity setup, keyboard shortcuts, workflows, and automation
**Purpose**: Centralized productivity tools configuration and efficiency optimizations
**Files**:
- `keyboard-shortcuts.md` - Keyboard shortcuts for all applications (GLOBAL shortcuts, Todoist, macOS system shortcuts)

### work-contribution
**What's Here**: Work contributions, achievements, and career milestones
**Purpose**: Track professional accomplishments, project impacts, and career documentation for performance reviews
**Files**:
- `overview.md` - Miscellaneous one-off contributions with clear guidance on when to use vs dedicated project files
- `project-2026-02-dls-manager-approval-service.md` - DLS Manager Approval Service design review (critical feedback leading to strategy change from rebuild to reuse)
- `project-2026-interviews.md` - Yearly log of interviews conducted for hiring and recruitment with statistics tracking

---

## Notes & Reminders

- Update this index when you add new folders or files
- Add descriptions for each folder as content grows
- Review this index when processing your inbox
- Keep folder descriptions current and accurate
- When files grow large (~500 lines), consider breaking them into subfolders

---

**Remember**: This index is your map to your knowledge. Keep it updated and use it as your first stop when looking for information!