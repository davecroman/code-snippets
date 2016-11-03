# Bower.json

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
