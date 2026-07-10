# Git Notes - `git restore` (Complete Guide)

---

# Topic: `git restore`

## What is `git restore`?

`git restore` is used to **discard (remove) uncommitted changes** from the **Working Directory** and restore the file to its **last committed version**.

In simple words,

> **"I don't want my recent changes. Bring my file back to the last commit."**

---

# When do we use it?

Suppose you accidentally modify a file and later realize:

* I don't need these changes.
* I want the old version back.

Instead of deleting the changes manually, use:

```bash
git restore <file-name>
```

Example:

```bash
git restore index.html
```

---

# Internal Working of Git

Git has three important areas.

```text
          Working Directory
                 │
        (Files you are editing)
                 │
                 ▼
          Staging Area
        (git add stores files here)
                 │
                 ▼
        Local Repository
      (git commit saves here)
```

---

# What is Working Directory?

The place where you write code.

Example

index.html

```html
<h1>Hello</h1>
```

Now you edit the file

```html
<h1>Hello</h1>
<h2>Welcome</h2>
```

The file has changed.

These changes are **only inside the Working Directory**.

Nothing has been committed yet.

---

# Practical Example

## Step 1

Create a project

```bash
mkdir restore-demo
cd restore-demo
git init
```

---

## Step 2

Create a file

```bash
echo Hello > index.html
```

Check

```bash
cat index.html
```

Output

```text
Hello
```

---

## Step 3

Save the file into Git

```bash
git add .
git commit -m "First Commit"
```

Git creates a snapshot.

Current Git history

```text
Commit

Hello
```

---

## Step 4

Modify the file

```bash
echo Welcome >> index.html
```

Now check

```bash
cat index.html
```

Output

```text
Hello
Welcome
```

---

## Step 5

Check Git status

```bash
git status
```

Output

```text
modified: index.html
```

Git is saying

> "This file has changed after the last commit."

---

## Step 6

Remove those changes

```bash
git restore index.html
```

---

## Step 7

Check the file

```bash
cat index.html
```

Output

```text
Hello
```

The line

```text
Welcome
```

has been removed.

---

# What happened internally?

Before restore

```text
Last Commit

Hello
```

Current File

```text
Hello
Welcome
```

Command

```bash
git restore index.html
```

Git compares the current file with the last commit.

Git throws away the uncommitted changes.

Result

```text
Hello
```

---

# Important Point

`git restore` removes only **uncommitted changes**.

It does NOT remove commits.

---

# Real-Life Example

Suppose you saved a Word document yesterday.

Today you make many unwanted edits.

Instead of pressing Undo multiple times, you restore yesterday's saved version.

That is exactly what `git restore` does.

---

# Common Mistake

I thought

> git restore removes commits.

Wrong.

Correct

It removes only **uncommitted changes**.

---

# Another Common Mistake

I accidentally ran

```bash
git restore index.html
```

without checking.

Result

My recent work disappeared.

Reason

`git restore` permanently discards uncommitted changes.

Always check

```bash
git status
```

before using it.

---

# When should I use git restore?

Use it when

✔ You accidentally edited a file.

✔ You don't want those edits.

✔ The changes have NOT been committed.

---

# When should I NOT use git restore?

Do NOT use it when

❌ You still need your changes.

❌ You already committed those changes.

---

# Command

```bash
git restore index.html
```

or

```bash
git restore app.js
```

---

# Summary

Purpose

Restore a file to its last committed version.

Works On

Working Directory

Removes

Uncommitted changes

Does it remove commits?

No

Does it remove staged files?

No

---

# One-Line Definition

> **`git restore` discards uncommitted changes from the Working Directory and restores the file to the state of the last commit.**

---

# Next Topic

The next command is:

```bash
git restore --staged
```

Difference:

* `git restore` → Removes changes from the **Working Directory**.
* `git restore --staged` → Removes a file from the **Staging Area**, but **keeps your changes**.

This difference is one of the most important Git concepts.
