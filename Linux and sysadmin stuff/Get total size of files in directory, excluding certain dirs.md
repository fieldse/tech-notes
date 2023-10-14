
## Get total size of files under directory, excluding certain directories

Our go-to command on Unix-like systems for getting filesize and disk usage summaries is `du`. 

Standard usage:
```
# Summarize disk space usage of current directory
du -sh .

# or.. 
du -sh some_directory

```


the -sh flags here mean:
-  ` -s`   "summary" - return the size of entire directory, not each individual file or dir
-  `-h`    "human" - return the size results in human-friendly format; eg `203M, instead of a byte number.


On occasion  you'd want to exclude a certain directory/directories from the results.
```
du -sh --exclude node_modules .
```


However, unlike the Linux version of the `du` command, the Mac version doesn't include the `--exclude` flag. Instead we use the `-I` flag

```
# Ignore certain directories / patterns
du -sh -I node_modules
```
