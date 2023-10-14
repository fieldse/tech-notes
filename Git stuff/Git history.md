-----

## Git history (git log)

### Find out when a file was created
```
git log --oneline somefile.txt | tail -1
```

### Get commit history for a given file

```
git log -p filename
```
```
```
### Shorter output for git log

```
git log --oneline
```

Result:
```
$ git log --oneline -n5
d5ee2f46 (upstream/main, origin/main, main) Display instant course bundle purchases in billing sections. (#3232)
3e346af5 Increase meeting duration limit to 6 hours. (#3227)
37472844 Don't escape HTML in the sales page "about me" block (#3226)
72e988bb Increase discussions and comments page sizes. (#3223)
efbe4ddb Do not autofocus to the assessment editor on mount. (#3222)
```


### Find most recent common ancestor commit between two branches

from https://stackoverflow.com/questions/1549146/git-find-the-most-recent-common-ancestor-of-two-branches

```
git merge-base branch2 branch3
050dc022f3a65bdc78d97e2b1ac9b595a924c3f2
```
---- 

## Checkout + commit hashes

### Checkout one commit prior to another commit

from https://stackoverflow.com/questions/20455980/how-do-i-git-checkout-one-commit-prior-to-a-specific-commit

**Scenario:**
 You want to checkout the commit prior to another commit with hash `f1962b3cc771184a471e1350fa280d80d5fdd09d` in the commit history:

```
 git checkout f1962b3cc771184a471e1350fa280d80d5fdd09d^
```
 
 Notice the `^` at the end. That means one revision behind.
 
 For example this would be 5 revisions behind:
 
```
 git checkout f1962b3cc771184a471e1350fa280d80d5fdd09d^^^^^
```
 
 ... equivalent to:
 
```
 git checkout f1962b3cc771184a471e1350fa280d80d5fdd09d~5
```
 
 Btw, when you do this, you'll be in a _detached HEAD_ state.
 