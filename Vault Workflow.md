---
type: reference
topic: [vault, workflow, syncthing, git]
created: 2026-03-26
---

# Vault Workflow

How your vault stays in sync across all your devices, and how to use it day to day.

## Your Devices

| Device | What it's for | Sync method |
|--------|--------------|-------------|
| **Laptop** | Main editing — Obsidian desktop app | Syncthing (automatic) |
| **Tablet** | Mobile editing — Obsidian mobile app | Syncthing (automatic) |
| **Phone** | Quick capture and reading — Obsidian mobile app | Syncthing (automatic) |
| **VM (AI Server)** | Claude Code sessions via Termius | Syncthing (automatic) + Git (for backup) |

## How Sync Works

**Syncthing** keeps all your devices in sync automatically. When you save a file on one device, it appears on every other device within seconds. You don't need to do anything — it just works in the background.

**Git** is only used on the VM for version history and backup. Claude Code commits and pushes your changes after each session. You don't need to think about git on your laptop, tablet, or phone.

```
Laptop ←→ VM (hub) ←→ Tablet
                ↕
              Phone
```

The VM is always on, so it acts as the central hub. All devices sync to it.

## Daily Workflow

### On Your Laptop or Tablet (Obsidian)

Just open Obsidian and start writing. Everything syncs automatically.

1. Open Obsidian
2. Create today's daily note in `_daily/` (e.g. `2026-03-26.md`)
3. Write notes, add tasks, capture ideas
4. Close Obsidian when done — changes sync to all other devices

### On Your Phone (Obsidian)

Great for quick captures when you're out:

1. Open Obsidian
2. Jot a quick note in `_inbox/` or add to today's daily note
3. Close the app — it syncs when you're back on Wi-Fi

### With Claude Code (via Termius)

When you want AI help:

1. Open Termius on any device
2. Connect to the AI Server
3. Start a session:
   ```bash
   cc
   ```
   (This is a shortcut that opens your vault and starts Claude)
4. Chat with Claude — ask questions, create notes, work on projects
5. When done, Claude commits your changes
6. Changes sync to all your other devices via Syncthing

## The One Rule

**Don't edit the same file on two devices at the same time.**

Syncthing syncs within seconds, so this is easy to avoid:
- Finish editing on one device
- Wait a few seconds
- Start on another device

If you're running a Claude Code session on the VM, don't edit in Obsidian until the session is done.

## What If Something Goes Wrong?

**Sync conflict:** If two devices edit the same file at the same time, Syncthing creates a copy like `note.sync-conflict-20260326.md`. Just open both, keep the one you want, delete the other.

**File missing:** Check if Syncthing is running on your device. On the laptop, look for the Syncthing icon in the system tray. On mobile, open the Syncthing app and check it's connected.

**Changes not appearing:** Wait 30 seconds — sometimes sync takes a moment. If still missing, check that all devices show "Up to Date" in the Syncthing UI.

## Where Things Live

| What | Where | Notes |
|------|-------|-------|
| Daily notes | `_daily/YYYY-MM-DD.md` | One per day, your main entry point |
| Quick captures | `_inbox/` | Process into daily notes later |
| Reference notes | `Personal/Notes/` | Knowledge you'll look up again |
| Projects | `Personal/Projects/` | One subfolder per project |
| Learning | `Learning/Topics/` and `Learning/Skills/` | Things you're studying |
| Attachments | `_attachments/` | Images, PDFs, files |
| Templates | `__system/Templates/` | Note templates |
| Personal files | `~/storage/` (on VM only) | NFS mount to TrueNAS — not in the vault |

## Tips

- **Start with daily notes** — don't worry about organising. Just write in today's daily note.
- **Use `_inbox/` for quick thoughts** — process them into daily notes when you have time.
- **Let Claude help you organise** — ask Claude to move content into dedicated notes when topics grow.
- **Check your phone** — after a Claude Code session, your updated notes appear on all devices within seconds.

## Recommended Apps

| App | What it does | Platform |
|-----|-------------|----------|
| **Wispr Flow** | Voice-to-text dictation — speak instead of typing. Works everywhere including Obsidian and Termius. Great for capturing thoughts quickly or dictating longer notes. | Windows, Mac |
| **Obsidian Web Clipper** | Browser extension that saves web pages and articles directly into your vault as Markdown notes. Useful for research and saving references. | Chrome, Firefox, Safari, Edge |
| **Hackers Keyboard** | Full keyboard with Ctrl, Tab, Esc, and arrow keys — essential for using Termius and Claude Code on a tablet or phone. The default keyboard lacks these keys. | Android |

## See Also

- [[Getting Started]] — vault structure, wikilinks, tags
- [[Claude Code Basics]] — how to use Claude Code
- [[Adding a New Device]] — onboard a new laptop, phone, or tablet
