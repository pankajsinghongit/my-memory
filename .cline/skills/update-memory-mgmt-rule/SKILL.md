---
name: update-memory-mgmt-rule
description: Update memory management rules and cascade changes to dependent skills
---

# update-memory-mgmt-rule

This skill helps you properly update the personal memory management rules (`personal-memory-mgmt-rule.md`) and ensure that any dependent skills are updated accordingly to maintain consistency across the system.

## Purpose

- **Maintain Rules**: Keep memory management rules current and effective
- **Ensure Consistency**: Propagate rule changes to all dependent components
- **Track Changes**: Document what was changed and why
- **Prevent Breakage**: Identify and update skills that depend on the rules

## Critical Understanding

⚠️ **IMPORTANT**: Changes to `personal-memory-mgmt-rule.md` may affect:
- **Skills** in `.cline/skills/` that reference or implement these rules
- **Workflows** that users follow based on these rules
- **File structures** and naming conventions
- **Processing schedules** and maintenance routines

## When to Use This Skill

Use this skill when the user wants to:
- Modify existing rules or guidelines
- Add new rules or sections
- Change folder structure conventions
- Update naming conventions
- Adjust processing schedules
- Refine workflows
- Add or modify custom workflows
- Update maintenance schedules

## Steps

### 1. Read Current Rules
Start by reading the existing rules to understand the current state.

```
read_file: personal-memory-mgmt-rule.md
```

### 2. Understand the Requested Change
Clarify with the user:
- What specific rule needs to change?
- Why is this change needed?
- What is the new behavior/rule?
- Are there examples to add or update?

### 3. Identify Affected Skills
**Critical Step**: Determine which skills depend on the rule being changed.

**Current Skills to Check:**
- `remember-info` - Depends on inbox rules, timestamp format, entry format
- `process-memory-inbox` - Depends on processing workflow, naming conventions, folder structure, audit format
- `update-memory-mgmt-rule` - Meta-skill that tracks all dependencies

**Common Dependencies:**
- **Inbox Rules Changes** → Affects: `remember-info`, `process-memory-inbox`
- **Timestamp Format Changes** → Affects: `remember-info`, `process-memory-inbox`
- **Folder Structure Changes** → Affects: `process-memory-inbox`
- **Naming Convention Changes** → Affects: `remember-info`, `process-memory-inbox`
- **Processing Workflow Changes** → Affects: `process-memory-inbox`
- **Content Guidelines Changes** → Affects: `process-memory-inbox`
- **Audit Format Changes** → Affects: `process-memory-inbox`

### 4. Update the Management Rules
Make the requested changes to `personal-memory-mgmt-rule.md`:

**Best Practices:**
- Keep formatting consistent with existing structure
- Update the "Last Reviewed" date
- Add entry to Changelog section with date and description
- Maintain markdown formatting and section structure
- Keep examples clear and accurate

**Structure to Maintain:**
```markdown
## Section Name

### Subsection

Content with examples...

**Important Notes:**
- Point 1
- Point 2
```

### 5. Update the Changelog
Always add an entry to the Changelog section:

```markdown
### Changelog
Track changes to your management rules:

- **2026-02-11**: Initial creation of management rules
- **YYYY-MM-DD**: [Brief description of what changed]
```

### 6. Update Dependent Skills
For each affected skill, update its SKILL.md file:

**What to Update:**
- Instructions that reference the changed rule
- Examples that demonstrate the changed behavior
- Step-by-step procedures that implement the rule
- Format specifications
- Quality checklists

**Example**: If inbox entry format changes, update `remember-info/SKILL.md`:
- Update the "Inbox Entry Format" section
- Update all examples showing the format
- Update the quality checklist items

### 7. Verify Consistency
Check that all updates are consistent:

**Checklist:**
- [ ] Rule change is clearly documented in personal-memory-mgmt-rule.md
- [ ] Changelog updated with date and description
- [ ] All affected skills identified
- [ ] Each affected skill's SKILL.md updated
- [ ] Examples in rules match examples in skills
- [ ] No contradictions between rules and skill instructions
- [ ] Quality checklists updated if needed

### 8. Inform the User
Provide a summary of:
- What rule was changed
- Why it was changed
- Which skills were updated
- Any action items for the user (e.g., re-read updated rules)

## Skill Dependencies Map

Maintain this map of which skills depend on which rule sections:

### remember-info Skill Dependencies
- **Inbox Rules** → Entry format, timestamp format, required fields
- **Inbox Entry Format** → Exact format specification
- **Inbox Processing** → Understanding of how entries will be processed
- **Naming Conventions** → File naming when creating new notes
- **Content Guidelines** → Note structure and formatting

### process-memory-inbox Skill Dependencies
- **Processing Workflow** → All 5 steps (Read, Decide, Move, Archive, Update)
- **Inbox Rules** → Understanding inbox structure and formats
- **Naming Conventions** → File and folder naming when creating new notes
- **Organization Rules** → Folder structure and categorization principles
- **Content Guidelines** → Note structure for created/updated files
- **Processed Audit Format** → Exact format for archiving entries
- **Personal Memory Index** → When and how to update the index

### update-memory-mgmt-rule Skill Dependencies
- **All Sections** → This meta-skill needs to track dependencies of all other skills
- **Changelog** → Must be updated with every rule change
- **All Skills** → Must identify and update affected skills when rules change

### Future Skills
As new skills are added that depend on rules, document them here:

```
skill-name:
  - Rule section it depends on
  - Specific rules it implements
  - What needs updating if rules change
```

## Common Update Scenarios

### Scenario 1: Change Timestamp Format
**Example**: Change from `[YYYY-MM-DD HH:MM]` to `[YYYY-MM-DD]`

**Steps:**
1. Update `personal-memory-mgmt-rule.md` → Inbox Entry Format section
2. Update `remember-info/SKILL.md`:
   - Timestamp Format subsection
   - All examples showing timestamps
   - Quality checklist timestamp verification
3. Add changelog entry

### Scenario 2: Add New Emoji Marker
**Example**: Add 📅 emoji for scheduled items

**Steps:**
1. Update `personal-memory-mgmt-rule.md` → Inbox Rules section
2. Update `remember-info/SKILL.md`:
   - Special Cases section
   - Add new example showing the emoji
   - Update instructions for when to use it
3. Add changelog entry

### Scenario 3: Change Folder Structure Rules
**Example**: Change maximum folder depth from 3-4 to 2-3 levels

**Steps:**
1. Update `personal-memory-mgmt-rule.md` → Organization Rules section
2. Check all skills for folder creation logic
3. Update affected skills' SKILL.md files
4. Update examples to match new depth limit
5. Add changelog entry

### Scenario 4: Modify Processing Workflow
**Example**: Add a new step in inbox processing workflow

**Steps:**
1. Update `personal-memory-mgmt-rule.md` → Processing Workflow section
2. Create or update processing skill (if one exists)
3. Update `remember-info/SKILL.md` → "Inbox Processing (For Reference)" section
4. Add changelog entry

### Scenario 5: Add New Custom Workflow
**Example**: Add workflow for "Meeting Notes"

**Steps:**
1. Update `personal-memory-mgmt-rule.md` → Custom Workflows section
2. Add new subsection with clear steps
3. Consider if a new skill should be created
4. Add changelog entry
5. Update index if new folders are mentioned

## Quality Checklist

Before completing the update, verify:

### Rules File (personal-memory-mgmt-rule.md)
- [ ] Change is clearly documented
- [ ] Formatting is consistent with existing structure
- [ ] Examples are clear and accurate
- [ ] "Last Reviewed" date updated
- [ ] Changelog entry added with date and description
- [ ] No typos or formatting errors
- [ ] Markdown renders correctly

### Dependent Skills
- [ ] All affected skills identified
- [ ] Each affected skill's SKILL.md updated
- [ ] Instructions match new rules
- [ ] Examples demonstrate new behavior
- [ ] Quality checklists updated if needed
- [ ] No contradictions with rules

### System Consistency
- [ ] Rules and skills are in sync
- [ ] Examples are consistent across files
- [ ] No breaking changes without user awareness
- [ ] Documentation is clear and complete

## Important Reminders

1. **Always Update Changelog**: Every change must be documented
2. **Check All Skills**: Don't assume - verify which skills are affected
3. **Update Examples**: Examples must match the new rules
4. **Test Understanding**: Ensure instructions are clear and unambiguous
5. **Maintain Consistency**: Rules, skills, and examples must align
6. **Consider Impact**: Think about how changes affect existing workflows
7. **Document Dependencies**: Keep the dependency map current

## Error Handling

### If Rules File Doesn't Exist
- Create it using the standard template structure
- Document this as initial creation in changelog

### If Skill Dependencies Are Unclear
- Read each skill's SKILL.md carefully
- Look for references to rules sections
- When in doubt, update the skill to be safe

### If Changes Conflict
- Discuss with user to resolve conflicts
- Document the decision in changelog
- Update all affected components consistently

## Examples

### Example 1: Adding New Emoji Marker

**User Request**: "Add a 📅 emoji for scheduled/deadline items in inbox"

**Actions:**
1. Update `personal-memory-mgmt-rule.md`:
```markdown
### Inbox Rules
- Mark urgent items with 🔴 emoji
- Mark ideas worth exploring with 💡 emoji
- Mark scheduled/deadline items with 📅 emoji
```

2. Update `remember-info/SKILL.md` → Special Cases:
```markdown
### Items with Deadlines
For items with deadlines or scheduled dates:
- Use 📅 emoji in title
- Include the deadline or scheduled date
- Example: `## [2026-02-11 14:30] 📅 Project Deadline - Submit Proposal`
```

3. Add changelog entry:
```markdown
- **2026-02-11**: Added 📅 emoji marker for scheduled/deadline items
```

### Example 2: Changing Timestamp Format

**User Request**: "Simplify timestamp to just date, remove time"

**Actions:**
1. Update `personal-memory-mgmt-rule.md`:
```markdown
### Inbox Entry Format
## [YYYY-MM-DD] Topic Title
```

2. Update `remember-info/SKILL.md`:
   - Change timestamp format specification
   - Update all examples from `[2026-02-11 14:30]` to `[2026-02-11]`
   - Update quality checklist

3. Add changelog entry:
```markdown
- **2026-02-11**: Simplified timestamp format to date only (removed time)
```

### Example 3: Adding New Processing Step

**User Request**: "Add step to tag entries by category during processing"

**Actions:**
1. Update `personal-memory-mgmt-rule.md` → Processing Workflow:
```markdown
3. **Categorize** and add tags:
   - Add #work, #personal, #learning, etc.
4. **Move** content to its proper location...
```

2. Update `remember-info/SKILL.md` → Inbox Processing section:
```markdown
1. **Read** each item during scheduled processing
2. **Categorize** by adding tags (#work, #personal, etc.)
3. **Decide** where it belongs...
```

3. Add changelog entry

## Success Criteria

The skill update is successful when:
1. ✅ Rules are updated clearly and accurately
2. ✅ Changelog documents the change with date
3. ✅ All affected skills are identified
4. ✅ Each affected skill is updated consistently
5. ✅ No contradictions exist between rules and skills
6. ✅ Examples demonstrate the new behavior
7. ✅ User is informed of all changes made

## Notes

- **Frequency**: Memory management rules should be reviewed monthly
- **Evolution**: Rules should evolve based on what works for the user
- **Flexibility**: Rules serve the user, not vice versa
- **Documentation**: Good documentation prevents confusion
- **Skills Growth**: As more skills are added, this dependency map grows

---

**Remember**: Keeping rules and skills in sync is crucial for system reliability. When rules change, skills must be updated to match, otherwise users will get inconsistent behavior!