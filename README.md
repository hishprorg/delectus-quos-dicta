# @hishprorg/delectus-quos-dicta <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Object.groupBy` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.github.io/proposal-array-grouping/).

## Getting started

```sh
npm install --save @hishprorg/delectus-quos-dicta
```

## Usage/Examples

```js
var groupBy = require('@hishprorg/delectus-quos-dicta');
var assert = require('assert');

var arr = [0, 1, 2, 3, 4, 5];
var parity = function (x) { return x % 2 === 0 ? 'even' : 'odd'; };

var results = groupBy(arr, function (x, i) {
    assert.equal(x, arr[i]);
    return parity(x);
});

assert.deepEqual(results, {
    __proto__: null,
    even: [0, 2, 4],
    odd: [1, 3, 5],
});
```

```js
var groupBy = require('@hishprorg/delectus-quos-dicta');
var assert = require('assert');
/* when Object.groupBy is not present */
delete Object.groupBy;
var shimmed = groupBy.shim();

assert.equal(shimmed, groupBy.getPolyfill());
assert.deepEqual(Object.groupBy(arr, parity), groupBy(arr, parity));
```

```js
var groupBy = require('@hishprorg/delectus-quos-dicta');
var assert = require('assert');
/* when Array#group is present */
var shimmed = groupBy.shim();

assert.equal(shimmed, Object.groupBy);
assert.deepEqual(Object.groupBy(arr, parity), groupBy(arr, parity));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hishprorg/delectus-quos-dicta
[npm-version-svg]: https://versionbadg.es/hishprorg/delectus-quos-dicta.svg
[deps-svg]: https://david-dm.org/hishprorg/delectus-quos-dicta.svg
[deps-url]: https://david-dm.org/hishprorg/delectus-quos-dicta
[dev-deps-svg]: https://david-dm.org/hishprorg/delectus-quos-dicta/dev-status.svg
[dev-deps-url]: https://david-dm.org/hishprorg/delectus-quos-dicta#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishprorg/delectus-quos-dicta.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishprorg/delectus-quos-dicta.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishprorg/delectus-quos-dicta.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishprorg/delectus-quos-dicta
[codecov-image]: https://codecov.io/gh/hishprorg/delectus-quos-dicta/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/hishprorg/delectus-quos-dicta/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/hishprorg/delectus-quos-dicta
[actions-url]: https://github.com/hishprorg/delectus-quos-dicta/actions
