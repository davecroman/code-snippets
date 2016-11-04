# Setting up and installing packages

## Installing node

#### Using `brew`

```bash
brew install node
```

## Create a `package.json` file

```
npm init
```

Example `package.json` file from `underscore`:

```json
{
  "name" : "underscore",
  "description" : "JavaScript's functional programming helper library.",
  "homepage" : "http://documentcloud.github.com/underscore/",
  "keywords" : ["util", "functional", "server", "client", "browser"],
  "author" : "Jeremy Ashkenas <jeremy@documentcloud.org>",
  "contributors" : [],
  "dependencies" : [],
  "repository" : {"type": "git", "url": "git://github.com/documentcloud/underscore.git"},
  "main" : "underscore.js",
  "version" : "1.1.6"
}
```

For the documentation of `package.json`, see this [link](https://docs.npmjs.com/files/package.json)

## Installing a package

```bash
npm install <package-name>
```

Note that this downloads the latest available version of the specified package name.

To add it to `package.json`, simply add the `--save` flag

```bash
npm install <package-name> --save
```

If it is just a dev dependency, use `--save-dev`

### Installing a specific version

```bash
npm install <package-name>@<version>
```

## Uninstalling a package

```bash
npm uninstall <package-name>
```

Similar to installing a package, if you wish to remove the package as a dependency from `package.json`, just add the `--save` or `--save-dev` flag.