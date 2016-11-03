# Configuring Bower

## `bower.json`

`bower.json` contains all the necessary configurations for a package.

## Creating a `bower.json` file

In the root of the project folder you are working on, type:

```bash
bower init
```

It will generate a `bower.json` file based on the answers you provide in the question prompts.

### Example file

```json
{
  "name": "my-example",
  "description": "An example JSON file",
  "main": [
    "main.js"
  ],
  "dependencies": {
    "packageA": "~1.1.3",
    "packageB": "~4.3.5"
  },
  "devDependencies": {

  },
  "moduleType": [
    "node"
  ],
  "keywords": [
    "bower",
    "example",
    "json"
  ],
  "authors": [
    "Dave Croman <davecromandev@gmail.com>"
  ],
  "license": "MIT",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
  ],
  "private": true
}
```

## Specs

View the specs [here](https://github.com/bower/spec/blob/master/json.md). It provides a good documentation of the parameters that it supports.

## `.bowerrc`

See the documentation for `.bowerrc` [here](https://github.com/bower/spec/blob/master/config.md)

## Installing packages from `bower.json`

```bash
bower install
```

This will install all the packages in the `dependencies` block of your project's `bower.json`

## Adding a package as a dependency to `bower.json`

```bash
bower install <package-name> --save
```

You can also add a package as a dev dependency (e.g., test libraries) using `--save-dev`

```bash
bower install <dev-package-name> --save-dev
```

## Removing a package from `bower.json`

```bash
bower uninstall <package-name-to-remove> --save
```