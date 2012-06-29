# Sourcery

*Package resolution and metadata guidelines for browser JS.*

This project is aimed at **package authors** and **package management tools**.

It is **module definition agnostic**, and can be used with AMD, CommonJS,
ES6 modules, or legacy browser globals. It is also **repository agnostic**,
and aims to accomodate existing and future package archives and sources. By
following these guidelines we hope to promote continued innovation in package
management tools, without creating package silos with every new project.


## Package resolution

SourceryJS aims to define a common plugin system for client package management
tools to talk to multiple package sources. This allows the user to define their
package repositories in order of preference and be able to fetch dependencies
from GitHub, private [Jam](http://github.com/caolan/jam) repositories, or other
systems.


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

#### url

The location of the browser compatible build (if not at the current location).
This allows package authors to direct package managers to their official release
CDN, and can be used to point to .js files or .tar.gz archives.

#### main

The name of the module inside the package that should be used when someone does
a require for "packageName". The default value is "main", so only specify it if
it differs from the default. The value is relative to the package folder.

Often the top-level "main" property is used to point to a Node.js specific module,
this property can be used to point to a browser-specific module if it would
conflict with the top-level property used by NPM.

#### include

An array of globs/paths pointing to resources that should be included in the
browser package. This allows package authors to exclude files related to Node.js
or the build system.
