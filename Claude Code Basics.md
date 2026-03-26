---
type: reference
topic: [claude-code, ai, getting-started]
created: 2026-03-26
---

# Claude Code Basics

Claude Code is an AI assistant that lives in your terminal. It can read your files, write code, create notes, answer questions, and help you get things done — all through a conversational interface.

## Starting a Session

Every session follows this pattern:

```bash
# 1. Navigate to your vault
cd ~/repos/vault

# 2. Pull latest changes (in case you edited on mobile)
git pull origin main

# 3. Start Claude
claude
```

You're now in a conversation with Claude. Type naturally — ask questions, give instructions, describe what you want.

## What Claude Can Do

**In your vault:**
- Create and edit notes
- Organise information into the right folders
- Find connections between your notes
- Create daily notes and log entries
- Help you think through problems

**With code:**
- Write, debug, and explain code
- Set up projects
- Run commands
- Help you learn programming concepts

**Research and thinking:**
- Answer questions about anything
- Break down complex topics
- Help you plan projects
- Draft writing

## Example Prompts

Here are some things you can say to Claude:

| What you want | What to say |
|--------------|-------------|
| Create today's daily note | "Create today's daily note" |
| Capture a thought | "Add to today's daily note: I had an idea about..." |
| Learn something | "Explain how [topic] works in simple terms" |
| Create a reference note | "Create a note about [topic] in Personal/Notes/" |
| Find information | "What notes do I have about [topic]?" |
| Plan a project | "Help me plan out [project name]" |
| Understand code | "Explain what this code does" |

## Session Workflow

Claude always follows these rules (from the CLAUDE.md file):

1. **To-do list** — Claude creates a task list for complex work so you can see progress
2. **Session log** — at the end of every session, Claude updates today's daily note with what was done
3. **Commit and push** — changes are committed to git so they sync to your other devices

## After Your Session

When you're done chatting with Claude, exit and save your work:

```bash
# Exit Claude (type 'exit' or press Ctrl+C)

# Save and sync your changes
git add .
git commit -m "Session: $(date '+%Y-%m-%d')"
git push origin main
```

Or use the shortcut alias: `vc` (vault commit — does all of the above in one command).

## The CLAUDE.md File

Every repository has a `CLAUDE.md` file at its root. This is Claude's instruction manual — it tells Claude:
- How the vault is structured
- What rules to follow (like session logging)
- What conventions to use

You can edit this file to customise Claude's behaviour. For example, if you want Claude to always use a specific writing style, add it to CLAUDE.md.

## Tips

- **Be specific** — "Create a note about my trip to London with dates and highlights" works better than "Make a note"
- **Ask Claude to explain** — if Claude does something you don't understand, ask "Why did you do that?"
- **Iterate** — start simple, then ask Claude to refine or expand
- **Check the daily note** — after each session, your daily note has a log of what happened
- **Use it daily** — the more you use Claude, the more useful your vault becomes
