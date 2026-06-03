
---

# Git Merge Conflict Notes (Beginner Friendly)

## Scenario

Suppose two developers are working on the same project.

### Developer A (feature1)

Adds a Button.

### Developer B (feature2)

Adds a Dropdown.

Both modify the **same file and same line** (`login.txt`).

Git must decide how to combine their changes.

---

## Step 1: Check Current Branch

```bash
git branch
```

### Purpose

Shows all available branches.

### Example Output

```bash
* main
```

`*` means you are currently on the `main` branch.

---

## Step 2: Create Feature1 Branch

```bash
git checkout -b feature1
```

### Purpose

Create a separate workspace for Button feature.

### What Happens?

Before:

```text
main
```

After:

```text
main
  \
   feature1
```

Now changes in `feature1` will not affect `main`.

---

## Step 3: Modify File in Feature1

`login.txt`

```text
Login Page
<p>Button</p>
```

Save the file.

Git notices the file has changed.

---

## Step 4: Check What Changed

```bash
git status
```

### Purpose

Shows modified files.

Example:

```text
modified: login.txt
```

---

## Step 5: Add Changes to Staging Area

```bash
git add .
```

### Purpose

Prepare files for commit.

### Flow

```text
Working Directory
        ↓
     git add
        ↓
   Staging Area
```

Think of this as putting files into a box before shipping them.

---

## Step 6: Save Changes Permanently

```bash
git commit -m "Add Button"
```

### Purpose

Create a snapshot of your work.

### What Happens?

Git stores your work in project history.

---

## Step 7: Switch Back to Main

```bash
git checkout main
```

### Purpose

Move back to the main branch.

---

## Step 8: Create Feature2 Branch

```bash
git checkout -b feature2
```

### Purpose

Create another feature branch.

### Branch Structure

```text
           feature1
          /
main -----
          \
           feature2
```

---

## Step 9: Modify the Same File in Feature2

`login.txt`

```text
Login Page
<p>Dropdown</p>
```

Save the file.

Notice that the same line was modified differently.

---

## Step 10: Add and Commit

```bash
git add .
git commit -m "Add Dropdown"
```

Now both branches have different versions of the same file.

---

## Step 11: Compare Branches

```bash
git diff feature1 feature2
```

### Purpose

See differences between branches.

Git shows what has changed.

Example:

```diff
- <p>Button</p>
+ <p>Dropdown</p>
```

---

## Step 12: Merge Feature1 into Main

```bash
git checkout main
git merge feature1
```

### Purpose

Bring Button changes into main.

Current state:

```text
main (Button)
```

---

## Step 13: Merge Feature2 into Main

```bash
git merge feature2
```

### Purpose

Bring Dropdown changes into main.

Git detects both branches changed the same line.

Result:

```text
CONFLICT (content): Merge conflict in login.txt
Automatic merge failed
```

---

## What Happens During Conflict?

### Main Branch

```text
Login Page
<p>Button</p>
```

### Feature2 Branch

```text
Login Page
<p>Dropdown</p>
```

Git becomes confused.

Result:

### Merge Conflict

---

## Step 14: Open Conflicted File

Git adds markers:

```text
<<<<<<< HEAD
<p>Button</p>
=======
<p>Dropdown</p>
>>>>>>> feature2
```

### Meaning

`<<<<<<< HEAD`

Current branch code (`main`)

`=======`

Separator

`>>>>>>> feature2`

Incoming branch code

---

## Step 15: Resolve Conflict Manually

Choose the final code.

Example:

```text
Login Page
<p>Button</p>
<p>Dropdown</p>
```

Remove all conflict markers.

Save the file.

---

## Step 16: Tell Git Conflict is Solved

```bash
git add login.txt
```

### Purpose

Marks the file as resolved.

---

## Step 17: Complete Merge

```bash
git commit -m "Resolve merge conflict"
```

### Purpose

Create a new commit containing the merged result.

---

## View Branch History

```bash
git log --oneline --graph --all
```

Example:

```text
*   c93bba3 Resolve merge conflict
|\  
| * 41a206d Add Dropdown
* | e0bd197 Add Button
|/
* cb1eb98 Added login page
```

This shows:

* Feature1 → Add Button
* Feature2 → Add Dropdown
* Main → Resolve merge conflict

---

## Pull Command

```bash
git pull origin main
```

### Purpose

Get latest changes from GitHub.

Internally Git Runs

```bash
git fetch
git merge
```

### Flow

```text
GitHub Repository
         ↓
      git pull
         ↓
 Local Repository Updated
```

---

## Undo Staged Changes

### Remove One File from Staging

```bash
git reset login.txt
```

### Remove All Files from Staging

```bash
git reset
```

### What Happens?

```text
Staging Area
      ↓
   git reset
      ↓
Working Directory
```

Files are not deleted.

Only unstaged.

---

## Complete Real Project Flow

```bash
git clone <repository-url>

git checkout -b feature1

# Make changes

git add .
git commit -m "Add Button"

git checkout main

git checkout -b feature2

# Make changes

git add .
git commit -m "Add Dropdown"

git checkout main

git merge feature1
git merge feature2

# If conflict occurs
# Edit file manually

git add login.txt

git commit -m "Resolve merge conflict"

git push origin main
```

## One-Line Summary

**Git Flow = Create Branch → Make Changes → Add → Commit → Merge → Conflict (Same Line Modified) → Resolve Conflict → Commit → Push**.
