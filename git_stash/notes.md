# Git Notes - Chapter 4: `git stash`

---

# Topic: `git stash`

## What is `git stash`?

`git stash` is a Git command used to **temporarily save uncommitted changes** (both modified and staged files) without creating a commit.

After saving the changes, Git restores your project to the **last committed state**, so your working directory becomes clean.

### One-Line Definition

> **`git stash` temporarily saves your unfinished work and restores your project to the last committed version without creating a commit.**

---

# Why do we need `git stash`?

Imagine you are developing a Login Page.

Current progress:

* Login UI ✅
* Validation 🚧 (Incomplete)

Suddenly your team lead says:

> "A production bug has been reported. Fix it immediately."

You cannot:

❌ Commit incomplete code.

❌ Delete your unfinished work.

Instead, use

```bash
git stash
```

Git safely stores your unfinished work.

Now your project becomes clean.

After fixing the bug, you can continue your previous work.

---

# Prerequisites

Before learning `git stash`, you should know:

* git init
* git add
* git commit
* git status

---

# Git Internal Structure

Git has three important areas.

```text
                 Working Directory
             (Where you write code)

                       │
                git add
                       │

                       ▼

                 Staging Area
           (Ready for next commit)

                       │
              git commit
                       │

                       ▼

               Local Repository
             (Commit History)
```

`git stash` creates another temporary storage.

```text
Working Directory

        │

git stash

        ▼

Git Stash (Temporary Storage)
```

---

# Practical Execution (Step by Step)

## Step 1 - Create a Project

```bash
mkdir git_stash
```

Creates a new folder.

---

Move inside

```bash
cd git_stash
```

---

Initialize Git

```bash
git init
```

Output

```text
Initialized empty Git repository
```

What happened?

Git created a hidden `.git` folder.

Now this folder is a Git repository.

---

## Step 2 - Create a File

```bash
echo "<h1>Hello</h1>" > index.html
```

Check file

```bash
cat index.html
```

Output

```html
<h1>Hello</h1>
```

---

## Step 3 - Check Git Status

```bash
git status
```

Output

```text
Untracked files:

index.html
```

Meaning

Git can see the file.

But it is NOT tracking it yet.

---

## Step 4 - Track the File

```bash
git add .
```

Check

```bash
git status
```

Output

```text
Changes to be committed:

new file: index.html
```

Meaning

The file is ready to be committed.

---

## Step 5 - Commit

```bash
git commit -m "First Commit"
```

Check

```bash
git status
```

Output

```text
nothing to commit, working tree clean
```

Meaning

Everything has been saved.

---

## Step 6 - Modify the File

Append new content.

```bash
echo "<p>Learning Git Stash</p>" >> index.html
```

Check

```bash
cat index.html
```

Output

```html
<h1>Hello</h1>
<p>Learning Git Stash</p>
```

---

## Step 7 - Check Status

```bash
git status
```

Output

```text
modified: index.html
```

Meaning

The file has changed after the last commit.

---

## Step 8 - Save the Unfinished Work

Run

```bash
git stash
```

Example Output

```text
Saved working directory and index state WIP on main
```

Meaning

Git has stored your unfinished work in the stash.

---

## Step 9 - Check Status Again

```bash
git status
```

Output

```text
nothing to commit, working tree clean
```

Meaning

Your working directory is clean again.

---

## Step 10 - Check the File

```bash
cat index.html
```

Output

```html
<h1>Hello</h1>
```

Question

Where did

```html
<p>Learning Git Stash</p>
```

go?

Answer

Git stored it safely inside the stash.

It is NOT deleted.

---

# How to Verify the Stash

Run

```bash
git stash list
```

Example

```text
stash@{0}: WIP on main: First Commit
```

Meaning

Your unfinished work is safely stored.

---

# How to See What Is Inside the Stash

Run

```bash
git stash show -p
```

Example

```diff
diff --git a/index.html b/index.html

@@

 <h1>Hello</h1>
+<p>Learning Git Stash</p>
```

The **+** means that line is stored in the stash.

---

# How to Restore the Stash

Run

```bash
git stash pop
```

Output

```text
Dropped refs/stash@{0}
```

Meaning

Git restored your work and removed that stash entry.

Check

```bash
cat index.html
```

Output

```html
<h1>Hello</h1>
<p>Learning Git Stash</p>
```

Your changes are back.

---

# Internal Working

Before

```text
Working Directory

Hello
Learning Git Stash
```

Run

```bash
git stash
```

After

```text
Working Directory

Hello

↓

Git Stash

Hello
Learning Git Stash
```

Run

```bash
git stash pop
```

Result

```text
Working Directory

Hello
Learning Git Stash
```

---

# Real-Life Example

Imagine you are writing an assignment.

Teacher suddenly says:

> "Leave your notebook and solve another question."

You put the notebook in a drawer.

Drawer = Git Stash

Later you take it back.

Notebook = Working Directory

Nothing was lost.

---

# Common Mistakes

### Mistake 1

I thought

```bash
git stash
```

deleted my code.

Wrong.

It only hides your changes.

---

### Mistake 2

I got

```text
No local changes to save
```

Reason

There were no modified or staged files.

Git had nothing to save.

---

### Mistake 3

After running

```bash
git stash
```

my changes disappeared.

Reason

This is normal.

Git restored the project to the last commit.

Use

```bash
git stash list
```

or

```bash
git stash show -p
```

to verify the changes are still stored.

---

# Best Practices

* Always check `git status` before using `git stash`.
* Use `git stash` only for temporary work.
* Restore your work with `git stash pop` when you're ready to continue.
* Don't use `git stash` as a permanent backup.

---

# Frequently Used Commands

Save current work

```bash
git stash
```

View saved stashes

```bash
git stash list
```

View stash contents

```bash
git stash show -p
```

Restore and remove stash

```bash
git stash pop
```

---

# Interview Questions

### What is `git stash`?

It temporarily saves uncommitted changes and cleans the working directory.

### Does `git stash` create a commit?

No.

### Does `git stash` upload code to GitHub?

No.

### Where are stashes stored?

Inside your local Git repository.

### How do you view a stash?

```bash
git stash show -p
```

### How do you restore a stash?

```bash
git stash pop
```

---

# Summary

* `git stash` saves unfinished work temporarily.
* It restores your working directory to the last committed state.
* Your work is not deleted; it is stored in the stash.
* Use `git stash list` to see saved stashes.
* Use `git stash show -p` to inspect them.
* Use `git stash pop` to continue your work later.
