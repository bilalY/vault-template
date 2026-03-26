# CLAUDE.md

Write in UK English unless otherwise specified.
Always create a to-do list so progress can be monitored in the terminal.

## Repository Overview

This is an Obsidian vault — a knowledge management system using Markdown files with bidirectional linking, tags, and graph view.

## Structure

```
/
├── _daily/           # Daily notes — the main entry point for everything
├── _inbox/           # Quick captures to process later
├── _attachments/     # Images and file attachments
├── __system/
│   ├── Templates/    # Note templates
│   └── Dashboards/   # Summary views
├── Personal/
│   ├── Notes/        # Reference notes and knowledge
│   └── Projects/     # Project folders
└── Learning/
    ├── Topics/       # Long-term learning subjects
    └── Skills/       # Specific procedures and how-tos
```

## Design Principles

1. **Daily notes are primary** — everything starts in daily notes. Most things stay there.
2. **Minimal structure** — only create dedicated files when a topic needs its own space.
3. **Use wikilinks** — `[[Note Name]]` creates bidirectional links between notes.
4. **YAML frontmatter** — every note starts with `---` properties block (type, date, etc.).

## Repos and Storage

- **Vault location:** `~/repos/vault/` — this repository
- **Other repos:** `~/repos/[name]/` — any other git repositories live alongside the vault
- **Personal storage:** `~/storage/` — NFS-mounted personal files from TrueNAS (not a git repo, do not commit files from here)

## Task Format

```markdown
- [ ] Task description #personal 📅 2026-01-01
- [x] Completed task ✅ 2026-01-01
- [/] In progress task
- [>] Scheduled for later
- [-] Cancelled task
```

Checkbox states: `[ ]` todo, `[x]` done, `[/]` doing, `[>]` scheduled, `[-]` cancelled

## Working with Notes

- Use `[[Note Name]]` wikilinks for cross-references
- Add YAML frontmatter to every note (see [[Example Reference Note]] for the pattern)
- Keep notes as plain Markdown — Obsidian handles rendering
- Daily notes go in `_daily/YYYY-MM-DD.md`
- Quick captures go in `_inbox/` — process them into daily notes later

## Session Rules

**CRITICAL — these apply to every Claude Code session:**

1. **Always create a to-do list** when working on tasks so progress is visible in the terminal.
2. **Session log is mandatory** — at the end of every session, add an entry to today's daily note (`_daily/YYYY-MM-DD.md`) summarising what was done. Include wikilinks to any files created or modified. If work happened, the daily note must reflect it.
3. **Commit and push** — after making changes, always commit and push to keep the vault in sync.

## When to Create Dedicated Files

Most things stay in daily notes. Create a separate file when:
- A topic has been referenced 3+ times across daily notes
- A project needs its own planning space
- You want to build a knowledge base entry you'll reference often
- A learning topic has 3+ sessions of notes

## Starter Notes

- [[Getting Started]] — how the vault works, daily-first workflow, wikilinks and tags
- [[Claude Code Basics]] — how to use Claude Code, example prompts, session workflow
- [[Example Reference Note]] — shows the pattern for creating reference notes
