
## Initialize go module

```
go mod init somerepo/mymodule
```

## Install dependencies and clean up go module

Install all package dependencies, clean up unused dependencies, and tidy up the go.mod file

```
go mod tidy
```

## Build go module
```
go mod build
```

## Install all dependencies for current package

If you have imports in your current package which aren't yet installed, you can install everything for the current package directory:

```
 go get .
```


## Add package to go module

To import / add a dependency to your project:

```
go get example.com/somemodule
```

## Show all available package updates

```
go list -m -u all
```

## Show all available updates for a specific package

```
go list -m -u example.com/somepackage
```