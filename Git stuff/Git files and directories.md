
### Check what files exist in a directory in another branch

```
git -p ls-tree -r --name-only somebranch:somedir
```

optional flags: 
- `-r ` recurse through subdirectories 
- `-p. `  page through the results