# Git Notes – Branch & Remote Commands

---

# Topic 1: `git branch -m`

## What is `git branch -m`?

The `git branch -m` command is used to **rename a Git branch**.

The `-m` stands for **move (rename)**.

This command is useful when:

* You gave a branch the wrong name.
* You want a more meaningful branch name.
* You want to rename `master` to `main`.

---

## Syntax

```bash
git branch -m <new-branch-name>
```

Renames the **current branch**.

Or

```bash
git branch -m <old-branch-name> <new-branch-name>
```

Renames another branch without switching to it.

---

## Example 1: Rename Current Branch

Current branch:

```bash
feature
```

Rename it:

```bash
git branch -m login-feature
```

Now:

```bash
login-feature
```

---

## Example 2: Rename Another Branch

```bash
git branch -m feature navbar-feature
```

Result:

Before

```
feature
```

After

```
navbar-feature
```

---

## Verify

```bash
git branch
```

Output

```text
* login-feature
  main
```

---

## Important Notes

* Branch history remains the same.
* No commits are lost.
* Only the branch name changes.
* If the branch exists on GitHub, you'll also need to update the remote branch.

---

## Summary

| Command                           | Purpose               |
| --------------------------------- | --------------------- |
| `git branch -m new-name`          | Rename current branch |
| `git branch -m old-name new-name` | Rename another branch |

---

# Topic 2: `git branch -d`

## What is `git branch -d`?

The `git branch -d` command is used to **delete a local Git branch**.

The `-d` stands for **delete**.

Use this after a feature branch has been merged and is no longer needed.

---

## Syntax

```bash
git branch -d <branch-name>
```

---

## Example

Current branches

```text
main
login-feature
```

Delete the feature branch

```bash
git branch -d login-feature
```

Output

```text
Deleted branch login-feature.
```

---

## Verify

```bash
git branch
```

Output

```text
* main
```

---

## Why Delete Branches?

Deleting old branches helps:

* Keep the repository clean.
* Avoid confusion.
* Remove branches that have already been merged.

---

## Important Notes

* You **cannot delete the branch you're currently on**.
* Switch to another branch first.

Example

```bash
git switch main
git branch -d login-feature
```

* If the branch has **unmerged changes**, Git will prevent deletion.

Example

```text
error: The branch 'login-feature' is not fully merged.
```

To force delete (use carefully):

```bash
git branch -D login-feature
```

> `-D` forcefully deletes the branch even if it contains unmerged commits.

---

## Summary

| Command                     | Purpose                       |
| --------------------------- | ----------------------------- |
| `git branch -d branch-name` | Safely delete a merged branch |
| `git branch -D branch-name` | Force delete a branch         |

---

# Topic 3: `git remote -v`

## What is `git remote -v`?

The `git remote -v` command shows the **remote repositories connected to your local Git repository**.

The `-v` stands for **verbose**, meaning it displays additional details like the repository URLs.

---

## Why Use It?

It helps you check:

* Which GitHub repository is connected.
* The remote name (usually `origin`).
* The URL used for fetching and pushing.

---

## Syntax

```bash
git remote -v
```

---

## Example

```bash
git remote -v
```

Output

```text
origin  https://github.com/user/my-project.git (fetch)
origin  https://github.com/user/my-project.git (push)
```

---

## Understanding the Output

| Part     | Meaning                      |
| -------- | ---------------------------- |
| `origin` | Default remote name          |
| `fetch`  | Download changes from GitHub |
| `push`   | Upload changes to GitHub     |

---

## Summary

| Command         | Purpose                                |
| --------------- | -------------------------------------- |
| `git remote -v` | Show all connected remote repositories |

---

# Topic 4: `git remote set-url`

## What is `git remote set-url`?

The `git remote set-url` command is used to **change the URL of an existing remote repository**.

This is useful when:

* The GitHub repository has moved.
* You switched from HTTPS to SSH.
* You want to connect your local project to a different remote repository.

---

## Syntax

```bash
git remote set-url <remote-name> <new-url>
```

Usually:

```bash
git remote set-url origin <new-url>
```

---

## Example

Current remote

```text
https://github.com/user/old-project.git
```

Change it

```bash
git remote set-url origin https://github.com/user/new-project.git
```

---

## Verify

```bash
git remote -v
```

Output

```text
origin  https://github.com/user/new-project.git (fetch)
origin  https://github.com/user/new-project.git (push)
```

---

## Common Use Cases

### Change HTTPS to SSH

Before

```text
https://github.com/user/project.git
```

After

```text
git@github.com:user/project.git
```

Command

```bash
git remote set-url origin git@github.com:user/project.git
```

---

### Connect to a New GitHub Repository

```bash
git remote set-url origin https://github.com/user/new-repository.git
```

---

## Verify the Change

Always check:

```bash
git remote -v
```

---

## Summary

| Command                               | Purpose                                          |
| ------------------------------------- | ------------------------------------------------ |
| `git remote set-url origin <new-url>` | Change the URL of the existing remote repository |
| `git remote -v`                       | Verify the updated remote URL                    |

---

# Quick Revision

| Command                               | Purpose                                              |
| ------------------------------------- | ---------------------------------------------------- |
| `git branch -m new-name`              | Rename the current branch                            |
| `git branch -m old-name new-name`     | Rename another branch                                |
| `git branch -d branch-name`           | Delete a merged local branch                         |
| `git branch -D branch-name`           | Force delete a local branch                          |
| `git remote -v`                       | Display connected remote repositories and their URLs |
| `git remote set-url origin <new-url>` | Change the URL of an existing remote repository      |
