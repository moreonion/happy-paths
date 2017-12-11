# Happy Path to Developing JavaScript

## JavaScript libraries

We agreed to a simple set of utility libraries which should be used over
alternatives:

* [`lodash`](https://lodash.com/docs)
* [`object-path`](https://github.com/mariocasciaro/object-path)
  (or maybe
  [`object-path-immutable`](https://github.com/mariocasciaro/object-path-immutable))
* [`qs`](https://www.npmjs.com/package/qs) for parsing query strings

Also, the general rule is:
Try to use plain JavaScript constructs if they do not need any boilerplate,
like:

* `Object.assign({}, obj)` for copying objects, but beware of
  [caveats](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
* `Array.prototype.reduce()` instead of the lodash version
* `Array.prototype.map()`

## Common problems

* simple deep cloning for data only objects/Arrays:
  `obj2 = JSON.parse(JSON.stringify(obj1))` (`null` is OK, but JSON.stringify
  ignores `undefined` and functions)
* use `_.cloneDeep()` for comprehensive deep cloning
* use `_.merge()` for deep merge
* use `_.forOwn()` for iterating over own properties
