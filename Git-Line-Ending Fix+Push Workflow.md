# Git Line Ending Fix + Push Workflow Notes

## 1. Command

```bash
git config --global core.autocrlf true
```

---

# What does this command do?

This command tells Git:

> "Automatically manage line endings on Windows."

---

# Why is this needed?

Different operating systems use different line endings.

| Operating System | Line Ending |
| ---------------- | ----------- |
| Windows          | CRLF        |
| Linux/macOS      | LF          |

When working on React, Vite, or other projects on Windows, Git may show warnings like:

```bash
LF will be replaced by CRLF
```

This happens because:

* Project files use LF
* Windows prefers CRLF

---

# What happens after running this command?

## While downloading/checking out files

Git converts:

```text
LF → CRLF
```

So files work properly on Windows.

---

## While committing files

Git converts:

```text
CRLF → LF
```

So repository files stay clean and consistent.

---

# Meaning of `--global`

```bash
--global
```

means:

* Apply this setting to all Git projects
* You only need to run it once

---

# Benefits

✅ Removes most LF/CRLF warnings
✅ Better compatibility on Windows
✅ Keeps Git repository clean
✅ Standard setting for Windows developers

---

# Check if setting is applied

Run:

```bash
git config --global --get core.autocrlf
```

Expected output:

```bash
true
```

---

# Full Git Workflow (Push to GitHub)

## Step 1 — Configure Git (one time)

```bash
git config --global core.autocrlf true
```

---

## Step 2 — Check project status

```bash
git status
```

Shows:

* modified files
* untracked files
* current branch

---

## Step 3 — Add files

```bash
git add .
```

Meaning:

* Add all files to staging area

---

## Step 4 — Commit files

```bash
git commit -m "initial commit"
```

Meaning:

* Save project snapshot

---

## Step 5 — Check GitHub remote

```bash
git remote -v
```

Shows connected GitHub repository.

---

## Step 6 — Add GitHub repository (if not connected)

```bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

---

## Step 7 — Push project to GitHub

```bash
git push -u origin main
```

If branch name is `master`:

```bash
git push -u origin master
```

---

# Future Push Workflow

After making changes:

```bash
git add .
git commit -m "update message"
git push
```

---

# Short Reminder

```bash
git add .
git commit -m "message"
git push
```

These are the 3 most-used Git commands.
