# Configuring `bower`

## `.bowerrc`

Create a `.bowerrc` file in the root of your project.

Example:
```json
{
  "directory": "app/components/",
  "timeout": 120000,
  "registry": {
    "search": [
      "http://localhost:8000",
      "https://bower.herokuapp.com"
    ]
  }
}
```

### directory

The directory to store the packages downloaded via bower