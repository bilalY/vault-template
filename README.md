# Obsidian Vault Template

A starter Obsidian vault designed for use with [Claude Code](https://claude.ai/code). Daily-first workflow, minimal structure, ready to go.

## Quick Start

1. Click **Use this template** > **Create a new repository** (private recommended)
2. Clone to your server: `git clone git@github.com:[you]/vault.git ~/repos/vault`
3. Open in Claude Code: `cd ~/repos/vault && claude`
4. On mobile: sync with Syncthing, open in Obsidian

## What's Included

```
├── _daily/                          # Daily notes (your main entry point)
├── _inbox/                          # Quick captures
├── _attachments/                    # Images and files
├── __system/Templates/Daily.md      # Daily note template
├── Personal/Notes/                  # Reference notes
├── Personal/Projects/               # Project folders
├── Learning/Topics/                 # Long-term learning
├── Learning/Skills/                 # How-to guides
├── Getting Started.md               # Vault onboarding guide
├── Claude Code Basics.md            # How to use Claude Code
├── CLAUDE.md                        # Instructions for Claude Code
└── .gitignore                       # Excludes Obsidian workspace files
```

## How It Works

- **Everything starts in daily notes** — one note per day in `_daily/YYYY-MM-DD.md`
- **Create dedicated files only when needed** — when a topic outgrows a daily note
- **Wikilinks** (`[[Note Name]]`) connect notes into a knowledge graph
- **Claude Code** reads `CLAUDE.md` and follows your vault's conventions automatically

## Starter Notes

| Note | Purpose |
|------|---------|
| [Getting Started](Getting%20Started.md) | Vault workflow, wikilinks, tags, folder structure |
| [Claude Code Basics](Claude%20Code%20Basics.md) | Starting sessions, example prompts, session workflow |
| [Example Reference Note](Personal/Notes/Example%20Reference%20Note.md) | Shows proper note structure with frontmatter |

## Session Workflow

```bash
cd ~/repos/vault
git pull origin main    # Sync latest changes
claude                  # Start Claude Code
# ... work ...
git add . && git commit -m "Session: $(date '+%Y-%m-%d')" && git push origin main
```

Claude will create a to-do list for complex tasks and log a summary in your daily note at the end of each session.

## Customising

- Edit `CLAUDE.md` to change how Claude behaves in your vault
- Add folders as your needs grow
- Install Obsidian plugins (Community Plugins > Browse) to extend functionality
