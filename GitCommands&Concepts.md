# Git Commands & Concepts Cheat Sheet 📝  

A quick reference guide for essential Git commands and workflows.  

---

## 🔄 **Basic Git Workflow**  

| Command | Description | Example |
|---------|------------|---------|
| `git add` | Stages changes from working directory → staging area | `git add .` |
| `git commit` | Saves staged changes to local repo with a message | `git commit -m "message"` |
| `git push` | Uploads commits to remote repo | `git push origin main` |

---

## 🔍 **Inspecting Changes**  

| Command | Description |
|---------|------------|
| `git status` | Shows modified/staged files |
| `git diff` | Displays unstaged changes |
| `git diff HEAD` | Compares working dir to latest commit |
| `git log` | Lists commit history (`--oneline` for compact view) |

---

## 🌿 **Branching & Merging**  

| Command | Description |
|---------|------------|
| `git branch` | Lists local branches (`-a` for all) |
| `git checkout -b <branch>` | Creates + switches to new branch |
| `git merge <branch>` | Merges changes from another branch |
| `git rebase <branch>` | Reapplies commits onto another branch |

---

## ⏪ **Undoing Changes**  

| Command | Description |
|---------|------------|
| `git reset <commit>` | Moves HEAD back to a commit (caution!) |
| `git revert <commit>` | Safely undoes changes via new commit |
| `git stash` | Temporarily shelves uncommitted changes |

---

## 📂 **Key Concepts**  

- **Working Directory**: Where you edit files.  
- **Staging Area (Index)**: Prepares changes for commits.  
- **Local Repository**: Your machine’s project history.  
- **Remote Repository**: Hosted version (e.g., GitHub).  

---

## 🚀 **Pro Tips**  

1. Always check `git status` before/after commands.  
2. Prefer `git revert` over `git reset` for shared branches.  
3. Use `.gitignore` to exclude files (e.g., `node_modules/`).  

---

### 📚 **Further Reading**  
- [Official Git Documentation](https://git-scm.com/doc)  
- [GitHub Guides](https://guides.github.com/)  

---

**🔁 Share this repo** with your dev network!  
✨ **Contribute** by submitting issues or PRs.  
