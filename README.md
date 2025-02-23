# squash_git_commit

# Squash All Commits into a Single Commit and Create a New Development Branch

This guide explains how to squash all commits on the `main` branch into a single commit while preserving the full commit history in a backup branch. It also covers setting up a new `dev` branch for further development.

---

## ✅ Prerequisites

Make sure you have Git installed and your repository cloned locally.

---

## 🔒 Step 1: Backup Your Existing Commit History

Before squashing, create a backup branch to preserve all 700 existing commits.

```bash
# Checkout the main branch
git checkout main

# Create a backup branch
git checkout -b backup-full-history

# Push the backup branch to remote
git push origin backup-full-history
```

This ensures that all existing commits are safe and accessible later if needed.

---

## 🔄 Step 2: Reset `main` to the First Commit

This step will squash all commits into one while keeping the changes intact.

```bash
# Checkout the main branch
git checkout main

# Soft reset to the first commit
git reset $(git rev-list --max-parents=0 HEAD)
```

All changes will remain staged, ready for a new commit.

---

## ✅ Step 3: Create a Single New Commit

Now, commit all staged changes as one single commit:

```bash
# Stage all changes
git add .

# Create a new commit
git commit -m "Squashed all previous commits into one"
```

---

## 🚀 Step 4: Force Push to Update `main`

Since this rewrite changes the commit history, force-push the changes:

```bash
# Force push the squashed commit to the remote main branch
git push --force
```

> ⚠️ **Warning:** This will overwrite the commit history of the `main` branch on the remote repository.

---

## 🌿 Step 5: Create and Switch to `dev` Branch

Now, create a new development branch from the updated `main`:

```bash
# Create and switch to the dev branch
git checkout -b dev

# Push the dev branch to remote
git push origin dev
```

---

## ✅ Outcome

- **`main` branch** ➔ Single commit with all code intact.
- **`backup-full-history` branch** ➔ All 700 commits preserved.
- **`dev` branch** ➔ Ready for new development work based on the squashed `main`.

---

## 📌 Notes

- You can always restore your original commit history from the `backup-full-history` branch if needed.
- Make sure to notify your team about the history rewrite if working in a collaborative environment.

---

## 🔗 Useful Commands

- Check commit history:
  ```bash
  git log --oneline
  ```
- Restore from backup:
  ```bash
  git checkout backup-full-history
  ```

---

**Author:** MD Saiful Hossain  
**GitHub:** [eamon831](https://github.com/eamon831)

