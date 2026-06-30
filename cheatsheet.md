# Git Command Cheat Sheet
### Companion handout — *Git to GitHub: A Faculty Workshop* · Vels Institute of Science, Technology & Advanced Studies

A quick-reference for everyday Git & GitHub use. Keep this open in a tab while you work, or print it for your desk.

---

## 1. First-Time Setup (run once per machine)

| Command | Purpose |
|---|---|
| `git config --global user.name "Your Name"` | Set the name attached to your commits |
| `git config --global user.email "you@vistas.ac.in"` | Set the email attached to your commits (match your GitHub account) |
| `git config --global init.defaultBranch main` | Use "main" as the default branch name for new repos |
| `git config --list` | View all current settings |

---

## 2. Starting a Project

| Command | Purpose |
|---|---|
| `git init` | Turn the current folder into a new, empty Git repository |
| `git clone <repo-url>` | Download a full copy (files + history) of an existing repository |
| `git clone <repo-url> <folder-name>` | Clone into a specific folder name instead of the default |

---

## 3. The Daily Loop — Check, Stage, Commit

| Command | Purpose |
|---|---|
| `git status` | Show what's changed, staged, or untracked — run this constantly |
| `git add <file>` | Stage a specific file's changes |
| `git add .` | Stage **all** changed files in the current folder and below |
| `git add -p` | Stage changes interactively, in chunks (review before staging) |
| `git commit -m "message"` | Save the staged snapshot permanently with a description |
| `git commit -am "message"` | Stage all tracked, modified files **and** commit in one step |
| `git commit --amend` | Edit the most recent commit (message and/or contents) |

**Good commit message habits**
- Short summary line (≈50 chars), present tense: *"Fix mark calculation bug"* not *"fixed stuff"*
- One logical change per commit
- Explain **why**, not just what, if it isn't obvious

---

## 4. Looking at History

| Command | Purpose |
|---|---|
| `git log` | Full commit history — author, date, message, hash |
| `git log --oneline` | Compact one-line-per-commit view |
| `git log --oneline --graph --all` | Visual graph of all branches |
| `git diff` | Line-by-line changes not yet staged |
| `git diff --staged` | Line-by-line changes that ARE staged |
| `git show <commit-hash>` | Full details of one specific commit |
| `git blame <file>` | Who last changed each line, and in which commit |

---

## 5. Branching & Merging

| Command | Purpose |
|---|---|
| `git branch` | List local branches (current one marked with `*`) |
| `git branch <name>` | Create a new branch (doesn't switch to it) |
| `git switch <name>` | Switch to an existing branch |
| `git switch -c <name>` | Create **and** switch to a new branch |
| `git checkout <name>` | Older equivalent of `switch` (still widely used) |
| `git merge <name>` | Merge `<name>` branch into your current branch |
| `git branch -d <name>` | Delete a branch (safe — only if merged) |
| `git branch -D <name>` | Force-delete a branch (even if unmerged) — use with care |
| `git branch -a` | List all branches, including remote-tracking ones |
| `git branch -m <new-name>` | Rename the current branch |

**Resolving a merge conflict**
1. Git marks the conflicting section in the file with `<<<<<<<`, `=======`, `>>>>>>>`
2. Open the file, read both versions carefully
3. Edit to keep the correct/combined content; remove the conflict markers
4. `git add <file>` to mark it resolved
5. `git commit` to complete the merge

---

## 6. Working With Remotes (e.g. GitHub)

| Command | Purpose |
|---|---|
| `git remote add origin <url>` | Link your local repo to a remote, named "origin" |
| `git remote -v` | View configured remotes |
| `git push origin main` | Upload local commits to the remote branch |
| `git push -u origin main` | Push and remember this link, so future `push`/`pull` need no arguments |
| `git pull origin main` | Download and merge remote changes into your local branch |
| `git fetch` | Download remote changes **without** merging — inspect first |
| `git remote remove origin` | Unlink a remote |

---

## 7. The "Oops" / Undo Toolkit

| Situation | Command | Effect |
|---|---|---|
| Undo edits in a file, not yet staged | `git restore <file>` | Reverts file to last committed version |
| Accidentally staged a file | `git restore --staged <file>` | Unstages it, keeps your edits |
| Undo last commit, keep changes staged | `git reset --soft HEAD~1` | Commit removed, changes stay staged |
| Undo last commit, keep changes unstaged | `git reset HEAD~1` | Commit removed, changes back in working dir |
| Completely discard last commit & changes | `git reset --hard HEAD~1` | ⚠️ Destructive — changes are permanently lost |
| Undo a commit that's already pushed/shared | `git revert <commit>` | ✅ Safe — adds a new commit that undoes it |
| Shelve unfinished work temporarily | `git stash` | Saves changes aside, cleans working directory |
| Bring shelved changes back | `git stash pop` | Restores and removes the most recent stash |
| View all stashes | `git stash list` | Lists everything currently stashed |

> **Golden rule:** once a commit is pushed and others may have it, prefer `git revert` over `git reset --hard`. Rewriting shared history causes chaos for collaborators.

---

## 8. Ignoring Files

Create a file named `.gitignore` in your project root:

```
*.log
node_modules/
.env
__pycache__/
*.pyc
.DS_Store
```

Anything matching these patterns is never tracked or accidentally committed (passwords, build output, OS clutter).

---

## 9. Tags (marking releases / milestones)

| Command | Purpose |
|---|---|
| `git tag v1.0` | Tag the current commit (e.g. a syllabus or release version) |
| `git tag -a v1.0 -m "message"` | Annotated tag with a message |
| `git push origin v1.0` | Push a single tag to the remote |
| `git push origin --tags` | Push all tags |

---

## 10. GitHub-Specific Concepts

| Term | Meaning |
|---|---|
| **Fork** | Your own copy of someone else's repository, on GitHub |
| **Pull Request (PR)** | A formal request to merge your branch's changes, with line-by-line review |
| **Issue** | A trackable task, bug report, or idea with discussion |
| **Project (board)** | Kanban-style board (To Do / In Progress / Done) for managing issues |
| **GitHub Actions** | Automation that runs on events (e.g. test code on every push) |
| **GitHub Pages** | Free static website hosting directly from a repository |
| **README.md** | The front-page documentation of a repository |

---

## 11. Standard Student Workflow (for assignments/projects)

```
1. Fork the class/project repository on GitHub
2. git clone <your-fork-url>
3. git switch -c assignment-1
4. ... write code, edit files ...
5. git add .
6. git commit -m "Complete part 1 of assignment"
7. git push -u origin assignment-1
8. Open a Pull Request on GitHub for submission/review
```

---

## 12. Building a Campus-Interview-Ready GitHub Profile

- ✅ Pin your 4–6 **best** projects (Profile → Customize pins)
- ✅ Every project has a clear `README.md` (what it does, tech stack, how to run it)
- ✅ Commit regularly, with meaningful messages — recruiters check the contribution graph and history
- ✅ Create a special `<username>/<username>` repository with a `README.md` for a personal profile page
- ✅ Use Issues/Projects even on solo projects — shows planning skill
- 🚫 Never commit passwords, API keys, or `.env` files
- 🚫 Avoid one giant "final project" commit the night before a deadline

---

## 13. Quick Troubleshooting

| Problem | Likely Fix |
|---|---|
| "fatal: not a git repository" | You're not inside a folder with `.git` — run `git init` or `cd` into the right folder |
| Merge conflict markers in a file | Resolve manually, then `git add` + `git commit` (see Section 5) |
| Pushed to wrong branch | `git push origin --delete <branch>` then push correctly, or ask a teammate before force-pushing |
| Accidentally committed a secret file | Add it to `.gitignore`, then `git rm --cached <file>` and commit; rotate the leaked credential |
| "Your branch is behind 'origin/main'" | `git pull origin main` before pushing again |

---

*Companion to the "Git to GitHub" workshop slide deck (`index.html`) — Vels Institute of Science, Technology & Advanced Studies.*
