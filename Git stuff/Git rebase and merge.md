### Undo a git rebase
credit https://stackoverflow.com/questions/134882/undoing-a-git-rebase

#### 1. Easy way (If you've just done the rebase)

>   Git rebase saves your starting point to `ORIG_HEAD` so this is usually as simple as:
> 
>```
> git reset --hard ORIG_HEAD
>```
> 
> However, the `reset`, `rebase` and `merge` all save your original `HEAD` pointer into `ORIG_HEAD`so, if you've done any of those commands since the rebase you're trying to undo then you'll have to use the reflog.

#### 2. Harder way (if you've done other `reset`, `rebase`, or `merge` commands)

> Find the head commit of the branch as it was immediately before the rebase started in the [reflog](https://git-scm.com/docs/git-reflog)...

```
git reflog
```

and to reset the current branch to it (with the usual caveats about being absolutely sure before reseting with the `--hard` option).

Suppose the old commit was `HEAD@{2}` in the ref log:

```
git reset --hard HEAD@{2}
```

_In Windows, you may need to quote the reference:_

```
git reset --hard "HEAD@{2}"
```

You can check the history of the candidate old head by just doing a `git log HEAD@{2}`(_Windows:_ `git log "HEAD@{2}"`).

If you've not disabled per branch reflogs you should be able to simply do ` git reflog branchname@{1}` as a rebase detaches the branch head before reattaching to the final head

----

