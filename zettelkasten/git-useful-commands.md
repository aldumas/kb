---
created-at: 2022-11-30 12:04
role: idea
tags: git tool tip
---

Show the full history of a file, even if it has been deleted:
```sh
git log --full-history --oneline -- <path/to/file>
```

Show the affected files of a given commit:
```sh
git show --pretty="" --name-status <hash>
```

Show the name of the current branch:
```sh
git rev-parse --abbrev-ref HEAD
```


