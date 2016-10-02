# bash-glob [![NPM version](https://img.shields.io/npm/v/bash-glob.svg?style=flat)](https://www.npmjs.com/package/bash-glob) [![NPM downloads](https://img.shields.io/npm/dm/bash-glob.svg?style=flat)](https://npmjs.org/package/bash-glob) [![Build Status](https://img.shields.io/travis/jonschlinkert/bash-glob.svg?style=flat)](https://travis-ci.org/jonschlinkert/bash-glob)

> Bash-powered globbing for node.js

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save bash-glob
```

## Why?

The initial motivation was to use this for generating the `expected` values for comparisons in tests. But as it turns out, this is faster than node-glob in most cases I've tested.

Moreover, this supports the majority of the feature-functionaly in node-glob, and it's more Base-compliant since, well, it **is** Bash.

**Edge cases**

Inevitably there will be edge cases. Thus far, however, I've found that many of the edge cases that seem to be problematic are already addressed or not problematic for Bash.

Please feel free to create an issue if you find a bug or have a feature request.

## Usage

```js
var glob = require('bash-glob');
glob(pattern[, options]);
```

## API

### [glob](index.js#L33)

Asynchronously returns an array of files that match the given pattern or patterns.

**Example**

```js
var glob = require('bash-glob');
glob('*.js', function(err, files) {
  if (err) return console.log(err);
  console.log(files);
});
```

**Params**

* `patterns` **{String|Array}**: One or more glob patterns to use for matching.
* `options` **{Object}**: Options to pass to bash. See available [options](#options).
* `cb` **{Function}**: Callback function, with `err` and `files` array.

### [.each](index.js#L97)

Asynchronously glob an array of files that match any of the given `patterns`.

**Example**

```js
var glob = require('bash-glob');
glob.each(['*.js', '*.md'], {dot: true}, function(err, files) {
  if (err) return console.log(err);
  console.log(files);
});
```

**Params**

* `patterns` **{String}**: One or more glob patterns to use for matching.
* `options` **{Object}**: Options to pass to bash. See available [options](#options).
* `cb` **{Function}**: Callback function, with `err` and `files` array.

### [.sync](index.js#L153)

Returns an array of files that match the given patterns or patterns.

**Example**

```js
var glob = require('bash-glob');
console.log(glob.sync('*.js', {cwd: 'foo'}));
console.log(glob.sync(['*.js'], {cwd: 'bar'}));
```

**Params**

* `patterns` **{String}**: One or more glob patterns to use for matching.
* `options` **{Object}**: Options to pass to bash. See available [options](#options).
* `returns` **{Array}**: Returns an array of files.

## Options

The following options may be used with the main `glob` function or any other method:

* `dotglob`: (or `dot`, for [node-glob](https://github.com/Crafity/node-glob) compatibility) Includes filenames beginning with a `.` (dot) in the results of pathname expansion.
* `extglob`: Enable extended [pattern matching](http://wiki.bash-hackers.org/syntax/pattern) features.
* `failglob`: If set, patterns that fail to match filenames during pathname expansion result in an error message.
* `globstar`: Enable recursive globbing with `**`.
* `nocaseglob`: (or `nocase`, for [node-glob](https://github.com/Crafity/node-glob) compatibility) Enable case-insensitive matching in filenames when performing pathname expansion.
* `nullglob`: If set, Bash allows patterns which match no files to expand to a null string, rather than themselves.

## About

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

Please read the [contributing guide](.github/contributing.md) for avice on opening issues, pull requests, and coding standards.

### Building docs

_(This document was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme) (a [verb](https://github.com/verbose/verb) generator), please don't edit the readme directly. Any changes to the readme must be made in [.verb.md](.verb.md).)_

To generate the readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install -g verb verb-generate-readme && verb
```

### Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

### License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/jonschlinkert/bash-glob/blob/master/LICENSE).

***

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.1.31, on October 01, 2016._