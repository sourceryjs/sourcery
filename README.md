# SourceryJS

*Package resolution and metadata guidelines for browser JS.*

This project is aimed at **package authors** and **package management tools**.


## Sources

SourceryJS aims to define a common plugin system for package managers to talk
to multiple package sources. This allows the user to define their package
repositories in order of preference and be able to fetch dependencies from GitHub,
private [Jam](http://github.com/caolan/jam) repositories, or other systems.


## Package.json (extended)

Since `package.json` is also used by [NPM](http://npmjs.org), we are defining
browser-specific properties under the `browser` namespace to be used by
browser-focused package management tools.

```json
{
    "browser": {
        "url": "http://example.com/path/to/lib.js",
        "main": "./path/to/lib.js",
        "include": [
            "browser/*",
            "README"
        ]
    }
}
```
