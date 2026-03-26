---
type: reference
topic: [vault, obsidian, getting-started]
created: 2026-03-26
---

# Getting Started

Welcome to your Obsidian vault! This is your personal knowledge management system — a place to capture thoughts, track tasks, learn new things, and build a web of connected notes.

## The Daily-First Workflow

The most important idea: **everything starts in your daily note**.

Each day, create a note in `_daily/` named with today's date (e.g. `2026-03-26.md`). This is where you:
- Jot down thoughts and observations
- Track tasks and to-dos
- Log what you worked on
- Capture ideas to explore later

Most things will stay in your daily note forever — and that's fine. Only create a dedicated file when a topic grows big enough to deserve its own space.

## Wikilinks — Connecting Your Notes

The power of Obsidian is **bidirectional linking**. When you write `[[Note Name]]`, it creates a link to that note — and that note automatically knows it's being linked to.

Examples:
- `[[Getting Started]]` — links to this note
- `[[2026-03-26]]` — links to a daily note
- `[[My Project]]` — links to a note that may not exist yet (Obsidian shows it as a broken link until you create it)

Over time, these links form a knowledge graph — a web of connected ideas that grows with you.

## Tags

Tags help categorise notes. Add them after the heading:

```markdown
# My Note
#personal #learning
```

Keep it simple. Common tags:
- `#personal` — personal life notes
- `#learning` — things you're studying
- `#project` — project-related notes

## Folder Structure

| Folder | What goes here |
|--------|---------------|
| `_daily/` | Daily notes (one per day) |
| `_inbox/` | Quick captures — process into daily notes later |
| `_attachments/` | Images, PDFs, files |
| `Personal/Notes/` | Reference notes and knowledge |
| `Personal/Projects/` | Project folders (one subfolder per project) |
| `Learning/Topics/` | Subjects you're studying long-term |
| `Learning/Skills/` | How-to guides and procedures |
| `__system/Templates/` | Note templates |

## Creating a Daily Note

1. Create a new file in `_daily/` named `YYYY-MM-DD.md`
2. Use the template from `__system/Templates/Daily.md`
3. Or just start writing — the format is simple:

```markdown
---
type: daily
date: 2026-03-26
---
# 2026-03-26

---

## Notes
- Had a great idea about...
- Learned that...

## Tasks
- [ ] Do this thing
- [x] Already did this

---
```

## When to Create a Dedicated Note

Ask yourself: "Will I look for this information again?" If yes, and it's grown beyond a few lines in a daily note, give it its own file.

**Good candidates for dedicated notes:**
- A recipe you want to keep
- A procedure you'll repeat (how to set something up)
- Notes on a topic you're actively learning
- A project with multiple tasks and phases

**See also:** [[Example Reference Note]] for how to structure a dedicated note.

## Tips

- **Don't overthink organisation** — start messy, refine later
- **Link generously** — the more links, the more useful the graph
- **Use daily notes as a safety net** — if you're not sure where something goes, put it in today's daily note
- **Let Claude help** — ask Claude to create notes, organise information, or find connections
