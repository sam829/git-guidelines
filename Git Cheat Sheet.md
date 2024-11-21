# Git Advanced Operations Cheat Sheet

## Table of Contents
1. [Basic Configuration](#basic-configuration)
2. [Branching](#branching)
3. [Merging Strategies](#merging-strategies)
4. [Rebasing](#rebasing)
5. [Cherry-Picking](#cherry-picking)
6. [Stashing](#stashing)
7. [Resetting and Reverting](#resetting-and-reverting)
8. [Advanced Operations](#advanced-operations)

## Basic Configuration

### Set Up Global Configuration
```bash
# Set user name and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default editor
git config --global core.editor "vim"

# List all configurations
git config --list
```

## Branching

### Basic Branch Operations
```bash
# Create a new branch
git branch feature/new-feature

# Switch to a branch
git checkout feature/new-feature

# Create and switch to a new branch
git checkout -b feature/another-feature

# List branches
git branch -a  # List all branches (local and remote)
git branch -r  # List remote branches
git branch -v  # Show last commit on each branch

# Delete a branch
git branch -d feature/old-feature  # Safe delete (only if merged)
git branch -D feature/old-feature  # Force delete
```

## Merging Strategies

### Merge Types

1. **Merge (Recursive Strategy)**
```bash
# Basic merge
git checkout main
git merge feature/new-feature

# Merge with no-ff (always create merge commit)
git merge --no-ff feature/new-feature
```

2. **Squash Merge**
```bash
# Combine all commits into a single commit
git checkout main
git merge --squash feature/new-feature
git commit -m "Implement new feature"
```

3. **Rebase Merge**
```bash
# Rebase feature branch onto main
git checkout feature/new-feature
git rebase main

# Then merge with fast-forward
git checkout main
git merge feature/new-feature
```

## Rebasing

### Rebase Basics
```bash
# Rebase current branch onto another branch
git rebase main

# Interactive rebase (edit, squash, reorder commits)
git rebase -i HEAD~3  # Last 3 commits
```

#### Interactive Rebase Commands
```
pick: Keep the commit as-is
reword: Change commit message
edit: Stop and edit commit
squash: Combine with previous commit
fixup: Combine with previous commit, discard commit message
drop: Remove commit
```

## Cherry-Picking

### Cherry-Pick Commits
```bash
# Pick a specific commit from another branch
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick <commit1-hash> <commit2-hash>

# Cherry-pick a range of commits
git cherry-pick <start-commit-hash>..<end-commit-hash>

# Cherry-pick with no commit (just apply changes)
git cherry-pick -n <commit-hash>
```

## Stashing

### Stash Operations
```bash
# Stash current changes
git stash save "Work in progress"

# List stashes
git stash list

# Apply latest stash
git stash apply

# Apply specific stash
git stash apply stash@{2}

# Pop (apply and remove) latest stash
git stash pop

# Create branch from stash
git stash branch feature/new-branch
```

## Resetting and Reverting

### Reset Types
```bash
# Soft reset (keeps changes in staging)
git reset --soft HEAD~1

# Mixed reset (default, unstages changes)
git reset HEAD~1

# Hard reset (discards all changes)
git reset --hard HEAD~1

# Revert a public commit
git revert <commit-hash>
```

## Advanced Operations

### Reflog (Recover Lost Commits)
```bash
# View all recent actions
git reflog

# Recover a deleted branch
git branch recovery-branch <commit-hash>
```

### Submodules
```bash
# Add a submodule
git submodule add <repository-url> <path>

# Update submodules
git submodule update --init --recursive
```

### Worktree (Multiple Working Directories)
```bash
# Add a worktree
git worktree add ../path/to/new/worktree feature/branch

# List worktrees
git worktree list

# Remove a worktree
git worktree remove ../path/to/worktree
```

## Workflow Scenarios

### Scenario 1: Feature Development
```bash
# Create feature branch
git checkout -b feature/user-auth

# Work on feature, make commits
git add .
git commit -m "Implement user authentication"

# Rebase onto main before merging
git checkout main
git pull origin main
git checkout feature/user-auth
git rebase main

# Merge with squash
git checkout main
git merge --squash feature/user-auth
git commit -m "Add user authentication feature"
```

### Scenario 2: Hotfix
```bash
# Create hotfix branch
git checkout -b hotfix/critical-bug main

# Fix bug, commit
git add .
git commit -m "Fix critical security vulnerability"

# Cherry-pick to other branches if needed
git checkout develop
git cherry-pick <hotfix-commit-hash>
```

## Best Practices
- Always pull before pushing
- Use meaningful commit messages
- Prefer rebasing over merging for cleaner history
- Don't rebase public/shared branches
- Use feature branches for development
- Regularly clean up local branches

## Troubleshooting
- `git reflog` is your friend for recovering lost work
- Use `git reset` and `git revert` carefully
- Understand the difference between `git reset` and `git revert`

## Recommended Tools
- GitHub CLI
- GitKraken
- Sourcetree
- Git Extensions
