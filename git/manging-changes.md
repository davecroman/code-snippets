# Managing changes

## Staging and unstaging files

### Staging changes

```bash
git add <file>
```

### Unstaging

```bash
git rm --cached <file>
```

## Discarding changes

### Discard changes since last commit

```bash
git reset --hard HEAD
```

Alternatively, you can use `stash` for this:

```bash
git stash
git stash drop
```

### Go to a specific commit and permanently discard all changes made after that commit

```bash
git reset --hard <commit-hash>
```

### Go to a specific commit and move all changes made after that commit into the working directory

```bash
git reset --soft <commit-hash>
```

## Cleaning untracked and ignored files

### Remove all untracked and ignored files

```bash
git clean fd
```

*WARNING:* You cannot undo this action