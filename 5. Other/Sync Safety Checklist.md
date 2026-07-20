---
tags:
  - reference
Type:
aliases:
  - Git Sync Rules
---

# 🔄 Sync Safety Checklist

> The #1 rule: **sync trouble is caused by *divergence* (two devices changing things independently), not by how *much* you change.** A huge edit is safe if the other device pulls it first. A tiny folder rename is dangerous if the other device is behind.

## ✅ The golden workflow (one device at a time)
Treat syncing like passing a baton:
1. **Before editing on a device → Pull first** ("Obsidian Git: Pull" / commit-and-sync).
2. **After editing → Commit-and-sync** and let it finish.
3. **Don't edit on the other device until it has pulled** those changes.

## ⚠️ High-risk operations (handle with care)
These touch *many* files at once, so they collide with almost any concurrent change and merge badly on mobile (which **can't resolve conflicts**):
- **Renaming a folder** (git sees it as delete-all + re-add-all)
- **Moving files/folders**
- **Deleting folders**

**Before ANY of these:**
1. Make **both devices identical first** — pull everywhere, confirm every device says "up to date."
2. Do the change on **one device only** (prefer the laptop).
3. **Push** it, and confirm it landed on GitHub.
4. Only **then** pull on the other device — *before* touching anything else there.

## 🚑 If it breaks (conflict error / doubled folders / missing folders)
1. **Stop editing** on the broken device immediately — don't pile new changes on top.
2. Confirm the good copy: the laptop/GitHub is usually authoritative.
3. **Reset the broken device to match the remote** — on mobile the reliable fix is to **re-clone**:
   - New empty vault → enable Git → add token → "Clone an existing remote repo" → delete the old broken vault.
   - Your data is safe on GitHub; re-cloning just replaces the tangled local copy with the good one.

## 🔧 Settings that help
- Phone Obsidian Git: **Pull on startup = ON**, **commit-and-sync before close**.
- Link format: **"Shortest path when possible"** (Files & links) — keeps links flat so folder moves don't rewrite them to breakable paths.
- Don't rename folders while any device is mid-sync.

## 🧠 Quick gut-check before a big change
- "Is every device fully in sync **right now**?" → if yes, proceed.
- "Am I renaming/moving/deleting folders?" → if yes, use the high-risk protocol above.
