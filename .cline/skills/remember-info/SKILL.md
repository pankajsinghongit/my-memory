---
name: remember-info
description: Store new information in the personal memory inbox following memory management rules
---

# remember-info

This skill helps you capture and remember new information by storing it in the inbox for later processing. All new information must first go to `personal-memory/inbox.md` following the established memory management rules.

## Purpose

- **Capture**: Quickly store new information without interrupting workflow
- **Organize**: Information will be processed and organized during scheduled inbox processing sessions
- **Track**: All entries include timestamps for audit trail and processing tracking
- **Preserve**: Nothing gets lost - everything is captured with proper context

## When to Use This Skill

Use this skill when the user wants to:
- Remember a piece of information (URL, fact, note, etc.)
- Store personal details (contact info, passwords, IDs)
- Save a reference or bookmark
- Capture a quick thought or idea
- Store any information for future reference

**Key Principle**: ALL new information must first go to inbox.md before being organized into the appropriate folder structure.

## Steps

### 1. Read Current Inbox
Always start by reading the current inbox to avoid conflicts and understand existing content.

```
read_file: personal-memory/inbox.md
```

### 2. Prepare the Inbox Entry
Format the new information according to the inbox entry format:

**Required Format:**
```markdown
## [YYYY-MM-DD HH:MM] Topic Title

Content of the captured information...

Source: [URL or reference if applicable]
```

**Timestamp Format:**
- Use `[YYYY-MM-DD HH:MM]` format (e.g., `[2026-02-11 14:30]`)
- Use current date and time from environment_details
- Time is in 24-hour format

**Title Guidelines:**
- Short title from the user input to keep it searchable
- Use title case or sentence case consistently

**Content Guidelines:**
- **CRITICAL**: Keep the EXACT information provided by the user. DO NOT enhance, expand, or rewrite the content.
- Only fix obvious typos if needed
- Include source URLs or references when applicable
- Preserve the user's original wording, style, and format

### 3. Add Entry to Inbox
Append the new entry to `personal-memory/inbox.md` using replace_in_file.

**Important:**
- Add the entry at the end of the file (after existing entries)
- Maintain proper markdown structure
- Preserve all existing entries
- Add a blank line between entries

### 4. Confirm Success
Inform the user that the information has been captured and will be processed during the next inbox processing session.

## Special Cases

### Sensitive Information
For sensitive data (passwords, PINs, personal IDs):
- Still add to inbox.md first (following the rules)
- Mention that it will be moved to secure location during processing
- Examples: PAN numbers, Aadhaar, SSN, passwords, etc.

### URLs and Bookmarks
For web links:
- Include the full URL in the `Source:` field
- Add context about why the link is interesting or relevant
- Consider adding emoji markers (💡 for ideas, 🔴 for urgent)

### Ideas and Thoughts
For quick ideas:
- Consider using 💡 emoji in title
- Keep it brief but actionable
- Include enough context for future understanding

### Multiple Related Items
If the user provides multiple related pieces of information:
- You may combine them into a single inbox entry if they're closely related
- OR create separate entries if they belong to different topics
- Use your judgment based on content and context

## Inbox Processing (For Reference)

The information stored in inbox.md will be processed later following this workflow:

1. **Read** each item during scheduled processing session (typically Sunday evening)
2. **Decide** where it belongs (create new file or add to existing)
3. **Move** content to appropriate location in `personal-memory/`
4. **Archive** the entry to `processed-inbox-audit/[YYYY-MM]-processed-inbox-audit.md`
5. **Update** `personal-memory-index.md` if new folders were created

**Note**: You don't need to process the inbox immediately - just capture the information. The user will process it during their scheduled session.

## Examples

### Example 1: Web Bookmark
```markdown
## [2026-02-11 14:30] DLS Virtual Assistant PRFAQ

Amazon WorkDocs document containing the PRFAQ (Press Release and Frequently Asked Questions) for the DLS Virtual Assistant project.

Source: https://amazon.awsapps.com/workdocs-amazon/index.html#/document/11504249130db86cea3e5235b8aae1430706e7096299a0162fb4aa3ca1397afc
```

### Example 2: Personal Information
```markdown
## [2026-02-11 14:32] PAN Number

PAN Number: CSDGS8675r
```

### Example 3: Family Information
```markdown
## [2026-02-11 14:35] Wife's Name

Wife's name: Vyakhya
```

### Example 4: Idea with Emoji
```markdown
## [2026-02-11 14:40] 💡 Project Idea - Auto-organize Photos

Idea to create a script that automatically organizes photos by date and location using EXIF data. Could use Python with PIL library.

Next Steps:
- Research EXIF libraries
- Create proof of concept
- Test with sample photos
```

### Example 5: Learning Note
```markdown
## [2026-02-11 15:00] Python Async/Await Pattern

Learned about async/await in Python for concurrent programming. Key points:
- Use `async def` to define coroutines
- Use `await` to wait for async operations
- Use `asyncio.run()` to execute async main function
- Good for I/O-bound operations

Source: https://docs.python.org/3/library/asyncio.html
```

## Quality Checklist

Before completing, verify:
- [ ] Timestamp is in correct format `[YYYY-MM-DD HH:MM]`
- [ ] Title is descriptive and searchable
- [ ] Content includes all relevant information
- [ ] Source URL is included if applicable
- [ ] Proper markdown formatting is used
- [ ] Entry is added to inbox.md correctly
- [ ] No existing entries were accidentally modified
- [ ] User is informed of successful capture

## Important Reminders

1. **Always add to inbox first** - Never directly create files in personal-memory folders
2. **Include timestamps** - Every entry must have a timestamp
3. **Preserve context** - Include enough information for future understanding
4. **Don't process immediately** - Just capture; processing happens during scheduled sessions
5. **Maintain formatting** - Follow the inbox entry format consistently
6. **Keep inbox clean** - Don't let it exceed 50 items (user will process regularly)

## Error Handling

If inbox.md doesn't exist:
- Create it with proper header: `# Inbox`
- Then add the entry

If adding entry fails:
- Read the file again to check current state
- Retry the operation
- Inform user if issues persist

## Success Criteria

The skill is successful when:
1. Information is captured in inbox.md with proper format
2. Timestamp is accurate and properly formatted
3. All relevant details are included
4. User is notified of successful capture
5. No existing inbox entries are lost or modified

---

**Remember**: This skill focuses on quick capture. The organization and filing will happen during the scheduled inbox processing sessions. Just focus on getting the information safely stored with proper context!