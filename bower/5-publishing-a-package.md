# Publishing a package

## Creating a bower package and publishing it

Step 1: Create a package with a `bower.json`. Make it into a `git` repository. 
Step 2: Publish it to Github then tag your initial commit with a version number, preferably the version you are using in `bower.json`.

```bash
git tag <version>
git push --tags
```

Step 3: Register your package with bower

```bash
bower register <package-name> <github-url>
```

## Creating a new version

1. Commit your new changes
2. Update the package version in `bower.json`
3. Commit the new changes
4. Tag it with `git tag <version>`
5. Execute `git push --tags`

## Updating all packages with the new version

```bash
bower update
```