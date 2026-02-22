# Git Cheatsheet

## Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git init                    # New repo
git clone <url>             # Clone existing
```

## Daily Workflow

```bash
git status                  # See changes
git add file.py             # Stage specific file
git add .                   # Stage all changes
git commit -m "message"     # Commit
git push                    # Push to remote
git pull                    # Fetch + merge
```

## Branching

```bash
git branch                  # List branches
git branch feature-x        # Create branch
git checkout feature-x      # Switch to branch
git checkout -b feature-x   # Create + switch
git merge feature-x         # Merge into current
git branch -d feature-x     # Delete branch
```

## Undoing Things

```bash
git checkout -- file.py     # Discard changes in file
git reset HEAD file.py      # Unstage file
git reset --soft HEAD~1     # Undo last commit (keep changes staged)
git reset --hard HEAD~1     # Undo last commit (discard changes)
git stash                   # Temporarily store changes
git stash pop               # Restore stashed changes
```

## Viewing History

```bash
git log --oneline -10       # Last 10 commits, compact
git log --graph --oneline   # Visual branch history
git diff                    # Unstaged changes
git diff --staged           # Staged changes
git blame file.py           # Who changed each line
```

## Remote

```bash
git remote -v               # List remotes
git remote add origin <url> # Add remote
git fetch                   # Download without merge
git push -u origin main     # Push + set upstream
```

## Common Patterns

```bash
# Update feature branch with latest main
git checkout main && git pull && git checkout feature && git merge main

# Interactive rebase (clean up commits)
git rebase -i HEAD~3

# Cherry-pick a commit
git cherry-pick <commit-hash>

# Tag a release
git tag v1.0.0 && git push origin v1.0.0
```
