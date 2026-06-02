
Git Merge Conflict Notes (Beginner Friendly)

Scenario

Suppose two developers are working on the same project.

Developer A

Creates a button.

Developer B

Creates a dropdown.

Both modify the same file (index.html).

Git must decide how to combine their changes.


---

Step 1: Check Current Branch

git branch

Purpose

Shows all available branches.

Example Output

* main
  feature1

* means you are currently on the main branch.


---

Step 2: Create a New Branch

git checkout -b feature1

Purpose

Create a separate workspace for a new feature.

What Happens?

Before:

main

After:

main
  └── feature1

Now changes in feature1 will not affect main.


---

Step 3: Modify the File

Example:

<p>Add Button</p>

Save the file.

Git notices the file has changed.


---

Step 4: Check What Changed

git status

Purpose

Shows modified files.

Example:

modified: index.html


---

Step 5: Add Changes to Staging Area

git add .

Purpose

Prepare files for commit.

Flow

Working Directory
        ↓
     git add
        ↓
   Staging Area

Think of this as putting files into a box before shipping them.


---

Step 6: Save Changes Permanently

git commit -m "Add Button"

Purpose

Create a snapshot of your work.

What Happens?

Git stores your work in project history.


---

Step 7: Switch to Another Branch

git checkout main

Purpose

Move back to the main branch.


---

Step 8: Someone Else Makes Changes

Suppose another developer changes the same file:

<p>Add Dropdown</p>

Then saves it.


---

Step 9: Add and Commit

git add .
git commit -m "Add Dropdown"

Now both branches have different versions of the same file.


---

Step 10: Compare Changes

git diff main

Purpose

See differences between branches.

Git shows what has changed.


---

Step 11: Merge Branches

git checkout main
git merge feature1

Purpose

Bring feature1 changes into main.


---

What Happens During Merge?

Case 1: Different Lines Modified

Main:

<h1>Welcome</h1>

Feature1:

<p>Add Button</p>

Git can merge automatically.

Result:

<h1>Welcome</h1>
<p>Add Button</p>

No conflict.


---

Case 2: Same Line Modified

Main:

<p>Add Button</p>

Feature1:

<p>Add Dropdown</p>

Git becomes confused.

Result:

Merge Conflict


---

Step 12: Open Conflicted File

Git adds markers:

<<<<<<< HEAD
<p>Add Button</p>
=======
<p>Add Dropdown</p>
>>>>>>> feature1

Meaning

<<<<<<< HEAD
Current branch code

=======
Separator

>>>>>>> feature1
Incoming branch code


---

Step 13: Resolve Conflict Manually

Choose the final code.

Example:

<p>Add Button</p>
<p>Add Dropdown</p>

Remove all conflict markers.

Save the file.


---

Step 14: Tell Git Conflict is Solved

git add index.html

Purpose

Marks the file as resolved.


---

Step 15: Complete Merge

git commit -m "Resolve Merge Conflict"

Purpose

Create a new commit containing the merged result.


---

Pull Command

git pull origin main

Purpose

Get latest changes from GitHub.

Internally Git Runs

git fetch
git merge

Flow

GitHub Repository
         ↓
      git pull
         ↓
 Local Repository Updated


---

Undo Staged Changes

Remove One File from Staging

git reset index.html

Remove All Files from Staging

git reset

What Happens?

Staging Area
      ↓
   git reset
      ↓
Working Directory

Files are not deleted.

Only unstaged.


---

Complete Real Project Flow

git clone <repository-url>

git branch

git checkout -b feature1

# Make changes

git status

git add .

git commit -m "Add Button"

git checkout main

git pull origin main

git merge feature1

# If conflict occurs
# Edit file manually

git add .

git commit -m "Resolve Merge Conflict"

git push origin main

One-Line Summary

Git Flow = Create Branch → Make Changes → Add → Commit → Merge → Resolve Conflict (if any) → Commit → Push.

