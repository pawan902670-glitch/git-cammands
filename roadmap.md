                    GIT INTERMEDIATE ROADMAP
                           │
                           ▼
                 Branch Management
                           │
       ┌───────────────────┼───────────────────┐
       ▼                   ▼                   ▼
 git branch -m      git branch -d       git branch -D
 (Rename Branch)    (Delete Branch)     (Force Delete)
                           │
                           ▼
                   Merge Workflow
                           │
            ┌──────────────┴──────────────┐
            ▼                             ▼
       git merge                  Merge Conflicts
                                        │
                                        ▼
                                Resolve Conflicts
                                        │
                                        ▼
                                   git commit
                                        │
                                        ▼
                    Temporary Save Work
                                        │
        ┌───────────────┬───────────────┬───────────────┐
        ▼               ▼               ▼
   git stash      git stash list    git stash pop
        │
        ▼
   git stash apply (Optional)
                                        │
                                        ▼
                         Version Management
                                        │
        ┌───────────────┬───────────────┐
        ▼               ▼
    git tag        git tag -a
        │
        ▼
   Push Tags to GitHub
                                        │
                                        ▼
                          Remote Repository
                                        │
 ┌──────────────┬──────────────┬──────────────────┬──────────────────┐
 ▼              ▼              ▼                  ▼
git remote -v git remote add git remote set-url git remote remove
                                        │
                                        ▼
                          Collaborating with GitHub
                                        │
          ┌──────────────┬──────────────┬──────────────┐
          ▼              ▼              ▼
      git fetch      git pull      git push
                                        │
                                        ▼
                     Ready for Advanced Git
                                        │
      ┌──────────────┬──────────────┬──────────────┐
      ▼              ▼              ▼
   git rebase   git cherry-pick   Pull Requests
                                        │
                                        ▼
                          Advanced Git Topics
                                        │
      ┌──────────────┬──────────────┬──────────────┬──────────────┐
      ▼              ▼              ▼              ▼
   git reflog    git bisect    git worktree    git submodule
