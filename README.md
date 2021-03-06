# bash-glob [![NPM version](https://img.shields.io/npm/v/bash-glob.svg?style=flat)](https://www.npmjs.com/package/bash-glob) [![NPM monthly downloads](https://img.shields.io/npm/dm/bash-glob.svg?style=flat)](https://npmjs.org/package/bash-glob)  [![NPM total downloads](https://img.shields.io/npm/dt/bash-glob.svg?style=flat)](https://npmjs.org/package/bash-glob) [![Linux Build Status](https://img.shields.io/travis/micromatch/bash-glob.svg?style=flat&label=Travis)](https://travis-ci.org/micromatch/bash-glob)

> Bash-powered globbing for node.js

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save bash-glob
```

Install with [yarn](https://yarnpkg.com):

```sh
$ yarn add bash-glob
```

**Install bash 4.3 or later**

I recommend using [homebrew](https://github.com/Homebrew/homebrew-core) to install/upgrade bash:

```sh
$ brew upgrade bash
```

## Why?

The initial motivation was to use this for generating the `expected` values for comparisons in tests. But as it turns out, this is faster than node-glob in most cases I've tested.

Moreover, this supports the majority of the feature-functionaly in node-glob, and it's more Bash-compliant since, well, it **is** Bash.

**Edge cases**

Inevitably there will be edge cases. Thus far, however, I've found that many of the edge cases that seem to be problematic are already addressed or not problematic for Bash.

Please feel free to [create an issue](../../issues) if you find a bug or have a feature request.

## Usage

```js
var glob = require('bash-glob');
glob(pattern[, options]);
```

## API

<details>
<summary><strong>glob</strong></summary>

### [glob](index.js#L32)

Asynchronously returns an array of files that match the given pattern or patterns.

**Params**

* `patterns` **{String|Array}**: One or more glob patterns to use for matching.
* `options` **{Object}**: Options to pass to bash. See available [options](#options).
* `cb` **{Function}**: Callback function, with `err` and `files` array.

**Example**

```js
var glob = require('bash-glob');
glob('*.js', function(err, files) {
  if (err) return console.log(err);
  console.log(files);
});
```

</details>

<details>
<summary><strong>.each</strong></summary>

### [.each](index.js#L100)

Asynchronously glob an array of files that match any of the given `patterns`.

**Params**

* `patterns` **{String}**: One or more glob patterns to use for matching.
* `options` **{Object}**: Options to pass to bash. See available [options](#options).
* `cb` **{Function}**: Callback function, with `err` and `files` array.

**Example**

```js
var glob = require('bash-glob');
glob.each(['*.js', '*.md'], {dot: true}, function(err, files) {
  if (err) return console.log(err);
  console.log(files);
});
```

</details>

<details>
<summary><strong>.sync</strong></summary>

### [.sync](index.js#L156)

Returns an array of files that match the given patterns or patterns.

**Params**

* `patterns` **{String}**: One or more glob patterns to use for matching.
* `options` **{Object}**: Options to pass to bash. See available [options](#options).
* `returns` **{Array}**: Returns an array of files.

**Example**

```js
var glob = require('bash-glob');
console.log(glob.sync('*.js', {cwd: 'foo'}));
console.log(glob.sync(['*.js'], {cwd: 'bar'}));
```

</details>

## Options

The following options may be used with the main `glob` function or any other method:

* `dotglob`: (or `dot`, for [node-glob](https://github.com/Crafity/node-glob) compatibility) Includes filenames beginning with a `.` (dot) in the results of pathname expansion.
* `extglob`: Enable extended [pattern matching](http://wiki.bash-hackers.org/syntax/pattern) features.
* `failglob`: If set, patterns that fail to match filenames during pathname expansion result in an error message.
* `globstar`: Enable recursive globbing with `**`.
* `nocaseglob`: (or `nocase`, for [node-glob](https://github.com/Crafity/node-glob) compatibility) Enable case-insensitive matching in filenames when performing pathname expansion.
* `nullglob`: If set, Bash allows patterns which match no files to expand to a null string, rather than themselves.

## About

### Related projects

* [bash-match](https://www.npmjs.com/package/bash-match): Match strings using bash. Does not work on windows, and does not read from the… [more](https://github.com/jonschlinkert/bash-match) | [homepage](https://github.com/jonschlinkert/bash-match "Match strings using bash. Does not work on windows, and does not read from the file system. This library requires that Bash 4.3 or higher is installed and is mostly used for checking parity in unit tests.")
* [braces](https://www.npmjs.com/package/braces): Fast, comprehensive, bash-like brace expansion implemented in JavaScript. Complete support for the Bash 4.3 braces… [more](https://github.com/micromatch/braces) | [homepage](https://github.com/micromatch/braces "Fast, comprehensive, bash-like brace expansion implemented in JavaScript. Complete support for the Bash 4.3 braces specification, without sacrificing speed.")
* [micromatch](https://www.npmjs.com/package/micromatch): Glob matching for javascript/node.js. A drop-in replacement and faster alternative to minimatch and multimatch. | [homepage](https://github.com/jonschlinkert/micromatch "Glob matching for javascript/node.js. A drop-in replacement and faster alternative to minimatch and multimatch.")
* [nanomatch](https://www.npmjs.com/package/nanomatch): Fast, minimal glob matcher for node.js. Similar to micromatch, minimatch and multimatch, but complete Bash… [more](https://github.com/jonschlinkert/nanomatch) | [homepage](https://github.com/jonschlinkert/nanomatch "Fast, minimal glob matcher for node.js. Similar to micromatch, minimatch and multimatch, but complete Bash 4.3 wildcard support only (no support for exglobs, posix brackets or braces)")

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

Please read the [contributing guide](.github/contributing.md) for advice on opening issues, pull requests, and coding standards.

### Building docs

_(This project's readme.md is generated by [verb](https://github.com/verbose/verb-generate-readme), please don't edit the readme directly. Any changes to the readme must be made in the [.verb.md](.verb.md) readme template.)_

To generate the readme, run the following command:

```sh
$ npm install -g verbose/verb#dev verb-generate-readme && verb
```

### Running tests

Running and reviewing unit tests is a great way to get familiarized with a library and its API. You can install dependencies and run tests with the following command:

```sh
$ npm install && npm test
```

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](https://twitter.com/jonschlinkert)

### License

Copyright © 2017, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT License](LICENSE).

***

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.6.0, on April 27, 2017._