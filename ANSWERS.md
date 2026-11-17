# TP5 Git and GitHub - Answers

## Exercise 1
1. `--global` applies the setting to every repository of the current user. It is stored in the user file `~/.gitconfig` (on Windows: `C:\Users\<user>\.gitconfig`).
2. No. Git works entirely locally: commits are stored in the `.git` folder. GitHub is only a remote hosting service used to publish and share.

## Exercise 2
1. They are untracked because Git has not been told to follow them yet: they are in no commit and not in the staging area.
2. `.env` ignores the file with secrets and environment variables. `*.log` ignores log files. `__pycache__/` ignores Python compiled cache. `.DS_Store` ignores macOS folder metadata.

## Exercise 3
1. Working tree: the files on disk that I edit. Staging area: the snapshot of what the next commit will contain. Repository: the full history of commits stored in `.git`.
2. Staging lets me choose which changes go in, so each commit stays focused on one logical change.
3. Good: `Add registration form`. Bad: `update` or `fix stuff`.

## Exercise 4
1. It was a three-way merge. The history graph shows a merge commit with two parents, because `main` and the feature branch had diverged.
2. Without the commit on `main`, Git would have done a fast-forward: it just moves the `main` pointer, with no merge commit and a linear history.
3. The work is already in `main`, so deleting the branch loses nothing and keeps the repository clean. `git branch -d` refuses if the branch is not merged.

## Exercise 5
| Scenario | Command |
|---|---|
| A | `git restore index.html` |
| B | `git restore --staged README.md` |
| C | `git revert HEAD` |
| D | `git reset --mixed HEAD~1` |
| E | `git stash push -m "wip"` then later `git stash pop` |

1. `git revert` creates a new commit that cancels an earlier one. `git reset` moves the branch pointer back and rewrites history. `revert` is safe on a shared branch because it does not change commits others already have.
2. `--soft` moves HEAD only: changes stay staged. `--mixed` moves HEAD and clears the staging area: changes stay in the working tree. `--hard` also discards the changes in the working tree.

## Exercise 6
1. `commit` saves a snapshot in the local repository. `push` uploads local commits to the remote repository on GitHub.
2. GitHub CLI (`gh auth login`, HTTPS, browser login). The token is stored in the Windows keyring. A token must never appear in a command or file because it can leak through shell history, commits or screenshots, and anyone who has it can act as me.
3. No. The password stays in the history. I must revoke or change the password immediately, then remove it from the history (for example with `git filter-repo` or BFG) and force-push, and treat it as compromised.

## Exercise 7
1. To keep `main` stable: no direct pushes, every change is reviewed, and the history cannot be overwritten.
2. Correctness of the logic, readability and style, tests or CI passing, no secrets in the code, and a change limited to its purpose.
3. A Pull Request can trigger automatic checks (build, tests) that must pass before merging. That is continuous integration (TP6).

## Exercise 8
1. `<<<<<<<` starts my branch's version, `=======` separates the two versions, `>>>>>>>` ends the other branch's version.
2. Both branches changed the same line differently, and Git cannot know which one is correct.
3. Merge or pull often with short-lived branches, and split the work so people edit different files or areas.

## Exercise 9
1. A branch moves forward with new commits. A tag is a fixed label on one commit, used to mark a release.
2. MAJOR: breaking changes. MINOR: new backward-compatible features. PATCH: backward-compatible bug fixes. A small bug fix increases PATCH.

## Bonus
The `push` event triggered the workflow. The logs are in the Actions tab of the repository, by opening the run and then the job.
