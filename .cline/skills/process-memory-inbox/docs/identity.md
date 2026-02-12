# Processing Personal and Identity Information

**When to use**: Personal documents, family information, contacts, sensitive data

## Storage Location
- `personal-memory/identity/personal-info.md` - Main file for identity and personal data
- Create additional files if needed (e.g., `contacts.md`, `documents.md`)

## How to Process

1. **Identify the type of information**:
   - Official documents (PAN, Passport, Aadhaar, licenses)
   - Family information (names, birthdays, relationships)
   - Contact information
   - Emergency contacts
   - Other personal data

2. **Add to appropriate section** in `personal-info.md`:

```markdown
## Official Documents

### [Document Type]
- **[Field]**: [Value]
- **[Field]**: [Value]

## Family

### [Relationship]
- **Name**: [Name]
- **Birthday**: [Date] (if applicable)
- **Notes**: [Additional info]

## Contacts

### [Contact Type]
- **Name**: [Name]
- **Phone**: [Number]
- **Email**: [Email]
```

## Example

**Inbox Entry:**
```markdown
## [2026-02-11 12:02] PAN Number

PAN Number: CSDGS8675r
```

**Result in identity/personal-info.md:**
```markdown
## Official Documents

### PAN Number
- **PAN**: CSDGS8675r
```

**Another Example - Family Info:**
```markdown
## [2026-02-11 12:03] Wife's Name

Wife's name: Vyakhya
```

**Result:**
```markdown
## Family

### Spouse
- **Name**: Vyakhya
```

## Security Considerations
- Consider if sensitive data needs encryption (discuss with user)
- Use appropriate section headers for organization
- Keep information up-to-date
- Don't include passwords or highly sensitive credentials in plain text

## Tips
- Create sections for different types (Official Documents, Family, Contacts, etc.)
- Keep organized and searchable
- Update "Last Updated" date when adding information
- Consider creating separate files for extensive contact lists