# Setting up and installing packages

## Installing `bower`

```bash
npm install bower -g
```


## Installing a package

```bash
bower install <package-name>
```

This will install the latest version of the specified package. If the package has already been installed, this command will replace that package with the latest version.

If you wish to add this package to your project's declared dependencies via `bower.json`, just add the flag `--save`

```bash
bower install <package-name> --save
```

For a dev-only dependecy, use `--save-dev` instead of `--save`

### Installing a specific version

```bash
bower install <package-name>#<version-number>
```

Example: `bower install jquery#1.9.1`

### List all available versions of a package

```bash
bower info <package-name>
```


## Update all packages to the latest version

```bash
bower update
```

## Listing all installed packages

```bash
bower list
```

If package B is represented as a child of package A, that means package A is dependent on package B.

## Searching for a package

```bash
bower search <keyword-to-search>
```

## Uninstalling a package

```bash
bower uninstall <package-name>
```

To remove this package from the declared dependencies in `bower.json`, just add the `--save` flag.