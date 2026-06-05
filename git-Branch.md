That's the right approach. Instead of only memorizing commands, understand:

1. **Why we use the command**
2. **What problem it solves**
3. **What happens internally in Git**
4. **When to use it in a real project**

---

# Git Branching - Deep Understanding Notes

## Imagine a Real Project

Suppose your company has an E-Commerce website.

Current code is running successfully on production.

```text
main
```

contains:

* Login
* Signup
* Products
* Cart

Now manager says:

> Add Payment Feature.

Should you directly start coding in main?

❌ No

Because if your payment code has bugs, the production code can break.

So we create a separate branch.

---

# What is a Branch?

A branch is simply a separate workspace.

Think of it like:

```text
Main Notebook
|
|-- Page for Login Feature
|
|-- Page for Payment Feature
|
|-- Page for Bug Fix
```

Everyone can work independently.

---

# Command 1: git branch

```bash
git branch
```

## Why use it?

To see all available branches.

## What does it do?

Git displays all branch names.

Example:

```bash
main
feature-login
feature-payment
```

Current branch:

```bash
* main
```

The `*` means:

```text
You are currently standing on main branch.
```

---

# Command 2: git branch feature-login

```bash
git branch feature-login
```

## Why use it?

To create a new branch.

## What does Git do internally?

Git creates another pointer.

Before:

```text
main
 |
commit1
 |
commit2
```

After:

```text
main
 |
feature-login
 |
commit2
```

Both point to the same code initially.

## Important

You are still on:

```bash
main
```

Creating a branch does not move you.

---

# Command 3: git checkout feature-login

```bash
git checkout feature-login
```

## Why use it?

To move into another branch.

## What happens internally?

Git changes HEAD.

Before:

```text
HEAD -> main
```

After:

```text
HEAD -> feature-login
```

Now every change goes into:

```text
feature-login
```

not main.

---

# What is HEAD?

HEAD means:

```text
Current active branch
```

Example:

```text
HEAD -> feature-login
```

Git knows where new commits should go.

---

# Command 4: git checkout -b feature-login

```bash
git checkout -b feature-login
```

## Why use it?

Most commonly used command.

Creates branch and moves into it immediately.

Instead of:

```bash
git branch feature-login

git checkout feature-login
```

Use:

```bash
git checkout -b feature-login
```

One command does both jobs.

---

# Modern Alternative

```bash
git switch -c feature-login
```

Same meaning.

### Git internally

```text
Create Branch
+
Move HEAD
```

---

# Coding Phase

After switching:

```bash
git checkout -b feature-login
```

You start writing code.

Example:

```jsx
function Login() {
 return <h1>Login Page</h1>
}
```

Now your files changed.

---

# Command 5: git status

```bash
git status
```

## Why use it?

To check what's happening in repository.

Git tells:

```text
Modified files
Untracked files
Current branch
Files ready for commit
```

Example:

```bash
modified: App.js
```

Meaning:

```text
App.js changed
but Git has not saved it yet
```

---

# Command 6: git add .

```bash
git add .
```

## Why use it?

To tell Git:

```text
Prepare these files for next commit.
```

Think of it like:

### School Example

Writing answer:

```text
Notebook
```

Submitting answer:

```text
git add .
```

Git moves files to:

```text
Staging Area
```

---

# Git Areas

```text
Working Directory
       |
       v
git add .
       |
       v
Staging Area
       |
       v
git commit
```

---

# Command 7: git commit

```bash
git commit -m "Added login page"
```

## Why use it?

To save a permanent snapshot.

Think:

```text
Video Game Save Point
```

Git remembers everything at that moment.

---

## What happens internally?

Git creates a commit object.

```text
Commit A
```

contains:

* File changes
* Author
* Date
* Commit message

Example:

```text
Commit A
|
Added login page
```

---

# Command 8: git diff

```bash
git diff
```

## Why use it?

To compare changes.

Git shows:

```text
Old code
New code
```

Example:

Before:

```js
const name = "John";
```

After:

```js
const name = "Pawan";
```

Git displays:

```diff
- John
+ Pawan
```

---

# Command 9: git push

```bash
git push origin feature-login
```

## Why use it?

To send local branch to GitHub.

Before:

```text
Your Laptop
```

After:

```text
GitHub Server
```

GitHub receives all commits.

---

# What is origin?

```text
origin = GitHub repository URL
```

Example:

```bash
origin
```

may point to:

```text
github.com/company/project.git
```

---

# Pull Request (PR)

After push:

```bash
git push origin feature-login
```

GitHub now sees your branch.

You create:

```text
Pull Request
```

---

## Why PR?

Without PR:

```text
Anyone can merge anything
```

Dangerous.

With PR:

```text
Review
Approval
Testing
Merge
```

Safe.

---

# Command 10: git merge

```bash
git merge feature-login
```

## Why use it?

To bring feature code into main.

Before:

```text
main
|
feature-login
```

After:

```text
main
|
contains login feature
```

---

# Complete Professional Workflow

### Step 1

Go to latest main

```bash
git checkout main
git pull origin main
```

Why?

```text
Get latest code from team.
```

---

### Step 2

Create feature branch

```bash
git checkout -b feature-login
```

Why?

```text
Work safely without affecting main.
```

---

### Step 3

Write code

```text
Login page
Validation
API calls
```

---

### Step 4

Check changes

```bash
git status
```

Why?

```text
See modified files.
```

---

### Step 5

Stage changes

```bash
git add .
```

Why?

```text
Prepare files for commit.
```

---

### Step 6

Save snapshot

```bash
git commit -m "Added login functionality"
```

Why?

```text
Create project checkpoint.
```

---

### Step 7

Push branch

```bash
git push origin feature-login
```

Why?

```text
Upload work to GitHub.
```

---

### Step 8

Create Pull Request

Why?

```text
Team reviews code.
```

---

### Step 9

Merge

Why?

```text
Feature becomes part of main project.
```

---

# One-Line Memory Trick

```text
git branch      -> See/Create branches

git checkout    -> Move branch

git checkout -b -> Create + Move

git status      -> Check changes

git add .       -> Stage changes

git commit      -> Save snapshot

git diff        -> Compare changes

git push        -> Send to GitHub

Pull Request    -> Ask team to review

git merge       -> Combine branches
```

