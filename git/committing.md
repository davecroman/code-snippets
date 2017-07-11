# Committing

## Committing file permission changes

### Option 1: Using a global config to index filemode changes

```
git config core.filemode true
```

### Option 2: Manually adding filemode changes into the file

Example:

```
git update-index --chmod=+x filename.sh
```