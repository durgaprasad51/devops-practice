       **GIT Initial Setup and commands**

# Initial Setup - Configure Git for first time use with your identity

# Set user info (required for commits)
git config --global user.name "Your Name"
git config --global user.email "email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Check settings
git config --list


# Create & Clone Repositories - Start a new project or get an existing one

# Create new repository
git init
git init <directory>

# Clone existing repository
git clone <url>
git clone <url> <directory>

# Clone specific branch
git clone -b <branch> <url>


**Making Changes**
# Check Status & Differences - See what has changed in your working directory

# Check status
git status
git status -s  # Short format

# View changes
git diff              # Unstaged changes
git diff --staged     # Staged changes
git diff HEAD         # All changes
git diff <branch>     # Compare with branch

# Stage & Commit Changes - Save your work to the repository history

# Stage files
git add <file>
git add .              # All files
git add -A             # All including deletions
git add -p             # Interactive staging

# Commit
git commit -m "message"
git commit -am "message"  # Add + commit tracked files
git commit --amend       # Modify last commit

# Log & History - Explore repository history and find specific commits

# View log
git log
git log --oneline
git log --graph --all
git log -n 5           # Last 5 commits

# Search commits
git log --grep="keyword"
git log --author="name"
git log --since="2 weeks ago"

# File history
git log -- <file>
git log -p <file>      # With changes
git blame <file>       # Line-by-line authorship

**Stashing Changes**
# Save Work Temporarily - Store uncommitted changes for later without committing

# Stash changes
git stash
git stash push -m "description"

# View stashes
git stash list

# Apply stash
git stash apply         # Apply latest
git stash apply stash@{n}  # Apply specific
git stash pop           # Apply and delete

# Delete stash
git stash drop stash@{n}
git stash clear         # Delete all

**Branching**
# Branch Management - Create, list, and delete branches for parallel development

# List branches
git branch            # Local
git branch -r         # Remote
git branch -a         # All

# Create branch
git branch <name>
git checkout -b <name>  # Create and switch

# Switch branches
git checkout <branch>
git switch <branch>     # Git 2.23+

# Delete branch
git branch -d <branch>  # Safe delete
git branch -D <branch>  # Force delete

# Merging & Rebasing - Combine changes from different branches

# Merge
git merge <branch>
git merge --no-ff <branch>  # No fast-forward

# Abort merge
git merge --abort

# Rebase
git rebase <branch>
git rebase -i HEAD~3        # Interactive

# Abort/continue rebase
git rebase --abort
git rebase --continue

**Working with Remotes**
#Remote Repositories - Connect and sync with remote repositories

# Show remotes
git remote
git remote -v

# Add remote
git remote add origin <url>

# Change remote URL
git remote set-url origin <new-url>

# Remove remote
git remote remove origin

# Rename remote
git remote rename origin upstream

**Fixing Mistakes**
# Undo Changes - Revert uncommitted changes in your working directory

# Discard working changes
git checkout -- <file>
git restore <file>        # Git 2.23+

# Unstage files
git reset HEAD <file>
git restore --staged <file>  # Git 2.23+

# Discard all local changes
git reset --hard HEAD
git clean -fd            # Remove untracked files

# Revert Commits - Undo committed changes by creating new commits

# Revert commit (safe)
git revert <commit>
git revert HEAD        # Revert last commit

# Revert range
git revert <oldest>..<newest>

# Revert merge commit
git revert -m 1 <merge-commit>

# Reset to commit (⚠️ rewrites history)
git reset --hard <commit>

**Merge Conflicts**
# Resolve Conflicts - Handle and fix merge conflicts when combining branches

# During merge conflict
git status              # See conflicted files

# Resolve conflicts manually, then:
git add <resolved-file>
git commit             # Complete merge

# Abort merge
git merge --abort

# Use specific version
git checkout --ours <file>    # Keep current branch
git checkout --theirs <file>  # Take other branch

# Version Tagging - Mark specific commits as releases or milestones

# List tags
git tag
git tag -l "v1.*"     # Pattern matching

# Create tag
git tag v1.0.0
git tag -a v1.0.0 -m "Version 1.0.0"  # Annotated

# Tag specific commit
git tag v1.0.0 <commit>

# Push tags
git push origin v1.0.0
git push origin --tags

# Delete tag
git tag -d v1.0.0
git push origin --delete v1.0.0


# Advance Topics

# Submodules - Include other Git repositories within your project

# Add submodule
git submodule add <url> <path>

# Clone with submodules
git clone --recursive <url>

# Update submodules
git submodule update --init
git submodule update --remote

# Bisect (Find Bugs) - Binary search through history to find the commit that introduced a bug

# Start bisect
git bisect start
git bisect bad          # Current commit is bad
git bisect good <commit>  # Known good commit

# Test each commit
git bisect good         # Mark as good
git bisect bad          # Mark as bad

# Finish
git bisect reset

# Worktrees - Work on multiple branches simultaneously in different directories


# Add worktree
git worktree add <path> <branch>
git worktree add ../feature-branch feature

# List worktrees
git worktree list

# Remove worktree
git worktree remove <path>
