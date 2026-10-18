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
- The other scenarios were destructive (hard resets, force-deleting branches, detached HEAD), so I practiced them in a separate throwaway sandbox repo to keep this one clean. Every command below is something I actually ran.

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

## Part 2: Troubleshooting and emergency fixes

| # | Problem | Command |
|---|---|---|
| 1 | Oops, wrong file | `git restore --staged .env` |
| 2 | Typo in the message | `git commit --amend -m "Added authentication token validation"` |
| 3 | Forgot a file | `git add styles.css` then `git commit --amend --no-edit` |
| 4 | I hate these changes | `git restore index.html` |
| 5 | Wrong branch | `git branch new-feature`, then `git reset HEAD~3 --hard`, then `git checkout new-feature` |
| 6 | Detached HEAD | `git switch -c recovery-branch` |
| 7 | Undo a pushed mistake | `git revert a550d04 --no-edit` (general form: `git revert <buggy-commit-hash>`) |
| 8 | Accidental deletion | `git reflog` to find the hash, then `git branch feature-x 32170b9` (general form: `git branch <deleted-branch-name> <commit-hash>`) |
| 9 | Ghost files | `git add -u` |
| 10 | Pushed to the void | `git push origin --delete testing-junk` |

## How to view the history

- Terminal: `git log --oneline --graph --all --decorate`
- GitHub: **Insights → Network**, or the "le git" browser extension.

## Collaborators

My instructor, **madzamador**, has been invited as a collaborator to review the network graph.

## Author

Trishia Anne M. Maralit | BSIS - 3C | TUP Manila