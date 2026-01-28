# Contributing to Genius365

Welcome to the Genius365 team! This document outlines our Git workflow and best practices for collaborating on this project.

---

## 📋 Table of Contents
1. [Git Workflow Overview](#git-workflow-overview)
2. [Initial Setup](#initial-setup)
3. [Development Workflow](#development-workflow)
4. [Branch Naming Conventions](#branch-naming-conventions)
5. [Commit Message Guidelines](#commit-message-guidelines)
6. [Pull Request Process](#pull-request-process)
7. [Merging Strategy](#merging-strategy)
8. [Common Commands](#common-commands)
9. [Troubleshooting](#troubleshooting)

---

## 🔄 Git Workflow Overview

Our repository follows a **three-tier branching strategy**:

```
┌─────────────────────────────────────────────────────────────┐
│                    MAIN (Production)                        │
│                   🔒 Protected Branch 🔒                    │
│         Only repo owner can merge from development          │
└─────────────────────────────────────────────────────────────┘
                            ▲
                            │ Merge (after testing)
                            │
┌─────────────────────────────────────────────────────────────┐
│              DEVELOPMENT (Staging/Integration)              │
│                    Repo owner merges here                   │
│            All feature branches merge here first            │
└─────────────────────────────────────────────────────────────┘
                            ▲
        ┌───────────────────┼───────────────────┐
        │                   │                   │
     Feature-1          Feature-2           Feature-3
  (Teammate A)         (Teammate B)        (Teammate C)
  ✅ Personal Branch    ✅ Personal Branch  ✅ Personal Branch
```

### Key Points:
- **main**: Production-ready code (PROTECTED - no direct pushes)
- **development**: Integration branch for all features
- **feature/**: Individual teammate branches for active work

---

## 🚀 Initial Setup

### Step 1: Clone the Repository
```bash
git clone https://github.com/ahsanjaved-dev/genius365.git
cd genius365
```

### Step 2: Configure Git (First Time Only)
```bash
# Set your name
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your.email@example.com"

# Optional: Make these settings for this repo only
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### Step 3: Verify Remote URLs
```bash
git remote -v
# Output should show:
# origin  https://github.com/ahsanjaved-dev/genius365.git (fetch)
# origin  https://github.com/ahsanjaved-dev/genius365.git (push)
```

### Step 4: Fetch Latest Changes
```bash
git fetch origin
git checkout development
git pull origin development
```

---

## 💻 Development Workflow

### Step 1: Create Your Feature Branch

Always create your branch from `development` (NOT from `main`):

```bash
# Make sure you're on development
git checkout development

# Pull latest changes
git pull origin development

# Create your feature branch with descriptive name
git checkout -b feature/your-feature-name
```

### Step 2: Make Changes and Commit

```bash
# See what files changed
git status

# Stage your changes
git add .

# Or stage specific files
git add filename.tsx

# Commit with clear message
git commit -m "Add login form component"
```

### Step 3: Push to Your Branch

```bash
# First push (sets up tracking)
git push -u origin feature/your-feature-name

# Subsequent pushes
git push origin feature/your-feature-name
```

### Step 4: Create a Pull Request

1. Go to GitHub: https://github.com/ahsanjaved-dev/genius365
2. Click **"Pull requests"** tab
3. Click **"New pull request"** button
4. Set:
   - **Base branch**: `development` (NOT main!)
   - **Compare branch**: `feature/your-feature-name`
5. Fill out the PR template:
   ```
   ## Description
   What changes did you make?
   
   ## Type of Change
   - [ ] Bug fix
   - [ ] New feature
   - [ ] Documentation update
   
   ## How to Test
   Steps to verify the changes work
   
   ## Checklist
   - [ ] Code follows style guidelines
   - [ ] Self-review completed
   - [ ] No breaking changes
   ```
6. Click **"Create pull request"**

### Step 5: Wait for Review

- **Repo owner** (Ahsan) will review your code
- If changes requested, make them on your branch
- Commit and push: `git push origin feature/your-feature-name`
- PR automatically updates

### Step 6: Merge to Development

Once approved ✅:
- Repo owner merges PR to `development`
- Your branch can be deleted (GitHub offers this option)

---

## 📝 Branch Naming Conventions

Use clear, descriptive branch names:

```
feature/feature-name           # New feature
  feature/login-form
  feature/payment-integration
  feature/dashboard-redesign

fix/bug-name                   # Bug fix
  fix/auth-token-expiry
  fix/mobile-layout-issue

docs/documentation-name        # Documentation
  docs/api-endpoints
  docs/setup-guide

refactor/refactor-name         # Code refactoring
  refactor/api-client
  refactor/database-queries
```

**Rules:**
- Use lowercase
- Separate words with hyphens
- No spaces or underscores
- Be specific and descriptive

---

## 📌 Commit Message Guidelines

Write clear, concise commit messages:

```bash
# Good ✅
git commit -m "Add authentication middleware"
git commit -m "Fix null pointer exception in payment handler"
git commit -m "Update user profile endpoint documentation"

# Bad ❌
git commit -m "fixes"
git commit -m "changes"
git commit -m "Update"
```

### Format:
```
<type>: <subject>

<body (optional)>
```

### Types:
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation
- `refactor:` - Code refactoring
- `style:` - Formatting changes
- `test:` - Adding/updating tests
- `chore:` - Dependencies, build files

### Examples:
```bash
git commit -m "feat: add user authentication"
git commit -m "fix: resolve payment calculation error"
git commit -m "docs: update API documentation"
```

---

## 🔀 Pull Request Process

### Before Creating a PR:
```bash
# 1. Make sure your branch is up to date
git fetch origin
git rebase origin/development

# 2. Run any tests (if applicable)
npm run test

# 3. Check code style
npm run lint
```

### PR Title Format:
```
[Type] Short description

Examples:
[Feature] Add two-factor authentication
[Fix] Fix memory leak in WebSocket handler
[Docs] Update deployment guide
```

### PR Description Template:
```markdown
## Description
Brief explanation of what this PR does

## Related Issue
Fixes #123 (if applicable)

## Type of Change
- [ ] New feature
- [ ] Bug fix
- [ ] Breaking change
- [ ] Documentation

## Testing
How to test these changes:
1. Step 1
2. Step 2

## Checklist
- [ ] Code follows project style
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] No new warnings generated
- [ ] Tests pass locally
```

---

## 🔗 Merging Strategy

### Workflow Timeline:

```
Week Timeline Example:
──────────────────────────────────────

Monday:
  Team A creates feature/auth → pushes → creates PR
  Review → Approve → Merge to development ✅

Tuesday:
  Team B creates feature/payment → pushes → creates PR
  Review → Approve → Merge to development ✅

Wednesday:
  Team C creates feature/dashboard → pushes → creates PR
  Review → Approve → Merge to development ✅

Friday (Release Day):
  Owner: Merge development → main → Tag v1.0.0 → Deploy
```

### Repo Owner (Ahsan) Responsibilities:

#### Daily: Review and Merge PRs to Development
```bash
# 1. Check for new PRs
git fetch origin

# 2. Review code on GitHub

# 3. Once approved, merge to development
git checkout development
git pull origin development
git merge feature/teammate-feature-name
git push origin development
```

#### Weekly/Release: Merge Development to Main
```bash
# 1. Ensure development is stable
git checkout development
git pull origin development

# 2. Create release PR
git checkout main
git pull origin main
git merge development
git push origin main

# 3. Tag the release
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0

# 4. Deploy to production
# (Follow your deployment process)
```

---

## 📚 Common Commands

### View Branches
```bash
# List local branches
git branch

# List remote branches
git branch -r

# List all branches
git branch -a
```

### Update Your Branch
```bash
# Get latest changes from development
git fetch origin
git rebase origin/development

# Or use merge (alternative to rebase)
git merge origin/development
```

### View Commit History
```bash
# See recent commits
git log

# See commits with graph
git log --oneline --graph --all

# See commits for specific branch
git log feature/your-branch
```

### View Changes
```bash
# See unstaged changes
git diff

# See staged changes
git diff --staged

# See changes in specific file
git diff filename.tsx
```

### Undo Changes
```bash
# Undo uncommitted changes
git checkout filename.tsx

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Remove accidental committed file
git rm --cached filename.tsx
```

### Clean Up Branches
```bash
# Delete local branch
git branch -d feature/your-branch

# Force delete local branch
git branch -D feature/your-branch

# Delete remote branch (after PR merged)
git push origin --delete feature/your-branch
```

---

## ⚠️ Troubleshooting

### Problem: "Permission denied (publickey)"
**Solution**: Set up SSH keys
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Copy key to GitHub settings
cat ~/.ssh/id_ed25519.pub
# Paste into GitHub → Settings → SSH Keys
```

### Problem: "Your branch is behind 'origin/development'"
**Solution**: Update your branch
```bash
git fetch origin
git pull origin development
```

### Problem: "Conflict in merge"
**Solution**: Resolve conflicts
```bash
# 1. Open conflicted files in editor
# 2. Look for <<<<<<, ======, >>>>>>
# 3. Edit to keep correct code
# 4. Save the file
git add filename.tsx
git commit -m "Resolve merge conflict"
```

### Problem: "Cannot push to main branch"
**Solution**: This is expected! You should:
```bash
# Push to your feature branch instead
git push origin feature/your-branch

# Create PR to development first
# Repo owner merges development to main
```

### Problem: "Accidentally committed to main"
**Solution**: Create a PR instead
```bash
# Create new branch with your changes
git checkout -b feature/your-feature
git push origin feature/your-feature

# Reset main to origin
git checkout main
git reset --hard origin/main
git push --force origin main
```

---

## 📋 Quick Reference Checklist

Before pushing your code:
- [ ] Branch created from `development` (not main)
- [ ] Branch name follows convention (`feature/`, `fix/`, etc.)
- [ ] All changes committed with clear messages
- [ ] Code tested locally
- [ ] No console errors or warnings
- [ ] `.gitignore` is respected (no secrets, env files, etc.)

Before creating PR:
- [ ] Branch is up to date with `development`
- [ ] Conflicts resolved (if any)
- [ ] PR title is clear and descriptive
- [ ] PR description includes what/why/how
- [ ] Related issue number included (if applicable)

After PR approval:
- [ ] Repo owner merges to `development`
- [ ] You delete your feature branch
- [ ] You check that changes appear in `development`

---

## ❓ Questions?

Contact the repo owner (Ahsan) for clarification on anything above.

**Happy coding! 🚀**

