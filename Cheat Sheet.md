---
type: reference
topic: [vault, shortcuts, quick-reference]
created: 2026-03-27
---

# Cheat Sheet

Quick reference for terminal shortcuts, commands, and vault conventions.

## Terminal Aliases

| Alias | What it does |
|-------|-------------|
| `v` | Go to vault (`cd ~/repos/vault`) |
| `vs` | Vault git status |
| `vp` | Pull latest vault changes |
| `vc` | Commit and push vault changes |
| `cc` | Open vault in Claude Code |
| `gm` | Open vault in Gemini CLI |
| `cx` | Open vault in Codex |
| `r` | Go to repos folder (`cd ~/repos`) |
| `s` | Go to storage (`cd ~/storage`) |

## Session Workflow

```
vp          ← pull latest
cc          ← start Claude (or gm / cx)
... work ...
            ← tell Claude to wrap up (session log + commit + push)
```

Manual commit if needed:
```bash
vc
```

## tmux (Session Persistence)

| Command | What it does |
|---------|-------------|
| `tmux new -s work` | Start a named session |
| `Ctrl+B` then `D` | Detach (session keeps running) |
| `tmux attach -t work` | Reattach to session |
| `tmux ls` | List active sessions |
| `tmux kill-session -t work` | Kill a session |

## Git Basics

| Command | What it does |
|---------|-------------|
| `git status` | See what's changed |
| `git pull origin main` | Get latest from GitHub |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Commit with a message |
| `git push origin main` | Push to GitHub |
| `git log --oneline -10` | Last 10 commits |

## Vault Conventions

| What | Where |
|------|-------|
| Daily notes | `_daily/YYYY-MM-DD.md` |
| Quick captures | `_inbox/` |
| Reference notes | `Personal/Notes/` |
| Projects | `Personal/Projects/[name]/` |
| Learning topics | `Learning/Topics/` |
| How-to guides | `Learning/Skills/` |
| Attachments | `_attachments/` |
| Templates | `__system/Templates/` |

## Note Frontmatter

```yaml
---
type: reference       # daily, reference, project, etc.
topic: [tag1, tag2]
created: YYYY-MM-DD
---
```

## Wikilinks

| Syntax | Result |
|--------|--------|
| `[[Note Name]]` | Link to a note |
| `[[Note Name\|Display Text]]` | Link with custom text |
| `![[Note Name]]` | Embed a note inline |
| `![[image.png]]` | Embed an image |

## Task Checkboxes

| Syntax | State |
|--------|-------|
| `- [ ]` | Todo |
| `- [x]` | Done |
| `- [/]` | In progress |
| `- [>]` | Scheduled |
| `- [-]` | Cancelled |

## Things to Tell Claude

| When | Say |
|------|-----|
| End of session | "Update daily note, commit and push" |
| Save conversation | "Dump this conversation to a file" |
| Remember something | "Remember that I prefer [X]" |
| Context getting high | "Save the important parts to a note before compacting" |

## See Also

- [[Getting Started]] — vault overview
- [[Vault Workflow]] — how sync works across devices
- [[Claude Code Basics]] — Claude Code concepts and usage
- [[Adding a New Device]] — onboard a new laptop or phone
