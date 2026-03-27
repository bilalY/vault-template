---
type: reference
topic: [vault, syncthing, setup]
created: 2026-03-27
---

# Adding a New Device

Already set up and working? This guide covers adding a new laptop, tablet, or phone to your vault sync.

**What you need before starting:**
- Your VM is running and Syncthing is active on it
- You can connect to the VM via Termius (for the web UI step)

---

## Adding a New Laptop (Windows)

### 1. Install Syncthing

Download and install from [syncthing.net](https://syncthing.net/downloads/). It runs in the system tray.

### 2. Set a GUI Password

Syncthing opens a web UI at `http://localhost:8384` on first launch. Go to **Actions > Settings > GUI** and set a username and password.

### 3. Get the VM's Device ID

You need the VM's Syncthing Device ID. Open Termius, connect to the AI Server, then:

1. Set up SSH port forwarding if you haven't already:
   - Edit your VM host in Termius > **Port Forwarding**
   - Add a **Local** rule: Port `8384`, Destination `127.0.0.1:8384`
2. Connect via SSH
3. Open `http://localhost:8384` in your browser (this shows the **VM's** Syncthing UI)
4. Go to **Actions > Show ID** — copy the Device ID

### 4. Connect to the VM

Back on your **laptop's** Syncthing web UI (`http://localhost:8384` — make sure you're on the right one):

1. Click **Add Remote Device**
2. Paste the VM's Device ID
3. Set the address to the VM's Tailscale IP: `tcp://[tailscale-ip]:22000`
4. Click **Save**

### 5. Approve on the VM

On the VM's Syncthing web UI, a notification appears asking to add your new laptop. Click **Add Device**.

### 6. Share the Vault Folder

On the VM's web UI:
1. Click the **Vault** folder > **Edit** > **Sharing** tab
2. Tick your new laptop > **Save**

On your laptop's web UI:
1. A prompt appears to accept the **Vault** folder
2. Choose where to store it (e.g. `C:\Users\[you]\Documents\vault`)
3. Click **Save**

Sync begins — wait for it to finish (check "Up to Date" on both sides).

### 7. Install Obsidian

1. Download from [obsidian.md](https://obsidian.md)
2. Choose **Open folder as vault**
3. Select the synced vault folder
4. Done — your notes are live

### 8. Install Recommended Apps

| App | Purpose |
|-----|---------|
| **Wispr Flow** | Voice-to-text dictation — [wispr.com](https://wispr.com) |
| **Obsidian Web Clipper** | Save web pages to vault — install from your browser's extension store |
| **Termius** | SSH into the VM for Claude Code sessions — [termius.com](https://termius.com) |
| **Tailscale** | Connect to the VM from outside your home network — [tailscale.com](https://tailscale.com) |

---

## Adding a New Laptop (Mac)

Same process as Windows, with these differences:

- Install Syncthing from [syncthing.net](https://syncthing.net/downloads/) or `brew install syncthing`
- Choose a vault folder like `~/Documents/vault`
- Everything else is identical — follow the Windows steps above

---

## Adding a New Phone or Tablet

### 1. Install Syncthing

| Platform | App |
|----------|-----|
| **Android** | **Syncthing-Fork** from the Play Store |
| **iOS** | **Möbius Sync** from the App Store |

### 2. Get the VM's Device ID

Same as the laptop steps — use Termius with SSH port forwarding to access the VM's Syncthing web UI and copy the Device ID from **Actions > Show ID**.

Or if you already have it saved from setting up another device, reuse it — the Device ID doesn't change.

### 3. Add the VM as a Device

In the Syncthing app on your phone/tablet:
1. Go to **Devices** > **Add Device** (or **+**)
2. Paste the VM's Device ID
3. Set the address to the VM's Tailscale IP: `tcp://[tailscale-ip]:22000`
4. Save

### 4. Approve on the VM

On the VM's Syncthing web UI, approve the new device when the notification appears.

### 5. Share the Vault Folder

On the VM's web UI:
1. Click the **Vault** folder > **Edit** > **Sharing** tab
2. Tick the new device > **Save**

On the phone/tablet app:
1. Accept the folder share when prompted
2. Choose a local folder to store the vault

### 6. Install Obsidian

1. Install **Obsidian** from the App Store / Play Store
2. Choose **Open folder as vault**
3. Select the synced vault folder

### 7. Install Recommended Apps (Android)

| App | Purpose |
|-----|---------|
| **Hackers Keyboard** | Full keyboard with Ctrl/Tab/Esc — essential for Termius |
| **Termius** | SSH into the VM for Claude Code sessions |
| **Tailscale** | Connect to the VM from outside your home network |

---

## Replacing an Old Device

If you're replacing a laptop or phone (not adding a second one):

1. Set up the new device using the steps above
2. Wait for the vault to fully sync (both sides show "Up to Date")
3. On the VM's Syncthing web UI, remove the old device:
   - Click the old device > **Edit** > **Remove**
4. Uninstall Syncthing from the old device

Your vault data stays on the VM — nothing is lost by removing an old device.

---

## Troubleshooting

### Devices stuck on "Disconnected"

- Check that Tailscale is running on both devices
- Set the device address explicitly: `tcp://[tailscale-ip]:22000` (don't rely on `dynamic`)
- On Android, check that Syncthing-Fork has permission to run in the background and isn't being killed by battery optimisation

### Sync is very slow

First sync can take a while if the vault is large. Subsequent syncs are fast (only changes are transferred). Be patient on the initial sync.

### "Folder path does not exist" on phone

Create the folder manually first, then point Syncthing to it.

### Can't access VM's Syncthing web UI

Make sure SSH port forwarding is set up in Termius:
- Local port: `8384`
- Destination: `127.0.0.1:8384`

Connect via SSH first, then open `http://localhost:8384` in a browser on the same device.

---

## See Also

- [[Vault Workflow]] — how sync works across all your devices
- [[Getting Started]] — vault structure and daily-first workflow
- [[Claude Code Basics]] — using Claude Code via Termius
