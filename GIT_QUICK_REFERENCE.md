# Git Quick Reference Card

## 🎯 Essential Commands - Copy & Paste Ready

### Initial Setup (First Time Only)
```bash
git clone https://github.com/ahsanjaved-dev/genius365.git
cd genius365
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

---

## 🚀 Start New Feature (Every Feature)

```bash
# 1. Switch to development
git checkout development

# 2. Update development branch
git pull origin development

# 3. Create new feature branch
git checkout -b feature/your-feature-name

# 4. Start working on your feature
# (edit files, add code)
```

---

## 💾 Save Your Work (Throughout the Day)

```bash
# Check what changed
git status

# Stage all changes
git add .

# Or stage specific file
git add filename.tsx

# Commit with message
git commit -m "feat: add new feature"

# Push to GitHub
git push origin feature/your-feature-name
```

---

## 🔄 Keep Your Branch Updated

```bash
# Get latest changes from development
git fetch origin

# Update your branch
git rebase origin/development

# Or use merge (alternative)
git merge origin/development

# Push updated branch
git push origin feature/your-feature-name
```

---

## 📤 Submit for Review (When Ready)

```bash
# 1. Make final commit
git commit -m "feat: complete feature"

# 2. Push to GitHub
git push origin feature/your-feature-name

# 3. Go to GitHub and create PR:
#    - Base: development
#    - Compare: feature/your-feature-name
#    - Fill description
#    - Submit
```

---

## 📝 After Code Review (If Changes Needed)

```bash
# 1. Make requested changes
# (edit files)

# 2. Stage and commit
git add .
git commit -m "fix: address review feedback"

# 3. Push (PR updates automatically)
git push origin feature/your-feature-name
```

---

## 🎉 After Merge (Cleanup)

```bash
# 1. Switch to development
git checkout development

# 2. Update development
git pull origin development

# 3. Delete local feature branch
git branch -d feature/your-feature-name

# 4. Delete remote branch
git push origin --delete feature/your-feature-name
```

---

## 🔍 View Information

```bash
# See all branches
git branch -a

# See commit history
git log

# See changes not staged
git diff

# See changes staged
git diff --staged

# See status
git status
```

---

## ❌ Undo Things

```bash
# Undo changes in file (before commit)
git checkout filename.tsx

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (delete changes)
git reset --hard HEAD~1

# Unstage file
git reset filename.tsx
```

---

## ⚠️ When Things Go Wrong

### "I committed to wrong branch"
```bash
git reset --soft HEAD~1  # Undo commit, keep changes
git checkout correct-branch
git commit -m "message"
```

### "I need to resolve a conflict"
```bash
# 1. Open file and look for:
#    <<<<<<< HEAD
#    your code
#    =======
#    their code
#    >>>>>>> branch-name

# 2. Edit to keep correct code

# 3. Mark as resolved
git add filename.tsx
git commit -m "resolve conflict"
```

### "I want to see what changed"
```bash
git diff feature/your-branch development
git log --oneline feature/your-branch
```

---

## ✅ Daily Checklist

- [ ] `git status` - see what changed
- [ ] `git add .` - stage changes
- [ ] `git commit -m "..."` - commit with message
- [ ] `git push origin feature/...` - push to GitHub
- [ ] Create/update PR on GitHub
- [ ] Respond to review feedback

---

## 📋 PR Checklist Before Submitting

- [ ] Branch name follows convention (feature/fix/docs/etc)
- [ ] All commits have clear messages
- [ ] Branch is up to date with development
- [ ] Code tested locally
- [ ] No console errors
- [ ] No secrets committed (check .gitignore)
- [ ] PR title is clear
- [ ] PR description explains what/why/how

---

## 🎯 Three-Tier Flow Reminder

```
Your Branch (feature/...)
         ↓
    Create PR to development
         ↓
    Repo owner reviews ✅
         ↓
    Merged to development
         ↓
    Testing/QA on development
         ↓
    Weekly: development → main (Release)
         ↓
    Production 🚀
```

---

## 🚫 NEVER DO THIS

```bash
# ❌ DON'T push to main
git push origin main

# ❌ DON'T force push
git push --force origin feature/your-branch

# ❌ DON'T commit sensitive data
git add .env  # NO!
git add passwords.txt  # NO!

# ❌ DON'T skip PR reviews
git merge feature/your-branch  # NO! Use PR instead

# ❌ DON'T forget to pull first
git push  # Check for conflicts first!
```

---

## 📞 Need Help?

- **Git command help**: `git help <command>`
- **Merge conflict**: Ask Ahsan
- **PR feedback**: Reply in PR comments
- **Branch issues**: Contact Ahsan immediately

---

## 🔗 Useful Links

- **Repo**: https://github.com/ahsanjaved-dev/genius365
- **CONTRIBUTING**: Read CONTRIBUTING.md in repo
- **Workflow Guide**: Read GIT_WORKFLOW_GUIDE.md in repo

---

**Print this card and keep it handy! 🖨️**

