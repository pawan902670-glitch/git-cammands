

1. Fork


2. Branch


3. Pull Request


4. Pull Request vs Pull Command


5. Fetch


6. Pushing


7. Inspecting History


8. Viewing Differences


9. Tags



Here are complete notes with a one-line command explanation for each.

1. Fork

Definition

A Fork is a copy of another user's GitHub repository into your own GitHub account.

Why use it?

Contribute to open-source projects.

Make changes without affecting the original repository.

Create Pull Requests to suggest changes.


Workflow

Original Repository
       ↓
Fork Repository
       ↓
Clone Fork
       ↓
Make Changes
       ↓
Push Changes
       ↓
Create Pull Request


---

2. Branch

Definition

A Branch is an independent line of development within a repository.

Commands

git branch feature-branch

Does: Creates a new branch named feature-branch.

git branch

Does: Lists all local branches.

git checkout feature-branch

Does: Switches to the specified branch.

git checkout -b feature-branch

Does: Creates and switches to a new branch.


---

3. Pull Request (PR)

Definition

A Pull Request is a request to merge code changes from one branch into another.

Why use it?

Code review.

Team collaboration.

Discuss changes before merging.

Maintain code quality.


Workflow

Create Branch
      ↓
Make Changes
      ↓
Commit
      ↓
Push
      ↓
Create Pull Request
      ↓
Review
      ↓
Merge


---

4. Pull Request vs Pull Command

Pull Request	Pull Command

GitHub feature	Git command
Used for code review	Used for updating code
Requires approval	No approval needed
Merges changes after review	Downloads and merges changes immediately


Pull Command

git pull origin main

Does: Downloads and merges latest changes from the remote repository.


---

5. Fetch

Definition

Fetch downloads remote changes without merging them.

Command

git fetch

Does: Retrieves latest repository updates from remote.

Example

git fetch origin

Does: Downloads updates from the remote named origin.

Benefit

You can inspect changes before merging them.


---

6. Pushing

Definition

Push sends your local commits to a remote repository.

Command

git push origin main

Does: Uploads local commits from main branch to GitHub.

Example

git push origin feature-branch

Does: Uploads commits from feature-branch.


---

7. Inspecting History

Definition

Used to view commit history and track project changes.

Commands

git log

Does: Shows complete commit history.

git log --oneline

Does: Shows commit history in a compact format.

git log --graph --oneline

Does: Displays commit history as a branch graph.

Uses

Track changes.

Find commit IDs.

Debug issues.



---

8. Viewing Differences

Definition

Shows differences between files, commits, or branches.

Commands

git diff

Does: Shows uncommitted changes.

git diff commit1 commit2

Does: Compares two commits.

git diff main feature-branch

Does: Compares two branches.

Uses

Review code changes.

Verify modifications before committing.



---

9. Tags

Definition

A Tag marks a specific commit, usually a release version.

Commands

git tag v1.0

Does: Creates a tag named v1.0.

git tag

Does: Lists all tags.

git push origin v1.0

Does: Uploads a specific tag to GitHub.

git push --tags

Does: Uploads all local tags to GitHub.

Example

v1.0 → First Release
v2.0 → Major Update
v3.0 → Stable Release


---

Complete GitHub Workflow

Fork Repository
       ↓
git clone
(Copy repository to local machine)

       ↓
git checkout -b feature-branch
(Create and switch to branch)

       ↓
Modify Files

       ↓
git status
(Check changes)

       ↓
git add .
(Stage changes)

       ↓
git commit -m "message"
(Save changes)

       ↓
git push origin feature-branch
(Upload changes)

       ↓
Create Pull Request
(Request merge)

       ↓
Review & Merge

       ↓
git fetch
(Get latest changes)

       ↓
git pull
(Update local repository)

       ↓
git log
(View history)

       ↓
git diff
(View differences)

       ↓
git tag v1.0
(Mark release version)

These are the complete topics visible in your image, organized as clean study notes.