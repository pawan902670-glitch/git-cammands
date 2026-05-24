# Beginner Git + VS Code Complete Guide

This guide explains:

* how to use Git commands
* how to use Visual Studio Code
* what each command does in simple words

---

# STEP 1 — Create Folder on Desktop

Create a folder manually.

Example:

```text id="c1"
my-project
```

This folder will contain your project.

---

# STEP 2 — Open Folder in VS Code

Open Visual Studio Code

Click:

```text id="c2"
File → Open Folder
```

Select:

```text id="c3"
my-project
```

---

# STEP 3 — Open Git Bash Terminal

Inside VS Code:

Open terminal:

```text id="c4"
Terminal → New Terminal
```

Then click:

```text id="c5"
+
```

Choose:

```text id="c6"
Git Bash
```

Git Bash is better for Git commands.

---

# STEP 4 — Check Git Version

## Command

```bash id="c7"
git --version
```

## What It Does

Checks Git is installed correctly.

## Example Output

```text id="c8"
git version 2.45.1
```

---

# STEP 5 — Go Inside Folder Using `cd`

## Command

```bash id="c9"
cd Desktop
```

Then:

```bash id="c10"
cd my-project
```

## What It Does

`cd` means:

```text id="c11"
Change Directory
```

It moves terminal into a folder.

---

# STEP 6 — Clone Repository

## Command

```bash id="c12"
git clone "repository-link"
```

## Example

```bash id="c13"
git clone https://github.com/user/demo-project.git
```

## What It Does

Downloads repository from GitHub to your computer.

---

# STEP 7 — Go Inside Repository

## Command

```bash id="c14"
cd demo-project
```

## What It Does

Moves terminal inside cloned repository.

---

# STEP 8 — Create Folder Inside Repository

## Command

```bash id="c15"
mkdir website
```

## What It Does

`mkdir` means:

```text id="c16"
Make Directory
```

Creates new folder.

---

# STEP 8.1 — Create HTML, CSS, JS Files

## Command

```bash id="c17"
touch index.html style.css script.js
```

## What It Does

Creates:

* HTML file
* CSS file
* JavaScript file

---

# STEP 9 — Check Git Status

## Command

```bash id="c18"
git status
```

## What It Does

Shows:

* new files
* modified files
* deleted files

## Example Output

```text id="c19"
Untracked files:
 index.html
 style.css
 script.js
```

Meaning:
Git sees files but not tracking them yet.

---

# STEP 10 — Add Files to Git

## Command

```bash id="c20"
git add .
```

## What It Does

Adds all files to Git tracking.

`.` means:

```text id="c21"
Current folder
```

---

# STEP 11 — Check Status Again

## Command

```bash id="c22"
git status
```

## What It Does

Shows files are ready to commit.

## Example Output

```text id="c23"
Changes to be committed:
 new file: index.html
 new file: style.css
 new file: script.js
```

Meaning:
Files are staged successfully.

---

# STEP 12 — Commit Files

## Command

```bash id="c24"
git commit -m "Added website files"
```

## What It Does

Saves changes into Git history.

`-m` means:

```text id="c25"
Message
```

Commit message explains changes.

---

# STEP 13 — Push Files to GitHub

## Command

```bash id="c26"
git push origin main
```

## What It Does

Uploads files from computer to GitHub.

### Meaning

| Part       | Meaning           |
| ---------- | ----------------- |
| `git push` | Upload changes    |
| `origin`   | GitHub repository |
| `main`     | Branch name       |

---

# COMPLETE COMMAND FLOW

```bash id="c27"
# Check git installation
git --version

# Go to desktop
cd Desktop

# Go inside folder
cd my-project

# Clone repository
git clone https://github.com/user/demo-project.git

# Go inside repository
cd demo-project

# Create folder
mkdir website

# Create files
touch index.html style.css script.js

# Check status
git status

# Add files
git add .

# Check status again
git status

# Commit files
git commit -m "Added website files"

# Push to GitHub
git push origin main
```

---

# SIMPLE MEANING OF IMPORTANT COMMANDS

| Command         | Simple Meaning      |
| --------------- | ------------------- |
| `git --version` | Check Git installed |
| `cd`            | Move inside folder  |
| `git clone`     | Download repository |
| `mkdir`         | Create folder       |
| `touch`         | Create file         |
| `git status`    | Check file status   |
| `git add .`     | Add all files       |
| `git commit`    | Save changes        |
| `git push`      | Upload to GitHub    |

---

# FINAL PROJECT STRUCTURE

```text id="c28"
demo-project/
│
├── website/
│
├── index.html
├── style.css
└── script.js
```
