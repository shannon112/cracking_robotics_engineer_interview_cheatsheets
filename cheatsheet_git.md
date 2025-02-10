# 1.git, .gitignore, .git
### **`Git`** version control system (VSC)
  - Git is a **distributed version control system (DVCS)** used for tracking changes in source code during software development.
  - It allows multiple developers to collaborate on a project efficiently. 
### **`.git` Directory**
  - `.git` is a **hidden folder** that Git creates inside a project when you run `git init` (or `git clone` a repository).
  - It contains all the metadata and history of the repository, including:
    - Commit history.
    - Branch information.
    - Configuration settings.
    - Staged changes.
    - Objects and references.
  - **Delete `.git` manually** to remove Git tracking.
### **`.gitignore` File**
  - `.gitignore` is a special file used to tell Git **which files or directories to ignore** when tracking changes.
  - This helps keep unnecessary or sensitive files (e.g., logs, compiled binaries, or API keys) out of the repository.
  - Example `.gitignore`:
```plaintext
# Ignore compiled files
*.exe
*.o
*.class

# Ignore log files
logs/
*.log

# Ignore environment files
.env
```

# 2.git init, git clone, fork
### **`git init`** (init a new&local repo)
  - Initializes a new Git repository in a local directory.
  - This creates a **`.git` directory**, making it a Git repository.
```sh
mkdir my_project
cd my_project
git init
```
### **`git remote add origin`** (link existing&local repo to a existing&remote repo)
  - This command **links a local repository to a remote repository** (e.g., on GitHub, GitLab, or Bitbucket). 
  - **`origin`** is a common name for the remote repository.
  - This allows you to push (`git push`) and pull (`git pull`) changes between your local and remote repository.
```bash
git remote add origin https://github.com/yourusername/your-repo.git
```
### **`git clone`** (copy a existing&remote repo to local)
  - Copies an existing remote repository to your local machine.
  - This downloads the repository and sets up the remote connection.
```sh
git clone https://github.com/user/repository.git
```
### **Fork (copy a existing&remote repo to remote)**
  - Creates a copy of someone else's repository under your own GitHub account.
  - **When to use:** When you want to contribute to a project but don’t have direct write access.
```
1. Click "Fork" on GitHub to create a copy of the repository.
2. Clone your fork to your local machine
```
### Github new repo instruction (init a new&remote repo)
  - ![圖片](https://github.com/user-attachments/assets/4c1bb583-36c0-46d2-88c6-53838ce3e079)

# 3. git fetch, git pull
### **`git fetch` (without merging)**
- Downloads changes from the remote repository **without merging** them into your local branch.
- **When to use:** When you want to check for updates before integrating them.
- The updates are stored in `.git` but **not** merged into your working branch.
```sh
git fetch origin
git diff main origin/main  # See differences
git merge origin/main      # Merge if needed
```
### **`git pull` (with fetch+merge or fetch+rebase)**
- **Fetches and merges** changes from the remote repository into your local branch.
- **When to use:** When you want to immediately update your local branch with remote changes.
- This **fetches and merges** changes from `origin/main` into your local `main` branch.
```sh
git pull origin main
# Equivalent to:
git fetch origin
git merge origin/main
# Use `git pull --rebase` instead of `git pull` to keep a **clean history**:
git pull --rebase origin main
```

# 4. git status, git add, git commit, git push
### **`git status`**
- Shows the current state of your working directory and staging area.
- **When to use:** Before committing, to see which files are:
```sh
git status
```

| if do | then status will show | status view on VSCode GUI | status view on terminal |
|-|-|-|-|
| new files               | untracked, to be added files  | Changes, (Untracked, U)            | Untracked files |
| edited/removed files    | unstaged, to be added files   | Changes, (Modified, M)(Deleted, D) |  Changes not staged for commit |
| git add new/edit files |  staged, tracked, added, to be committed files | Staged Changes, Added, A | Changes to be committed |
| git commit files       |  committed files | to Sync Changes 1 | Your branch is ahead of 'origin/master' by 1 commit |

### **`git add`**
- Stages changes for the next commit.
- **When to use:** git add -> git commit -> git push
```sh
git add file.txt         # Stage a single file
git add .                # Stage all changes
git add *.cpp            # Stage all `.cpp` files
git add -A               # Stage all files
```

### **`git commit`**
- Saves the staged changes with a message.
- **When to use:** git add -> git commit -> git push
```sh
git commit -m "message or notes"
git commit # opens a text editor for writing a detailed message
```

### **`git push`**
- Uploads your commits to a remote repository.
- **When to use:** git add -> git commit -> git push
```sh
git push --set-upstream origin feature-branch  # First time pushing a new branch (set upstream and push)
git push -u origin feature-branch              # -u is --set-upstream
git push                            # Regularly pushing to a tracked branch
git push origin feature-branch      # Pushing without tracking (one-time push). You want to push to a specific remote repository (origin) / specific branch (feature-branch).
git push --force                    # Overwrites the remote branch with your local branch. After rewriting history (e.g., git rebase, git reset).
git push --force-with-lease         # Similar to --force, but checks if someone else pushed changes before forcing.
git push --all                      # Pushes all local branches. When you want to sync every branch.
```

# 5. git restore/reset/clean: unstaged/staged/committed
### `git restore *`, Deleted(D)(removed) -> none
### `git restore *`, Modified(M)(edited) -> none
### `git clean -f`, Untracked(U)(new) -> none
### `git reset`, staged -> unstaged
### `git reset --soft`, staged -> unstaged
### `git reset --hard`, staged -> none
### `git reset --soft HEAD~1`, committed -> staged
### `git reset --hard HEAD~1`, committed -> none
### `git revert HEAD`, 1committed -> none (2committed)
### Summary

| **Command**                     | **Effect**                          | 
|----------------------------------|-------------------------------------|
| `git restore *`                 | Modified (M) & Deleted (D) → none  | 
| `git clean -f`                  | Untracked (U) → none               | 
| `git reset`                     | Staged → Unstaged                   | 
| `git reset --soft`              | Staged → Unstaged                   | 
| `git reset --hard`              | Staged → none                       | 
| `git reset --soft HEAD~1`       | Committed → Staged                  |
| `git reset --hard HEAD~1`       | Committed → none                    | 
| `git revert HEAD`               | 1 committed → none (2committed)     | 

# 6. git log, git diff
### **`git log`**
- Shows the commit history in reverse chronological order.
```sh
git log
git log --oneline      # Compact view (commit hash + message)
git log --graph        # Visualize branches
git log --patch        # Shows commit history with diffs (line-by-line changes).
git log -- file        # Show Commit History for a File
```
### **`git diff`** or Source Control on VSCode
- Shows unstaged changes in your working directory.
- a/ = Before the change (old version).
- b/ = After the change (new version).
```sh
git diff                 # showing all unstaged (M+D) changes (without U)
git diff file            # showing specific unstaged (M+D) changes (without U)
git diff --cached        # showing staged changes
git diff HEAD~1 HEAD     # showing between commmitted changes
git diff a1b2c3d f6e7d8a # showing between commmitted changes
```
```diff
diff --git a/cheatsheet_git.md b/cheatsheet_git.md
index e69de29..d95f3ad 100644
--- a/cheatsheet_git.md
+++ b/cheatsheet_git.md
@@ -1,3 +1,3 @@
-Old line here
+New line added here
 Another unchanged line
```
### **`git blame`** or GitLens on VSCode
- Shows who last modified each line in a file.
```
git blame file.txt
```
### Comparing `git log -p -- file.txt` vs. `git blame file.txt`

| Command | Purpose | Shows Changes? | Shows Who Edited? | Best For |
|---------|---------|---------------|------------------|----------|
| `git log -p -- file.txt` | Shows file history **with diffs** |  Yes |  No | Seeing **how** a file changed over time |
| `git blame file.txt` | Shows **who edited each line** |  No |  Yes | Finding out **who changed a specific line** |

# 7. git checkout, git branch, git tag, git cherrypick
### **`git checkout`**
- Switches between branches or restores files to an older state.
```sh
git checkout feature-branch     # Switch to an existing branch
git checkout commit-hash         # Switch to an old commit
git checkout v1.0                # Switch to a tag
git checkout -b new-branch        # Create and switch to a new branch
git checkout commit-hash file.txt  # Restore a file from an old commit
```
### **`git branch`**
- Manages branches in a repository.
- To list, create, rename, or delete branches.
```sh
git branch                  # List all branches
git branch new-branch       # Create a new branch
git branch -d old-branch    # Delete a branch
git branch -m old new-name  # Rename a branch
```
### **`git tag`**
- Creates a tag (a named reference) pointing to a specific commit.
- **When to use:** To mark **important commits**, such as version releases.
```sh
git tag                                   # List all tags
git tag v1.0                              # Create a lightweight tag for the latest commit
git tag -a v1.0 -m "Version 1.0 release"  # Create an annotated tag for the latest commit
git push origin v1.0                      # Push a tag to remote
git tag -d v1.0                           # Delete a local tag
git push origin --delete v1.0             # Delete a remote tag
```
### **`git cherry-pick`**
- **Applies** a specific commit from one branch to another.
- **When to use:** When you need to **copy** a commit from another branch **without merging everything**.
```sh
git cherry-pick a1b2c3d  # Apply commit `a1b2c3d` to `main`
```

# 8. git merge, git rebase
### **`git merge`**
- Creates a **new merge commit** that combines changes from another branch.
- Pros: When you want to keep a **clear branch history** (good for team collaboration).
- Cons: Creates extra merge commits, making history messier.
```sh
git checkout main        # Switch to main branch
git merge feature-branch  # Merge changes from feature-branch into main
```
- before merge
```
*  f6e7d8a (feature-branch) Add new feature
*  4c5b6e7 Fix bug
| *  e1f2g3h (main) Previous commit on main
|/
*  d1e2f3g4 Base commit
```
- after merge (two branches + additional commit)
```
*   a1b2c3d (HEAD -> main) Merge branch 'feature-branch'
|\
| *  f6e7d8a (feature-branch) Add new feature
| *  4c5b6e7 Fix bug
|/
*  e1f2g3h Previous commit on main
*  d1e2f3g4 Base commit
```
### **`git rebase`**
- **Reapplies commits** from the feature branch **on top of** another branch.
- Makes it **look like** the branch was developed from the latest `main`.
- Pros: When you want **a cleaner linear history**.
- Cons: Can be **complex** if conflicts arise.
- Cons: **Rewrites commit history**, which can be **dangerous** if already pushed.
```sh
git checkout feature-branch  # Switch to feature branch
git rebase main              # Reapply commits on top of main
git rebase --continue        # If conflicts arise, resolve them and continue with
```
- before rebase
```
*  f6e7d8a (feature-branch) Add new feature
*  4c5b6e7 Fix bug
| *  e1f2g3h (main) Previous commit on main
|/
*  d1e2f3g4 Base commit
```
- after rebase (straight line)
```
*  f6e7d8a (feature-branch) Add new feature
*  4c5b6e7 Fix bug
*  e1f2g3h (main) Previous commit on main
*  d1e2f3g4 Base commit
```
### **Combining `rebase` with `merge`**
- This keeps a **clean feature branch** while avoiding merge commits in `main`.
```sh
# Step 1: Use `rebase` for a clean history
git checkout feature-branch
git rebase main
# Step 2: Use `merge` to bring changes into main
git checkout main
git merge feature-branch
```
- before
```
*  f6e7d8a (feature-branch) Add new feature
*  4c5b6e7 Fix bug
| *  e1f2g3h (main) Previous commit on main
|/
*  d1e2f3g4 Base commit
```
- after rebase
```
*  f6e7d8a (feature-branch) Add new feature
*  4c5b6e7 Fix bug
*  e1f2g3h (main) Previous commit on main
*  d1e2f3g4 Base commit
```
- after merge (straight line + additional commit)
```
*   a1b2c3d (HEAD -> main) Merge branch 'feature-branch'
|
* f6e7d8a Add new feature
* 4c5b6e7 Fix bug
* e1f2g3h Previous commit on main
```

# A. pipeline: resolve conflict
### **Handling Conflicts in `git merge`**
- When you merge a branch into another:
```sh
git merge feature-branch
```
- If there are conflicts, Git will pause the merge and show:
```
CONFLICT (content): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result.
```
- **Check which files have conflicts**:
```sh
 git status
```
- Example output:
```
both modified:   file.txt
```
- **Open the conflicted file in an editor** and resolve manually:
- Keep the correct version and remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
```txt
 <<<<<<< HEAD
 This is the content from main.
 =======
 This is the content from feature-branch.
 >>>>>>> feature-branch
```
- **Stage the resolved file**:
```sh
 git add file.txt
```
- **Complete the merge with a commit**:
```sh
 git commit -m "Resolved merge conflict in file.txt"
```
- **Save the result to remote**:
```
git push
```

### **Handling Conflicts in `git rebase`**
- When rebasing:
```sh
git rebase main
```
- If there are conflicts, Git will stop and show:
```
CONFLICT (content): Merge conflict in file.txt
error: could not apply a1b2c3d... Add new feature
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>" then run "git rebase --continue".
```
- **Check which files have conflicts**:
```sh
git status
```
- Example output:
```
both modified:   file.txt
```
- **Open the conflicted file in an editor** and resolve manually:
- Keep the correct version and remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
```txt
<<<<<<< HEAD
This is the content from main.
=======
This is the content from feature-branch.
>>>>>>> feature-branch
```
- **Mark the conflict as resolved**:
```sh
git add file.txt
```
- If there are more conflicts, repeat the process.
```sh
git rebase --continue
```
- If you made a mistake, **abort the rebase**:
```sh
git rebase --abort
```
- **Save the result to remote forcely**:
  - need to force push because git rebase rewrites commit history
  - Use --force-with-lease instead of --force to avoid accidentally overwriting teammates' commits.
```
git push --force-with-lease
```

| **Command** | **Conflict Resolution Steps** |
|------------|------------------------------|
| `git merge feature-branch` | 1 Check conflicts with `git status` <br> 2 Open files and fix conflicts <br> 3 `git add resolved_file` <br> 4 `git commit -m "Resolved conflicts"` <br> 5 `git push` |
| `git rebase main` | 1 Check conflicts with `git status` <br> 2 Open files and fix conflicts <br> 3 `git add resolved_file` <br> 4 `git rebase --continue` or `git rebase --abort` <br> 5 `git push --force-with-lease` |


# B. pipeline: handle large file
### **If You Push a File > 50MB**
- GitHub will allow the push **but show a warning**:
```
warning: File file.zip is 55.1 MB; this is larger than GitHub's recommended file size of 50.00 MB
```

### **If You Push a File > 100MB**
- GitHub will **reject the push** entirely:
```
remote: error: File file.zip is 150.00 MB; exceeds GitHub’s file size limit of 100MB
remote: fatal: the push was rejected
```
- **Solution:**
```sh
git reset --hard HEAD~1
```

# C. pipeline: how to squash
### **Squash using `git rebase -i HEAD~N (Interactive Rebase)`**
- If you just want to squash the **last N commit into the previous one**, use:
```sh
git rebase -i HEAD~N
```
```
pick a1b2c3d Commit message 1
pick f6e7d8a Commit message 2
pick 4c5b6e7 Commit message 3
```
- **Change `pick` to `squash` (or `s`) on the commits you want to combine**  
  - The **first commit (`pick`) will remain**.  
  - The **other commits (`squash`) will be merged** into the first one.  
```
pick a1b2c3d Commit message 1
squash f6e7d8a Commit message 2
squash 4c5b6e7 Commit message 3
```
```sh
git push --force-with-lease
```
### **Squash using `git merge --squash feature-branch`**
- If you're merging a feature branch and want to **squash everything into one commit**, use:
```sh
git checkout main
git merge --squash feature-branch
git commit -m "Merged feature-branch in one commit"
git push origin main
```

### **Squash using `git reset --soft HEAD~N`**
- If you just want to squash the **last N commit into the previous one**, use:
```sh
git reset --soft HEAD~N
git commit -m "New combined commit message"
git push --force-with-lease
```

# D. pipeline: pull request (PR) and code review
A **Pull Request (PR)** is a way to **propose changes** before merging them into the main branch.
- Allows **team review before merging**.
- Shows **commit history and changes** in a UI.
- Enables **discussions, comments, and approvals**.

1.**Create a feature branch**:  
```sh
git checkout -b feature-branch
```
2.**Make changes and commit**:  
```sh
git add .
git commit -m "Added new feature"
```
3.**Push the branch to GitHub/GitLab**:  
```sh
git push origin feature-branch
```
4.**Create a Pull Request on GitHub/GitLab**:
- Go to **GitHub → Your Repo → Pull Requests → New Pull Request**.
- Compare `feature-branch` with `main`.
- Add a **title and description** of your changes.
- Request **reviewers** from your team.
5.**Address feedback and update PR**:
```sh
git add .
git commit --amend -m "Updated based on feedback"
git push --force-with-lease
```
6.**Merge the PR** (after approval).

| Merge Type | What It Does |
|------------|--------------|
| **Merge Commit** | Default merge (keeps commit history). |
| **Squash and Merge** | Combines all PR commits into **one**. |
| **Rebase and Merge** | Applies commits **on top of the latest main branch**. |
