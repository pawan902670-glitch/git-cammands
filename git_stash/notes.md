# Git Notes - Chapter 5: `git stash list` & `git stash pop`

---

# Topic 1 - `git stash list`

## What is `git stash list`?

`git stash list` is used to **display all the stashes stored in your local Git repository**.

It does **not** restore or delete anything.

It only shows the list of saved stashes.

### One-Line Definition

> **`git stash list` displays all the temporary stashes saved in the local repository.**

---

# Why Do We Need `git stash list`?

Suppose you have used

```bash
git stash
```

many times.

You may forget:

* How many stashes exist?
* Which stash is the latest?
* Is there any stash available?

Instead of guessing, run

```bash
git stash list
```

---

# Practical Example

## Step 1

Modify a file

```bash
echo "<h2>Login Feature</h2>" >> index.html
```

---

## Step 2

Save it

```bash
git stash
```

Output

```text
Saved working directory and index state WIP on main
```

---

## Step 3

Again modify

```bash
echo "<p>Signup Page</p>" >> index.html
```

---

## Step 4

Again stash

```bash
git stash
```

Now you have two stashes.

---

## Step 5

Run

```bash
git stash list
```

Example Output

```text
stash@{0}: WIP on main: Second Commit

stash@{1}: WIP on main: First Commit
```

Meaning

```text
stash@{0}

↓

Latest Stash
```

```text
stash@{1}

↓

Older Stash
```

Git always keeps the newest stash at the top.

---

# Internal Working

```text
Working Directory

↓

git stash

↓

Git Stash

stash@{0}

↓

Newest
```

Older stashes move down.

---

# Real-Life Example

Imagine a cupboard.

Every time you put a file inside,

the newest file stays on the top.

`git stash list` simply opens the cupboard and shows all saved files.

---

# Common Mistakes

### Mistake

I thought

```bash
git stash list
```

restores my code.

Wrong.

It only displays the list.

Nothing changes in your project.

---

# Frequently Used Command

```bash
git stash list
```

---

# Topic 2 - `git stash pop`

## What is `git stash pop`?

`git stash pop` restores the latest stash back into the Working Directory and then removes it from the stash list.

### One-Line Definition

> **`git stash pop` restores the latest stashed changes and automatically removes that stash from the list.**

---

# Why Do We Need `git stash pop`?

Imagine this workflow.

```text
Working on Login Feature

↓

git stash

↓

Fix Urgent Bug

↓

Commit Bug Fix

↓

Need Login Feature Again
```

Instead of rewriting the code,

Run

```bash
git stash pop
```

Git restores everything.

---

# Practical Execution

## Step 1

Current file

```html
<h1>Hello</h1>
```

---

## Step 2

Modify

```bash
echo "<p>Login Feature</p>" >> index.html
```

Current file

```html
<h1>Hello</h1>
<p>Login Feature</p>
```

---

## Step 3

Save

```bash
git stash
```

File becomes

```html
<h1>Hello</h1>
```

Your changes are inside the stash.

---

## Step 4

Do another task

Example

```text
Fix Payment Bug
```

Complete it.

Commit it.

Push it.

---

## Step 5

Now continue Login Feature

Run

```bash
git stash pop
```

Example Output

```text
On branch main

Changes not staged for commit:

modified: index.html

Dropped refs/stash@{0}
```

Meaning

Git has restored your changes.

The stash has been deleted because it is no longer needed.

---

## Step 6

Check file

```bash
cat index.html
```

Output

```html
<h1>Hello</h1>
<p>Login Feature</p>
```

Your unfinished work is back.

---

# Internal Working

Before

```text
Git Stash

Login Feature
```

Run

```bash
git stash pop
```

After

```text
Working Directory

Login Feature

↓

Git Stash

Empty
```

The stash moves back to the Working Directory.

---

# Real-Life Example

Imagine a drawer.

You keep your notebook inside.

Drawer = Git Stash

Later

You take the notebook back.

The drawer becomes empty.

That is exactly how `git stash pop` works.

---

# Common Mistakes

### Mistake 1

I thought

```bash
git stash pop
```

only restores the stash.

Wrong.

It restores the stash **and removes it** from the stash list.

---

### Mistake 2

I ran

```bash
git stash pop
```

but there was no stash.

Output

```text
No stash entries found.
```

Reason

There is nothing saved.

---

### Mistake 3

I thought

```bash
git stash pop
```

creates a commit.

Wrong.

It only restores your changes.

You still need

```bash
git add .
git commit -m "..."
```

to save them permanently.

---

# Best Practices

✔ Use `git stash` before switching tasks.

✔ Use `git stash pop` after finishing the other task.

✔ Check `git stash list` if you have multiple stashes.

---

# Frequently Used Commands

Save work

```bash
git stash
```

Show all stashes

```bash
git stash list
```

Restore latest stash

```bash
git stash pop
```

---

# Interview Questions

### What does `git stash list` do?

It displays all saved stashes in the local repository.

---

### What does `git stash pop` do?

It restores the latest stash and removes it from the stash list.

---

### Does `git stash pop` create a commit?

No.

---

### What happens after `git stash pop`?

* Changes return to the Working Directory.
* The restored stash is removed from the stash list.

---

# Summary

## `git stash list`

* Shows all saved stashes.
* Does not restore or delete anything.

## `git stash pop`

* Restores the latest stash.
* Removes it from the stash list.
* Lets you continue your unfinished work.

---

# Complete Workflow

```text
Start Working
      │
      ▼
Modify Files
      │
      ▼
git stash
      │
      ▼
Work on Another Task
      │
      ▼
Commit & Push
      │
      ▼
git stash list (Optional)
      │
      ▼
git stash pop
      │
      ▼
Continue Previous Work
```
