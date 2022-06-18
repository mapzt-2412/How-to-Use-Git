- [1. Introduction](#1-introduction)
- [2. Working tree, repository,](#2-working-tree-repository)
- [3. Index definition](#3-index-definition)
- [4. Git tree, Branches](#4-git-tree-branches)
- [5. Add, Commit, Merge, Stash](#5-add-commit-merge-stash)
- [6. Fetch, pull, push](#6-fetch-pull-push)
- [7. Pull/merge request](#7-pullmerge-request)
- [8. Conflict resolve when merge](#8-conflict-resolve-when-merge)
- [9. Conflict resolve when pull](#9-conflict-resolve-when-pull)
- [10. Revert, Reset](#10-revert-reset)
- [11. Gitlab, Github](#11-gitlab-github)
- [12. Other VSC tool](#12-other-vsc-tool)
- [13. Conventional commits](#13-conventional-commits)
- [14. Branching models](#14-branching-models)
- [15. Submodule](#15-submodule)
- [16. Git tool, extension](#16-git-tool-extension)
# 1. Introduction
# 2. Working tree, repository,
# 3. Index definition
# 4. Git tree, Branches
# 5. Add, Commit, Merge, Stash
# 6. Fetch, pull, push
## 6.1 Fetch
+ Downloads all the latest commits from all branches and also all the new branches from the remote and saves it in the local repo
+ But it will not merge it to the local branch that are active
+ It is useful to review changes in the remote repo before pulling
 ## 6.2 Pull
 + Updates your current local working branch, and all of the remote tracking branches.
 + However, will merge all changes into local working directory (might create merge conflict)
 ## 6.3 Push
 + Updates the remote branch with local commits
 + By default, git push only updates the corresponding branch on the remote.
 + It is good practice to fetch or pull before pushing to avoid conflict
 > Common push options
 + git push -u <remote_name> [branch] : Useful when pushing a new branch, this creates an upstream tracking branch with a lasting relationship to your local branch

 + git push --all: push all branches

 + git push <remote_name> --delete <branch_name>  
  => can be used to delete a remote branch
 


# 7. Pull/merge request
# 8. Conflict resolve when merge
# 9. Conflict resolve when pull
# 10. Revert, Reset
# 11. Gitlab, Github
# 12. Other VSC tool
|                           Git                           |          Concurrent version system (CVS)          |
|:-------------------------------------------------------:|:-------------------------------------------------:|
| Distributed vsc                                         | Centralized vsc                                   |
| Operations are atomic                                   | Operations are not atomic                         |
| Changes are per project                                 | Changes are per file                              |
| Have index (staging area)                               | Do not have index                                 |
| The repository are committed into the local repository. | The repository are committed into central server. |
# 13. Conventional commits
# 14. Branching models
# 15. Submodule
# 16. Git tool, extension