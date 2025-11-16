# Git Cheat Sheet

## Configuration

### Basic Configuration

- Set user name: `git config --global user.name "Your Name"`
- Set user email: `git config --global user.email "your.email@example.com"`
- View config: `git config --list`
- View specific config: `git config <key>`
- Edit config file: `git config --global --edit`

### Caching Credentials

- Generate PAT in GitHub through Developer Settings
- Copy token to secure place
- Configure git credential cache
  - `git config --global credential.helper cache`
  - `git config --global user.name "garretpatten"`
  - `git config --global user.email "garret.patten@proton.me"`
- Pull or push to a private repository
  - Enter username and personal access token
- The credentials should now be cached

### Commit Signing

- Enable commit signing: `git config --global commit.gpgsign true`
- Set signing key: `git config --global user.signingkey <KEY_ID>`
- Set GPG program: `git config --global gpg.program gpg`
- Sign a specific commit: `git commit -S -m "message"`
- Verify signed commit: `git log --show-signature`
- List GPG keys: `gpg --list-secret-keys --keyid-format=long`
- Export public key: `gpg --armor --export <KEY_ID>`

### Useful Aliases

- Create alias: `git config --global alias.<alias> '<command>'`
- Common aliases:
  - `git config --global alias.st status`
  - `git config --global alias.co checkout`
  - `git config --global alias.br branch`
  - `git config --global alias.ci commit`
  - `git config --global alias.unstage 'reset HEAD --'`
  - `git config --global alias.last 'log -1 HEAD'`
  - `git config --global alias.visual '!gitk'`
  - `git config --global alias.lg "log --oneline --decorate --all --graph"`

## Repository Management

### Initialization

- Initialize repository: `git init`
- Clone repository: `git clone <url>`
- Clone with specific branch: `git clone -b <branch> <url>`
- Clone shallow: `git clone --depth 1 <url>`
- Clone with submodules: `git clone --recurse-submodules <url>`

### Status and Information

- Check status: `git status`
- Short status: `git status -s`
- Show changes: `git diff`
- Show staged changes: `git diff --staged` or `git diff --cached`
- Show file changes: `git diff <file>`
- Show commit history: `git log`
- One-line log: `git log --oneline`
- Graph log: `git log --oneline --graph --all`
- Log with stats: `git log --stat`
- Log with patches: `git log -p`
- Log by author: `git log --author="<name>"`
- Log by date: `git log --since="2 weeks ago"`
- Show file history: `git log --follow <file>`
- Show blame: `git blame <file>`
- Show annotation: `git annotate <file>`

## Branching

### Branch Operations

- List branches: `git branch`
- List all branches: `git branch -a`
- List remote branches: `git branch -r`
- Create branch: `git branch <branch_name>`
- Create and switch: `git checkout -b <branch_name>` or `git switch -c <branch_name>`
- Switch branch: `git checkout <branch>` or `git switch <branch>`
- Rename branch: `git branch -m <old_name> <new_name>`
- Delete branch: `git branch -d <branch_name>`
- Force delete: `git branch -D <branch_name>`
- Delete remote branch: `git push origin --delete <branch_name>`
- Set upstream: `git branch --set-upstream-to=origin/<branch> <branch>`
- Track remote: `git checkout --track origin/<branch>`

### Branch Comparison

- Compare branches: `git diff <branch1>..<branch2>`
- Show commits in branch: `git log <branch1>..<branch2>`
- Show commits not in main: `git log main..<branch>`
- Show merge base: `git merge-base <branch1> <branch2>`

## Committing

### Basic Commits

- Stage file: `git add <file>`
- Stage all: `git add .`
- Stage interactively: `git add -p`
- Unstage file: `git reset HEAD <file>`
- Commit: `git commit -m "message"`
- Amend commit: `git commit --amend`
- Amend without changing message: `git commit --amend --no-edit`
- Skip hooks: `git commit --no-verify`

### Advanced Commits

- Commit with sign-off: `git commit -s -m "message"`
- Commit with GPG sign: `git commit -S -m "message"`
- Empty commit: `git commit --allow-empty -m "message"`
- Fixup commit: `git commit --fixup <commit_hash>`
- Squash commit: `git commit --squash <commit_hash>`

## Stashing

- Stash changes: `git stash`
- Stash with message: `git stash save "message"`
- Stash untracked: `git stash -u`
- List stashes: `git stash list`
- Apply stash: `git stash apply`
- Apply specific stash: `git stash apply stash@{n}`
- Pop stash: `git stash pop`
- Drop stash: `git stash drop stash@{n}`
- Clear all stashes: `git stash clear`
- Show stash diff: `git stash show -p stash@{n}`

## Merging and Rebasing

### Merging

- Merge branch: `git merge <branch>`
- Merge with no fast-forward: `git merge --no-ff <branch>`
- Merge squash: `git merge --squash <branch>`
- Abort merge: `git merge --abort`
- Continue merge: `git merge --continue`

### Rebasing

- Rebase branch: `git rebase <branch>`
- Interactive rebase: `git rebase -i <commit_hash>`
- Interactive rebase last N commits: `git rebase -i HEAD~<n>`
- Continue rebase: `git rebase --continue`
- Abort rebase: `git rebase --abort`
- Skip commit: `git rebase --skip`
- Edit rebase: `git rebase --edit-todo`
- Auto-squash: `git rebase -i --autosquash <commit_hash>`

### Cherry-picking

- Cherry-pick commit: `git cherry-pick <commit_hash>`
- Cherry-pick range: `git cherry-pick <start>..<end>`
- Cherry-pick without commit: `git cherry-pick -n <commit_hash>`
- Continue cherry-pick: `git cherry-pick --continue`
- Abort cherry-pick: `git cherry-pick --abort`

## Remote Operations

### Remote Management

- List remotes: `git remote`
- Show remote URLs: `git remote -v`
- Add remote: `git remote add <name> <url>`
- Remove remote: `git remote remove <name>`
- Rename remote: `git remote rename <old> <new>`
- Show remote info: `git remote show <name>`
- Update remote URL: `git remote set-url <name> <new_url>`

### Fetching and Pulling

- Fetch remote: `git fetch <remote>`
- Fetch all remotes: `git fetch --all`
- Fetch with tags: `git fetch --tags`
- Pull: `git pull`
- Pull with rebase: `git pull --rebase`
- Pull specific branch: `git pull <remote> <branch>`

### Pushing

- Push: `git push`
- Push to remote: `git push <remote> <branch>`
- Push with upstream: `git push -u <remote> <branch>`
- Force push: `git push --force` (use with caution)
- Force push with lease: `git push --force-with-lease` (safer)
- Push all branches: `git push --all`
- Push tags: `git push --tags`
- Push specific tag: `git push <remote> <tag>`
- Delete remote branch: `git push <remote> --delete <branch>`

## Tagging

- List tags: `git tag`
- Create tag: `git tag <tag_name>`
- Create annotated tag: `git tag -a <tag_name> -m "message"`
- Tag specific commit: `git tag <tag_name> <commit_hash>`
- Delete tag: `git tag -d <tag_name>`
- Delete remote tag: `git push <remote> --delete <tag_name>`
- Show tag info: `git show <tag_name>`
- Checkout tag: `git checkout <tag_name>`

## Undoing Changes

### Reset

- Soft reset: `git reset --soft <commit_hash>`
- Mixed reset (default): `git reset <commit_hash>`
- Hard reset: `git reset --hard <commit_hash>` (destructive)
- Reset to HEAD: `git reset HEAD`
- Reset file: `git checkout -- <file>` or `git restore <file>`

### Revert

- Revert commit: `git revert <commit_hash>`
- Revert without commit: `git revert -n <commit_hash>`
- Revert merge: `git revert -m 1 <merge_commit_hash>`

### Clean

- Show what would be cleaned: `git clean -n`
- Clean untracked files: `git clean -f`
- Clean untracked directories: `git clean -fd`
- Clean with interactive: `git clean -i`

## Advanced Operations

### Submodules

- Add submodule: `git submodule add <url> <path>`
- Initialize submodules: `git submodule init`
- Update submodules: `git submodule update`
- Update recursively: `git submodule update --recursive`
- Clone with submodules: `git clone --recurse-submodules <url>`
- Sync submodules: `git submodule sync`

### Worktree

- Add worktree: `git worktree add <path> <branch>`
- List worktrees: `git worktree list`
- Remove worktree: `git worktree remove <path>`
- Prune worktrees: `git worktree prune`

## Useful Tips

- Use `git reflog` to recover lost commits
- Use `--force-with-lease` instead of `--force` for safer pushes
- Use `git add -p` for interactive staging
- Use `git rebase -i` to clean up commit history
- Use `git bisect` to find when a bug was introduced
- Use `git worktree` to work on multiple branches simultaneously
- Use `git stash` to temporarily save uncommitted changes
- Use `git cherry-pick` to apply specific commits
- Use `git log --grep` to search commit messages
- Use `git log -S <string>` to find commits that changed a string
- Use `git blame` to see who last modified each line
- Use `git diff --check` to check for whitespace errors
- Use `git config --global core.autocrlf true` on Windows
- Use `git config --global init.defaultBranch main` to set default branch
