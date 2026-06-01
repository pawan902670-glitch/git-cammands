
Git Branching Cheat Sheet (Command-Oriented)

1. Check Repository Status

Purpose: See what changed.

git status

---

2. Check Current Branch

Purpose: Know where you are.

git branch

Output:

* main
  feature-login

"*" = current branch

---

3. Create New Branch

Purpose: Start new feature.

git branch feature-login

Check:

git branch

---

4. Switch Branch

Purpose: Move to another branch.

git switch feature-login

Old command:

git checkout feature-login

---

5. Create + Switch Together

Most used command.

git switch -c feature-login

or

git checkout -b feature-login

---

6. See Files

Linux/Git Bash:

ls

Windows CMD:

dir

---

7. Create File

echo "Login Page" > login.txt

Check:

git status

---

8. Stage Changes

Single file:

git add login.txt

All files:

git add .

---

9. Commit Changes

git commit -m "Added login page"

Meaning:

Create checkpoint.

---

10. View Commit History

Short history:

git log --oneline

Full history:

git log

Graph view:

git log --oneline --graph --all

---

11. Show Current Commit

git rev-parse HEAD

---

12. Compare Branches

git diff main feature-login

No output = no difference.

---

13. See What a Commit Changed

git show <commit-id>

Example:

git show cb1eb98

---

14. Merge Branch

Move to main:

git switch main

Merge:

git merge feature-login

Possible output:

Fast-forward

Meaning:

Merge successful.

---

15. Delete Branch

Safe delete:

git branch -d feature-login

Force delete:

git branch -D feature-login

---

16. Rename Branch

Current branch:

git branch -m new-name

Another branch:

git branch -m old-name new-name

---

17. View Local Branches

git branch

---

18. View Remote Branches

git branch -r

---

19. View All Branches

git branch -a

---

20. Push Branch to GitHub

Main:

git push origin main

Feature branch:

git push origin feature-login

---

21. Download Latest Information

git fetch

Fetch does NOT merge.

---

22. Pull Latest Changes

git pull

Equivalent to:

git fetch
git merge

---

23. Clone Repository

git clone <repository-url>

Example:

git clone https://github.com/user/project.git

---

24. Check Remote Repository

git remote -v

Output:

origin https://github.com/user/project.git

---

25. See Tracked Files

git ls-files

---

Real Daily Workflow

git pull

git switch -c feature-login

git status

git add .

git commit -m "Added login page"

git push origin feature-login

git switch main

git pull

git merge feature-login

git branch -d feature-login

Memory Formula

Repository
↓
Branch
↓
File Change
↓
git add
↓
git commit
↓
git merge
↓
git push

Commands in order:

git status
git branch
git switch -c branch-name
git add .
git commit -m "message"
git merge branch-name
git push origin branch-nameThis is the 80/20 Git command set—the small set of commands that covers most day-to-day development work with branches.