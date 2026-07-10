
# Git Notes – Chapter 6: `git fetch`

## Topic: `git fetch`

---

# What is `git fetch`?

`git fetch` is used to **download the latest changes from GitHub** without changing your current project.

### One-Line Definition

> **`git fetch` downloads the latest changes from the remote repository but does not merge them into your current branch.**

---

# Why do we use `git fetch`?

Imagine two developers are working on the same project.

* 👨 You
* 👨‍💻 Your Friend

Your friend pushes new code to GitHub.

Your project doesn't know about those changes.

To check for new updates, you run:

```bash
git fetch
```

Git downloads the latest commits from GitHub.

But your project files stay exactly the same.

---

# Easy Real-Life Example

Suppose you are writing notes.

Your friend updates the notes on Google Drive.

You click **Download**.

Now the latest file is downloaded to your laptop.

But you haven't opened or replaced your old file yet.

That is exactly how `git fetch` works.

---

# Formula

```text
git fetch

↓

Download latest changes

↓

Do NOT change my project
```

---

# Difference Between `git fetch` and `git pull`

| Command     | Download | Merge |
| ----------- | -------- | ----- |
| `git fetch` | ✅ Yes    | ❌ No  |
| `git pull`  | ✅ Yes    | ✅ Yes |

### Memory Trick

```text
git fetch = Download only

git pull = Download + Merge
```

---

# Practical (Using Your Repository)

## Step 1 - Check Status

```bash
git status
```

Output

```text
On branch main

Your branch is up to date with 'origin/main'.
```

### Meaning

Everything is updated.

No new changes are available.

---

## Step 2 - Someone Pushes New Code

Example

Your friend adds:

```text
Adding new film
```

and pushes it to GitHub.

Now GitHub has a new commit.

Your local project **still doesn't know**.

---

## Step 3 - Download Latest Changes

Run:

```bash
git fetch
```

Output

```text
From https://github.com/username/project

2a3ea49..157cf89

main -> origin/main
```

### What Git Did

* Connected to GitHub ✅
* Checked for new commits ✅
* Downloaded the latest commit ✅
* Updated `origin/main` ✅
* **Did not change your project files** ❌

---

## Step 4 - Check Status Again

Run:

```bash
git status
```

Output

```text
Your branch is behind 'origin/main' by 1 commit.
```

### Meaning

Git is saying:

> "I have downloaded the new commit, but your local `main` branch has not received it yet."

Current situation:

```text
GitHub (origin/main)

Commit 1
Commit 2
Commit 3
Commit 4

↓

Local (main)

Commit 1
Commit 2
Commit 3
```

---

## Step 5 - See the Missing Commit

Run:

```bash
git log --oneline main..origin/main
```

Output

```text
157cf89 Adding new film
```

### Meaning

This commit exists on GitHub but not in your local branch.

---

## Step 6 - Update Your Local Branch

Run:

```bash
git merge origin/main
```

OR

```bash
git pull
```

Now your local project becomes updated.

---

# Internal Working

Before `git fetch`

```text
GitHub

A
B
C
D

↓

Local

A
B
C
```

Run:

```bash
git fetch
```

After:

```text
GitHub

A
B
C
D

↓

origin/main

A
B
C
D

↓

main

A
B
C
```

Notice:

Only `origin/main` is updated.

`main` is still old.

---

# Real Company Workflow

```text
Developer Pushes Code
        │
        ▼
GitHub Updated
        │
        ▼
You run

git fetch

        │
        ▼
Download latest changes
        │
        ▼
Review changes
        │
        ▼
git merge origin/main
        │
        ▼
Continue Coding
```

---

# Common Mistakes

## Mistake 1

"I thought `git fetch` updates my project."

❌ Wrong.

It only downloads changes.

---

## Mistake 2

"I thought `git fetch` and `git pull` are the same."

❌ Wrong.

`git pull` = `git fetch` + `git merge`

---

## Mistake 3

"I ran `git fetch`, but my files didn't change."

✅ Correct.

That is exactly how `git fetch` works.

---

# Best Practices

✔ Use `git fetch` before starting work.

✔ Check what has changed.

✔ Merge only when you are ready.

---

# Frequently Used Commands

Check status

```bash
git status
```

Download latest changes

```bash
git fetch
```

Show missing commits

```bash
git log --oneline main..origin/main
```

Merge downloaded changes

```bash
git merge origin/main
```

OR

```bash
git pull
```

---

# Interview Questions

### What is `git fetch`?

It downloads the latest changes from the remote repository without merging them into the current branch.

---

### Does `git fetch` change my project?

**No.**

---

### What is the difference between `git fetch` and `git pull`?

* `git fetch` downloads only.
* `git pull` downloads and merges.

---

# Summary

```text
Friend Pushes Code
        │
        ▼
GitHub Updated
        │
        ▼
git fetch
        │
        ▼
Download New Commit
        │
        ▼
Local Project Still Same
        │
        ▼
git merge origin/main
        │
        ▼
Project Updated
```

---

## ⭐ Easy Memory Trick

```text
git fetch

↓

📥 Download

↓

Wait

↓

git merge

↓

📂 Use Changes
```

### One-line Revision

> **`git fetch` downloads the latest changes from GitHub but does not apply them to your project until you merge or pull them.**

---

