### [Reset all changes after last commit in git](https://stackoverflow.com/questions/4630312/reset-all-changes-after-last-commit-in-git)
**First, reset any changes**

This will undo any changes you've made to tracked files and restore deleted files:

```
git reset HEAD --hard
```

**Second, remove new files**

This will delete any new files that were added since the last commit:

```
git clean -fd
```

Files that are not tracked due to `.gitignore` are preserved; they will not be removed

_Warning_: using `-x` instead of `-fd` _would_ delete ignored files. You probably don't want to do this.

### Delete a branch
```
git branch -d <branch-name>
```
### Force delete a local branch
```
git branch -D <branch-name>
```
### To push a local branch to git which does not have mapping on github
We need to map the local branch to an upstream branch
```
git push --set-upstream origin <branch-name>
```
