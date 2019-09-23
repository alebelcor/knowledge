# JavaScript

Map and filter an array at the same time, using `reduce()`:

```javascript
const foo = [1, 2, 3, 4, 5, 6];
const bar = foo.reduce((accumulator, current) => {
  if (current % 2 === 0) {
    accumulator.push(current * 2);
  }

  return accumulator;
}, []);

bar; // [4, 8, 12]
```

Get a random number in a range (inclusive):

```javascript
Math.floor(Math.random() * 10) + 1 // random number between 1 and 10
```

## ES5

* [Getter accessors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get)
* [Setter accessors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set)
* [Trailing commas in object literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)
* [Trailing commas in array literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)
* [Reserved word property names](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Reserved_word_usage)
* [Object.create](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
* [`Object.defineProperty()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)
* [`Object.defineProperties()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperties)
* [`Object.freeze()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)
* [`Object.getOwnPropertyDescriptor()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptor)
* [`Object.getOwnPropertyNames()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyNames)
* [`Object.getPrototypeOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf)
* [`Object.isExtensible()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isExtensible)
* [`Object.isFrozen()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isFrozen)
* [`Object.isSealed()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isSealed)
* [`Object.keys()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
* [`Object.preventExtensions()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/preventExtensions)
* [`Object.seal()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)
* [`Array.isArray()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)
* [`Array.prototype.every()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
* [`Array.prototype.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
* [`Array.prototype.forEach()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
* [`Array.prototype.indexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
* [`Array.prototype.lastIndexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)
* [`Array.prototype.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
* [`Array.prototype.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
* [`Array.prototype.reduceRight()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight)
* [`Array.prototype.some()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
* [`Array.prototype.sort`: `compareFunction` must be function or `undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#Description)
* [`Array.prototype.sort`: `compareFunction` may be explicit `undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#Description)
* [Property accessor of strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Character_access)
* [`String.prototype.trim()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/Trim)
* [`Date.now()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/now)
* [`Date.prototype.toISOString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString)
* [`Date.prototype.toJSON()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toJSON)
* [`Function.prototype.bind()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
* [`JSON.parse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)
* [`JSON.stringify()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
* [Immutable `undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined#Description)
* [Immutable `NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN#Description)
* [Immutable `Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity#Description)
* [`Function.prototype.apply()` permits array-likes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
* [`parseInt()` ignores leading zeros](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#Octal_interpretations_with_no_radix)
* [Function "prototype` property is non-enumerable](https://kangax.github.io/compat-table/es5/#test-Miscellaneous_Function_prototype_property_is_non-enumerable)
* [Arguments toStringTag is "Arguments"](https://kangax.github.io/compat-table/es5/#test-Miscellaneous_Arguments_toStringTag_is_Arguments)
* [Zero-width chars in identifiers](https://kangax.github.io/compat-table/es5/#test-Miscellaneous_Zero-width_chars_in_identifiers)
* [Unreserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Future_reserved_keywords_in_older_standards)
* [Enumerable properties can be shadowed by non-enumerables](https://kangax.github.io/compat-table/es5/#test-Miscellaneous_Enumerable_properties_can_be_shadowed_by_non-enumerables)
* [Thrown functions have proper `this` values](https://kangax.github.io/compat-table/es5/#test-Miscellaneous_Thrown_functions_have_proper_this_values)
* [Strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)

## ES2015

## Links

* [ECMAScript compatibility table](https://kangax.github.io/compat-table/)
* [Mozilla Developer Network Web Docs](https://developer.mozilla.org/)
