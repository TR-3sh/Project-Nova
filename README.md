# Project Nova

A hands-on Git and GitHub activity.

## What this repo is for

In the scenario, I'm a junior DevOps engineer at *TechNova Solutions* who has to set up the repo, handle feature branches, and clean up a bunch of version control disasters. This repo is where I did all of that, so the commit history and network graph show what I actually ran.

## What I did

**Part 1: Core repository management**
- Initialized the repo, made the first commit (`auth-service.js`), and pushed `main` to GitHub.
- Created `feature/payment-gateway`, worked on it, and pushed it with upstream tracking.
- Simulated a teammate changing `config.js` on `main` through the GitHub website, pulled it, resolved the merge conflict by hand, and merged the feature back into `main`.

**Part 2: Troubleshooting and emergency fixes**
- Scenarios 2, 7, and 10 (amend, revert, remote branch deletion) were done in this repo, so they show up in the history.
- The other scenarios were destructive (hard resets, force-deleting branches, detached HEAD), so I practiced them in a separate throwaway sandbox repo to keep this one clean.

## Part 1: Core repository management

| # | Task | Command |
|---|---|---|
| 1 | Initialization | `git init` |
| 2 | Staging | `git add auth-service.js` |
| 3 | Committing | `git commit -m "Added initial auth service logic."` |
| 4 | Branching | `git branch feature/payment-gateway` |
| 5 | Navigation | `git checkout feature/payment-gateway` |
| 6 | Publishing | `git push --set-upstream origin feature/payment-gateway` |
| 7 | Syncing | `git pull origin main` |
| 8 | Conflict check | `git status` |
| 9 | Resolution | `git commit -m "Merged main into feature/payment-gateway and resolved config.js conflict"` |

### Supporting commands

| Purpose | Command |
|---|---|
| Name the default branch `main` | `git branch -M main` |
| Connect the local repo to GitHub | `git remote add origin https://github.com/TR-3sh/Project-Nova.git` |
| Push `main` for the first time | `git push -u origin main` |
| Push the resolved feature branch | `git push` |
| Return to `main` and sync | `git checkout main`<br>`git pull origin main` |
| Merge the feature into `main` | `git merge --no-ff feature/payment-gateway -m "Merged feature/payment-gateway into main"` |
| Push the merged `main` | `git push origin main` |

The "teammate" commit (`Added base application configuration`) was made through GitHub's **Add file → Create new file** page, to simulate a collaborator merging first.

## Part 2: Troubleshooting and emergency fixes

| # | Problem | Command |
|---|---|---|
| 1 | Oops, wrong file | `git restore --staged .env` |
| 2 | Typo in the message | `git commit --amend -m "Added authentication token validation"` |
| 3 | Forgot a file | `git add styles.css`<br>`git commit --amend --no-edit` |
| 4 | I hate these changes | `git restore index.html` |
| 5 | Wrong branch | `git branch new-feature`<br>`git reset HEAD~3 --hard`<br>`git checkout new-feature` |
| 6 | Detached HEAD | `git switch -c recovery-branch` |
| 7 | Undo a pushed mistake | `git revert a550d04 --no-edit` |
| 8 | Accidental deletion | `git reflog`<br>`git branch feature-x 32170b9` |
| 9 | Ghost files | `git add -u` |
| 10 | Pushed to the void | `git push origin --delete testing-junk` |

**Notes**
- Scenarios 2, 7, and 10 were run in this repo. The rest were run in a separate sandbox repo (`nova-sandbox`).
- The hashes in 7 and 8 come from my own history. The general forms are `git revert <buggy-commit-hash>` and `git branch <deleted-branch-name> <commit-hash>`.
- For 8, I first deleted the branch with `git branch -D feature-x`, because `-d` refuses to delete unmerged work.
- For 10, I created the branch with `git branch testing-junk` and pushed it with `git push origin testing-junk` before deleting it from the remote. I then ran `git branch -d testing-junk` to remove the local copy.

## How to view the history

- Terminal: `git log --oneline --graph --all --decorate`
- GitHub: **Insights → Network**
- Browser extension: **Le Git**

## Collaborators

My instructor, **madzamador**, has been invited as a collaborator to review the network graph.

## Author

Trishia Anne M. Maralit | BSIS - 3C | TUP Manila