# Team Onboarding Checklist - Git & GitHub Setup

Use this checklist to onboard your 4 teammates to the Git workflow.

---

## ✅ Pre-Onboarding (Repo Owner - Ahsan)

- [ ] Ensure branch protection ruleset is active on main branch
- [ ] Enable branch protection on development branch (optional but recommended)
- [ ] Share GitHub repository link with all teammates
- [ ] Add teammates as "Write" collaborators to repository
- [ ] Review and finalize CONTRIBUTING.md file
- [ ] Review and finalize GIT_WORKFLOW_GUIDE.md
- [ ] Review and finalize GIT_QUICK_REFERENCE.md
- [ ] Schedule team onboarding meeting (15-20 minutes)

---

## 👥 Per-Teammate Onboarding

Repeat this checklist for each of your 4 teammates:

### Team Member Name: ______________________

#### Step 1: GitHub Account & Access (5 min)
- [ ] Teammate has GitHub account
- [ ] Teammate accepted repository invitation
- [ ] Teammate can access: https://github.com/ahsanjaved-dev/genius365
- [ ] Verify "Collaborators" page shows teammate as "Write" permission

#### Step 2: Local Setup (10 min)

Have teammate run these commands:
```bash
# Clone repository
git clone https://github.com/ahsanjaved-dev/genius365.git
cd genius365

# Configure Git (first time only)
git config user.name "Their Full Name"
git config user.email "their.email@example.com"

# Verify setup
git config --list
git remote -v
```

**Checklist:**
- [ ] Repository cloned successfully
- [ ] Git configured with their name/email
- [ ] Remote URL shows correct repository
- [ ] Can see all files locally

#### Step 3: Read Documentation (10 min)

Have teammate read these files in this order:

1. [ ] Read `GIT_QUICK_REFERENCE.md` (5 min)
   - ✅ Understand basic commands
   - ✅ Can see copy-paste commands

2. [ ] Read `CONTRIBUTING.md` (10 min)
   - ✅ Understand workflow
   - ✅ Understand PR process
   - ✅ Know branch naming conventions

3. [ ] Read `GIT_WORKFLOW_GUIDE.md` (15 min)
   - ✅ Understand three-tier branching
   - ✅ Understand daily workflow
   - ✅ Know what to do with PRs

#### Step 4: First Feature Practice (20 min)

Have teammate do a "practice run":

**What they should do:**
1. [ ] Create a test feature branch
   ```bash
   git checkout development
   git pull origin development
   git checkout -b feature/test-setup
   ```

2. [ ] Create a test file with their name
   ```bash
   echo "Hello from [Name]" > teammates/[name]-test.txt
   ```

3. [ ] Commit and push
   ```bash
   git add .
   git commit -m "test: add onboarding test file for [name]"
   git push origin feature/test-setup
   ```

4. [ ] Create Pull Request on GitHub
   - Go to: https://github.com/ahsanjaved-dev/genius365/pulls
   - Click "New Pull Request"
   - Base: `development`
   - Compare: `feature/test-setup`
   - Title: "test: onboarding test for [name]"
   - Create PR

5. [ ] You (Ahsan) review and merge
   - [ ] Approve the PR
   - [ ] Merge to development
   - [ ] Confirm branch deletion

6. [ ] Teammate verifies merge
   ```bash
   git checkout development
   git pull origin development
   # Should see their test file exists
   ```

**Verification:**
- [ ] Test file appears on development branch
- [ ] PR shows as merged
- [ ] Teammate understands the flow

#### Step 5: Explain Protection Rules (5 min)

Explain to teammate:

- [ ] Main branch is protected
  - ✅ "You can never push directly to main"
  - ✅ "Main can only receive merges from development"
  - ✅ "Every merge needs review"

- [ ] Development branch best practices
  - ✅ "Always create feature branches from development"
  - ✅ "Create PRs to development (not main)"
  - ✅ "Wait for review before merge"

- [ ] Their workflow
  - ✅ "You create feature/ branches from development"
  - ✅ "Push to your branch"
  - ✅ "Create PR to development"
  - ✅ "I review and merge"
  - ✅ "Delete your branch after merge"

#### Step 6: Explain Release Process (5 min)

Explain to teammate:

- [ ] Weekly releases
  - ✅ "Every Friday we merge development to main"
  - ✅ "This triggers production deployment"
  - ✅ "Only I can do this"

- [ ] Their features go live
  - ✅ "Features merged to dev are in staging"
  - ✅ "Friday release puts them in production"
  - ✅ "Production users see their work"

#### Step 7: Common Scenarios (10 min)

Explain these scenarios:

- [ ] **"Code review feedback"**
  - ✅ If you request changes:
  - ✅ "Make changes on your branch"
  - ✅ "Commit and push again"
  - ✅ "PR updates automatically"

- [ ] **"Update your branch"**
  - ✅ If development gets new features:
  - ✅ `git fetch origin`
  - ✅ `git rebase origin/development`
  - ✅ This keeps branch current

- [ ] **"Merge conflict"**
  - ✅ If you get a conflict:
  - ✅ "Open file and look for <<<<<<<<"
  - ✅ "Fix the conflict"
  - ✅ "Commit and push again"

- [ ] **"Accidentally pushed to wrong branch"**
  - ✅ "Contact me immediately"
  - ✅ "We can fix it together"

#### Step 8: Set Up IDE (5 min)

If using VSCode with Git GUI:

- [ ] Install "GitHub Pull Requests and Issues" extension
- [ ] Sign in with GitHub account
- [ ] Can see PRs in IDE sidebar
- [ ] Can create PRs from IDE

**Or use Git CLI:**
- [ ] Terminal ready for git commands
- [ ] Can run `git` commands from project folder
- [ ] PATH includes git binary

#### Step 9: Configure IDE Git Settings (Optional)

If teammate uses different IDE:

- [ ] Configure IDE Git integration
- [ ] Set author name in commits
- [ ] Configure push to "current branch"
- [ ] Set up branch tracking

#### Step 10: Final Check (5 min)

Ask teammate to demonstrate:

- [ ] ✅ "Show me how you'd create a new feature branch"
  - Correct answer: `git checkout -b feature/name`

- [ ] ✅ "How would you save your work?"
  - Correct answer: `git add . && git commit -m "message"`

- [ ] ✅ "How would you get latest development?"
  - Correct answer: `git fetch origin && git rebase origin/development`

- [ ] ✅ "What's the branch naming convention?"
  - Correct answer: `feature/`, `fix/`, `docs/`

- [ ] ✅ "Where do you create PRs?"
  - Correct answer: GitHub website, base=development

---

## 📋 Ongoing Maintenance Checklist

### Daily (You - Ahsan)
- [ ] Check for new PRs
- [ ] Review teammate PRs
- [ ] Approve and merge PRs to development
- [ ] Monitor for merge conflicts
- [ ] Check development branch stability

### Weekly
- [ ] Monday: Prepare for new features
- [ ] Friday: Release to production
  - [ ] Merge development → main
  - [ ] Tag release (v1.5.0, etc.)
  - [ ] Deploy to production

### Monthly
- [ ] Review git log for patterns
- [ ] Update documentation if needed
- [ ] Archive old feature branches
- [ ] Review teammate git practices
- [ ] Provide feedback on workflow

---

## 🚨 Emergency Procedures

### If Teammate Pushes to Main by Mistake
```bash
# Contact them immediately and do:
git checkout main
git reset --hard origin/main~1  # Go back one commit
git push --force-with-lease origin main

# Then explain it should not have happened
# Review branch protection rules with them
```

### If Teammate Can't Access Repository
- [ ] Check GitHub "Collaborators" page
- [ ] Verify they're added as "Write" permission
- [ ] Have them accept repository invitation email
- [ ] Verify they're logged into correct GitHub account

### If Someone Has Merge Conflicts
- [ ] Have them run: `git status` (to see conflicted files)
- [ ] Open each file and look for `<<<<<<<`, `=======`, `>>>>>>>`
- [ ] Remove conflict markers, keeping correct code
- [ ] `git add .` and `git commit -m "resolve: merge conflict"`
- [ ] `git push origin` to update PR

### If Accidental Force Push Happens
- [ ] GitHub has backup (go to repository activity)
- [ ] Or use: `git reflog` on your local machine
- [ ] Contact GitHub support if needed for recovery

---

## 📞 Support Resources

### Provide These Links to Teammates:

**Git Learning:**
- Git Basics: https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository
- Interactive Learning: https://learngitbranching.js.org/
- GitHub Skills: https://skills.github.com/

**Repository Resources:**
- Repository: https://github.com/ahsanjaved-dev/genius365
- CONTRIBUTING.md: In repository root
- GIT_WORKFLOW_GUIDE.md: In repository root
- GIT_QUICK_REFERENCE.md: In repository root
- GIT_VISUAL_GUIDE.md: In repository root

**Direct Help:**
- Direct message on Slack: @Ahsan
- Create GitHub issue with question
- Schedule a call for complex issues

---

## ✅ Success Criteria - Teammate is Ready When:

- [ ] They understand three-tier branching (main, dev, feature)
- [ ] They can create and push to a feature branch
- [ ] They can create a PR correctly (base=development)
- [ ] They understand they cannot push to main
- [ ] They know to wait for review before merging
- [ ] They can handle code review feedback
- [ ] They understand weekly release process
- [ ] They know who to contact for help
- [ ] They've done at least 1 successful PR cycle

---

## 📝 Documentation Handoff Checklist

Before teammate starts real work:

- [ ] Teammate has read all documentation files
- [ ] Teammate has printed or bookmarked GIT_QUICK_REFERENCE.md
- [ ] Teammate knows where to find documentation
- [ ] Teammate has asked all questions
- [ ] Teammate is comfortable with the workflow
- [ ] You (Ahsan) have cleared them to start

---

## 🎓 First Week Expectations

### Days 1-2 (Monday-Tuesday):
- [ ] Teammate creates first real feature branch
- [ ] Teammate makes commits and pushes
- [ ] Teammate creates first PR
- [ ] You review and provide feedback

### Days 3-5 (Wednesday-Friday):
- [ ] Teammate responds to feedback
- [ ] You approve and merge their first PR ✅
- [ ] Teammate's code ships with Friday release 🚀
- [ ] Celebrate their first contribution! 🎉

---

## 📊 Team Status Tracking

| Teammate | Onboarded | First PR Merged | Feedback | Status |
|----------|-----------|-----------------|----------|--------|
| Ali | [ ] Date: __ | [ ] Date: __ | [ ] Notes: __ | __ |
| Sara | [ ] Date: __ | [ ] Date: __ | [ ] Notes: __ | __ |
| Mike | [ ] Date: __ | [ ] Date: __ | [ ] Notes: __ | __ |
| Lisa | [ ] Date: __ | [ ] Date: __ | [ ] Notes: __ | __ |

---

## 💡 Tips for Successful Onboarding

✅ **DO:**
- Explain the "why" behind the workflow
- Let them do practice runs first
- Be patient with git questions
- Celebrate their first PR merge
- Provide clear feedback on PRs
- Share this checklist with them

❌ **DON'T:**
- Rush the setup process
- Assume they know git already
- Give complex commands without explanation
- Be too strict with first submissions
- Skip the documentation reading
- Make exceptions to the workflow

---

## 🎯 Long-Term Goals

After 1 month:
- [ ] Team member can workflow independently
- [ ] Team member creates 4-8 PRs per week
- [ ] Team member gets PR approved on first try (usually)
- [ ] Team member helps other teammates with git

After 3 months:
- [ ] Team member is git workflow expert
- [ ] Team member can resolve merge conflicts alone
- [ ] Team member mentors new team members
- [ ] Team member suggests workflow improvements

---

**Print this checklist and use it for each teammate!** ✅

Questions? Contact Ahsan.

