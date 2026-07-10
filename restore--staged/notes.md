# Git Notes - `git restore --staged` (Complete Guide)

---

# Topic: `git restore --staged`

## What is `git restore --staged`?

`git restore --staged` is used to **remove a file from the Staging Area** while **keeping all your changes safe in the Working Directory**.

In simple words,

> **"Cancel `git add`, but don't delete my code."**

---

# Why do we need it?

Sometimes we accidentally stage a file.

Example

```bash
git add .
```

This stages every changed file.

Later we realize:

> "I don't want to commit one of these files yet."

Instead of deleting our work, we simply remove that file from the staging area.

---

# Internal Working

Git has three important areas.

```text
Working Directory
      │
      │ git add
      ▼
Staging Area
      │
      │ git commit
      ▼
Local Repository
```

---

# What happens after `git add`?

Suppose

index.html

```html
<h1>Hello</h1>
<h2>Welcome</h2>
```

Run

```bash
git add index.html
```

Now

```text
Working Directory

Hello
Welcome

↓

git add

↓

Staging Area

Hello
Welcome
```

The file is now **ready to be committed**.

---

# What happens after `git restore --staged`?

Run

```bash
git restore --staged index.html
```

Git removes the file from the staging area.

Result

```text
Working Directory

Hello
Welcome

↓

Not Staged

↓

Staging Area

Empty
```

Notice

Your file is still

```text
Hello
Welcome
```

Nothing is deleted.

Only `git add` is cancelled.

---

# Practical Example

## Step 1

Modify a file

```html
<h1>Hello</h1>
<h2>Welcome</h2>
```

---

## Step 2

Stage it

```bash
git add index.html
```

Check

```bash
git status
```

Output

```text
Changes to be committed:

modified: index.html
```

Meaning

The file is ready for commit.

---

## Step 3

Oops!

You don't want to commit this file.

Run

```bash
git restore --staged index.html
```

---

## Step 4

Check again

```bash
git status
```

Output

```text
Changes not staged for commit:

modified: index.html
```

Notice

The file is no longer staged.

But your changes are still there.

---

# Real-Life Example

Imagine you are packing a suitcase.

You put these items inside:

* Laptop
* Charger
* Mobile

Packing the suitcase is like

```bash
git add
```

Before leaving, you decide:

> "I don't want to take the Mobile."

You remove only the Mobile from the suitcase.

The Mobile is still in your room.

Exactly the same.

Room = Working Directory

Suitcase = Staging Area

Trip = Commit

---

# Profit (Why is it useful?)

Suppose your project has

```text
index.html
style.css
login.js
README.md
```

You accidentally run

```bash
git add .
```

Everything becomes staged.

But `login.js` is only half finished.

Instead of deleting your work,

Run

```bash
git restore --staged login.js
```

Now

✅ index.html stays staged

✅ style.css stays staged

✅ README.md stays staged

❌ login.js is removed from staging

You can safely commit the completed files and finish `login.js` later.

---

# Professional Use

A manager asks:

> "Commit only the bug fix."

You accidentally stage

* Bug Fix ✅
* New Feature (Incomplete) ❌

Use

```bash
git restore --staged newFeature.js
```

Now only the bug fix is committed.

This keeps Git history clean and professional.

---

# Difference Between `git restore` and `git restore --staged`

| Command                           | Removes File Changes | Removes from Staging |
| --------------------------------- | -------------------- | -------------------- |
| `git restore index.html`          | ✅ Yes                | ❌ No                 |
| `git restore --staged index.html` | ❌ No                 | ✅ Yes                |

---

# Common Mistake

I thought

```bash
git restore --staged index.html
```

would delete my code.

Wrong.

Correct

It only removes the file from the staging area.

The file contents remain unchanged.

---

# Another Common Mistake

I thought

```bash
git restore
```

and

```bash
git restore --staged
```

do the same thing.

Wrong.

`git restore`

↓

Deletes uncommitted changes.

`git restore --staged`

↓

Cancels `git add`.

---

# Best Practices

✔ Use `git restore --staged` when you accidentally stage a file.

✔ Check `git status` before committing.

✔ Make small, meaningful commits instead of committing everything.

✔ Stage only the files related to one task.

---

# Interview Questions

### What does `git restore --staged` do?

It removes a file from the staging area while keeping all changes in the working directory.

---

### Does `git restore --staged` delete my code?

No.

It only unstages the file.

---

### When should I use it?

When a file was staged by mistake and should not be included in the next commit.

---

# One-Line Definition

> **`git restore --staged` unstages a file by removing it from the Staging Area while keeping all file changes safely in the Working Directory.**

