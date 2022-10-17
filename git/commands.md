This is a list of Git commands I have found useful.

- - -

Show the full history of a file, even if it has been deleted:
```sh
git log --full-history --oneline -- <path/to/file>
```

Show the affected files of a given commit:
```
git show --pretty="" --name-status <hash>
```

Show the name of the current branch:
```
git rev-parse --abbrev-ref HEAD
```
