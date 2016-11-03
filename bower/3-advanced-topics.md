# Bower Cache

When installing packages, bower automatically creates a cache copy of that package in the local machine 

## Listing the packages in the cache

```bash
bower cache list
```

## Clearing the cache

```bash
bower cache clean
```

## Force install a package from the cache folder

```bash
bower install <package-name> --o
```

`-o` stands for offline mode

## Prune

`prune` uninstalls all packages present in the current project that are not declared in `bower.json`

```bash
bower prune
```

To preview which packages are going to be uninstalled, simply run `bower list` and check all packages with the `--extraneous` label.