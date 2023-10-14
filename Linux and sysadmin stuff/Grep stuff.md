

### Grep recursively through a directory

```
grep -inr "some search term" .
```


### Grep recursively, only for specific filetypes

credit: https://www.howtogeek.com/devops/how-to-use-grep-recursively-within-certain-file-extensions/

Assuming you want to search across `.txt, .csv, .json`  files in the current directory:

```
grep -inr --include \*.txt --include \*.csv --include \*.json "some search term" .
```

*(note the dot at the end.)*
