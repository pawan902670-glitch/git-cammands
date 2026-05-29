# Complete Beginner-Friendly Git + GitHub Workflow Guide

This version is more practical, more structured, and explains **why commands matter in real projects** — especially for beginners learning Git with projects like React, Node.js, HTML/CSS, etc.

---

# 1. Terminal & Folder Navigation (Foundation)

Before Git works, you must know how to move inside folders using Terminal/CMD.

Think of Terminal like:

* A **text-based file explorer**
* Where you control folders using commands

---

## `pwd`

### What it does

Shows your current folder location.

### Why use it

Sometimes you forget where you are in Terminal.

```bash
pwd
```

Example:

```bash
C:/Users/Pawan/Desktop
```

---

## `ls`

### What it does

Shows files and folders inside the current directory.

```bash
ls
```

---

## `ls -a`

### What it does

Shows all files including hidden files.

### Why important in Git

Git creates a hidden folder called `.git`.

Use this to verify Git was initialized properly.

```bash
ls -a
```

You may see:

```bash
.git
src
README.md
```

---

## `cd <folder_name>`

### What it does

Moves into a folder.

```bash
cd project
```

### Real Use

Before running Git commands, you must enter your project folder.

---

## `cd ..`

### What it does

Moves one folder backward.

```bash
cd ..
```

### Real Use

Useful when you entered the wrong folder.

---

## `mkdir <folder_name>`

### What it does

Creates a new folder.

```bash
mkdir myproject
```

### Real Use

Used when starting a brand-new project.

---

## `touch <file_name>`

### What it does

Creates an empty file.

```bash
touch index.html
```

### Real Use

Quickly create files without opening VS Code.

---

# 2. Understanding Git First

Git is a:

* **Version Control System**

Meaning:

* It tracks file changes
* Stores project history
* Lets you restore old versions
* Helps teams collaborate safely

---

# 3. Starting Git in a Project

## `git init`

### What it does

Turns a normal folder into a Git repository.

```bash
git init
```

### What happens internally

Git creates:

```bash
.git
```

This hidden folder stores:

* commit history
* branches
* tracking data
* configurations

---

## Why this command matters

Without `git init`:

* Git cannot track changes
* `git add`
* `git commit`
* `git push`

will not work properly.

---

# 4. Git Configuration (Important Reality)

Many beginners misunderstand `git config`.

It is **NOT specifically for React projects**.

It is:

* A one-time setup for Git behavior
* Usually done once after installing Git

---

# 5. Most Important Git Config Commands

## Set Your Name

```bash
git config --global user.name "Pawan"
```

### Why

Your commits will store this name.

---

## Set Your Email

```bash
git config --global user.email "you@example.com"
```

### Why

GitHub uses this email to identify your commits.

---

# 6. Understanding `--global`

## What `--global` means

Applies settings to:

* ALL repositories on your computer

You usually set this:

* once after installing Git

---

## Without `--global`

Settings apply only to the current project.

Example:

```bash
git config user.name "ProjectUser"
```

---

# 7. Line Ending Problem (CRLF vs LF)

## Command

```bash
git config --global core.autocrlf true
```

---

## Why this exists

Different operating systems save line endings differently.

| System      | Line Ending |
| ----------- | ----------- |
| Windows     | CRLF        |
| Linux/macOS | LF          |

Git warns about this sometimes.

---

# 8. Best Setting Recommendation

## If using Windows

```bash
git config --global core.autocrlf true
```

### Why

Git automatically converts line endings safely.

Best for:

* React
* Node.js
* HTML/CSS
* Most normal development

---

## If using Linux/macOS

```bash
git config --global core.autocrlf input
```

---

# 9. Daily Git Workflow (MOST IMPORTANT)

This is the real developer cycle:

```text
Edit Files
   ↓
git status
   ↓
git add
   ↓
git commit
   ↓
git push
```

---

# 10. Check Project Status

## `git status`

### What it does

Shows:

* modified files
* untracked files
* staged files

```bash
git status
```

---

## Why this command is VERY important

This is the:

* "What changed?" command

Use it constantly.

---

# 11. Staging Files

## `git add .`

### What it does

Stages ALL changed files.

```bash
git add .
```

Think of it as:

> "Prepare these files for saving."

---

## Add Single File

```bash
git add app.js
```

Useful when:

* you only want one file committed

---

# 12. Commit = Save Point

## `git commit -m "message"`

### What it does

Creates a permanent snapshot.

```bash
git commit -m "added login page"
```

---

## Why commit messages matter

Good messages help:

* teammates
* future you
* debugging

---

## Good Examples

```bash
git commit -m "fixed navbar bug"
```

```bash
git commit -m "created authentication system"
```

---

# 13. Local vs Remote (VERY IMPORTANT CONCEPT)

## Local Repository

Exists:

* on YOUR computer

---

## Remote Repository

Exists:

* on GitHub/GitLab/Bitbucket

---

# Visual Understanding

```text
Your Computer  ←→  GitHub Server
(Local Repo)       (Remote Repo)
```

---

# 14. Check Remote Connection

## `git remote -v`

### What it does

Checks if GitHub is connected.

```bash
git remote -v
```

---

## If empty

Means:

* your project is NOT connected to GitHub yet

---

# 15. Connect GitHub Repository

## `git remote add origin <URL>`

Example:

```bash
git remote add origin https://github.com/user/project.git
```

---

## What is `origin`?

`origin` is simply:

* the nickname of your GitHub repository

You can technically name it anything:

```bash
git remote add myrepo URL
```

But developers usually use:

```bash
origin
```

---

# 16. Upload Code to GitHub

## `git push origin main`

### What it does

Uploads commits to GitHub.

```bash
git push origin main
```

---

# Meaning Breakdown

| Part   | Meaning          |
| ------ | ---------------- |
| git    | use Git          |
| push   | upload           |
| origin | remote repo name |
| main   | branch name      |

---

# 17. First Push Sometimes Needs This

```bash
git push -u origin main
```

---

## Why `-u` is useful

It creates a permanent connection between:

* local branch
* remote branch

After this you can simply use:

```bash
git push
```

---

# 18. Real Beginner Workflow Example

## Step 1 — Create Folder

```bash
mkdir react-project
```

---

## Step 2 — Enter Folder

```bash
cd react-project
```

---

## Step 3 — Initialize Git

```bash
git init
```

---

## Step 4 — Create Files

```bash
touch README.md
```

---

## Step 5 — Check Status

```bash
git status
```

---

## Step 6 — Stage Files

```bash
git add .
```

---

## Step 7 — Commit Files

```bash
git commit -m "initial commit"
```

---

## Step 8 — Connect GitHub

```bash
git remote add origin YOUR_URL
```

---

## Step 9 — Push Code

```bash
git push -u origin main
```

---

# 19. Most Important Beginner Understanding

Git has 3 major areas:

```text
Working Directory
       ↓
Staging Area
       ↓
Repository (Commit History)
```

---

# Simple Meaning

| Area              | Meaning                   |
| ----------------- | ------------------------- |
| Working Directory | files you're editing      |
| Staging Area      | selected files for commit |
| Repository        | permanently saved history |

---

# 20. Golden Rule for Beginners

Always follow:

```bash
git status
git add .
git commit -m "message"
git push
```

This becomes your daily developer habit.
