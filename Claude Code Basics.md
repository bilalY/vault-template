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

## Ending a Session Well

This is the most important part. Before you finish, **always tell Claude to wrap up**. Say something like:

- "Update the daily note, commit and push"
- "Log what we did, commit everything, and push"
- "Wrap up — session log, commit, push"

Claude will:
1. Add a summary to today's daily note (what was done, links to files changed)
2. Commit all changes to git
3. Push to GitHub

If you just close the terminal without doing this, your work is still saved locally (Syncthing will sync it), but there's no session log and no git backup. **Get into the habit of wrapping up properly.**

If Claude doesn't offer to do this automatically, remind it — it should, but long sessions can sometimes lose track.

### Manual Fallback

If Claude has already exited, you can commit manually:

```bash
git add .
git commit -m "Session: $(date '+%Y-%m-%d')"
git push origin main
```

Or use the shortcut alias: `vc` (vault commit — does all of the above in one command).

## Saving Conversations

### Why Save Conversations?

Claude's context window is limited. During long sessions, Claude **compacts** the conversation — it summarises older messages to free up space. This means earlier details can be lost or simplified. If you've had a particularly useful or detailed conversation, save it before that happens.

Saved conversations are also much easier to read back later than scrolling through terminal output.

### How to Save

Ask Claude to dump the conversation to a file:

- "Save this conversation to a file in Personal/Notes/"
- "Dump this session to a markdown file"
- "Export our conversation about [topic] to a note"

Claude will create a readable Markdown file with the key content from your conversation. This is especially useful for:

- **Long research sessions** — where Claude explained something in detail
- **Planning sessions** — where you worked through decisions together
- **Before context gets high** — if you see 🟠 or 🔴, consider saving important parts
- **Complex troubleshooting** — so you have a record of what was tried

### Memory

Claude has a memory system that persists between sessions. If you want Claude to remember something for next time (a preference, a decision, context about a project), tell it:

- "Remember that I prefer [X]"
- "Save to memory that [project] uses [technology]"
- "Remember this decision: we chose [X] because [Y]"

This is different from conversation saving — memory stores short facts and preferences, not full conversations. Both are useful.

## The CLAUDE.md File

Every repository has a `CLAUDE.md` file at its root. This is Claude's instruction manual — it tells Claude:
- How your vault is structured
- What rules to follow (like session logging)
- What conventions to use

You can edit this file to customise Claude's behaviour. For example, if you want Claude to always write in a certain style, add it to CLAUDE.md.

## How Claude Code Works

### The Conversation

When you type a message, Claude reads it, thinks about it, and responds. It can also use **tools** — reading files, writing files, running commands, searching the web — to get things done. You'll see it working in real time.

### Context Window

Claude has a **context window** — a limit on how much it can "remember" in a single conversation. Think of it as a desk: Claude can only have so many documents open at once. The statusline shows your context usage as a percentage with a colour-coded indicator:

- 🟢 Under 50% — plenty of room
- 🟡 50-75% — getting full
- 🟠 75-90% — running low
- 🔴 Over 90% — almost full

When context gets high, Claude automatically **compacts** the conversation — it summarises older messages to free up space, so you can keep working without starting over. You might see a brief pause when this happens. If a session has been going for a very long time and feels sluggish, starting fresh (`exit` then `claude`) is always an option.

Claude reads the CLAUDE.md file at the start of every session, so it always knows your vault's rules and structure.

### CLAUDE.md — Claude's Instruction Manual

The `CLAUDE.md` file at the root of your vault tells Claude:
- How your vault is structured
- What rules to follow (session logging, to-do lists)
- Where things live (`~/repos/`, `~/storage/`)
- Any preferences you have

**This is how you customise Claude.** Want Claude to always write in a certain style? Add it to CLAUDE.md. Want it to follow specific rules for a project? Add them. Claude reads this file at the start of every conversation.

### Agents

Agents are specialised versions of Claude that focus on specific tasks. They run as sub-processes — Claude launches them when needed. For example, an agent might explore your codebase, research a topic, or review code.

You don't need to manage agents directly — Claude uses them automatically when a task benefits from specialised focus.

### Skills

Skills are pre-written prompts you trigger with a slash command. They're shortcuts for common tasks:

- `/commit` — commit your changes with a good message
- `/review` — review code changes

Type `/` in Claude to see available skills. Your vault can define custom skills in `.claude/skills/`.

### MCP Servers

MCP (Model Context Protocol) servers give Claude access to external tools and services — things like GitHub, web browsing, and databases. They extend what Claude can do beyond just reading and writing local files.

Your setup includes MCP servers for GitHub and web access. More can be added over time.

### Models

Claude comes in different models:

| Model | Icon | Best for |
|-------|------|----------|
| **Opus** | 💎 | Complex reasoning, large tasks, deep analysis |
| **Sonnet** | 🎵 | Balanced — good for most tasks |
| **Haiku** | 🍃 | Fast, lightweight tasks |

The statusline shows which model you're using. You can switch with `/model`.

## Tips

- **Be specific** — "Create a note about my trip to London with dates and highlights" works better than "Make a note"
- **Ask Claude to explain** — if Claude does something you don't understand, ask "Why did you do that?"
- **Iterate** — start simple, then ask Claude to refine or expand
- **Check the daily note** — after each session, your daily note has a log of what happened
- **Use it daily** — the more you use Claude, the more useful your vault becomes
