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
Math.floor(Math.random() * (max - min + 1)) + min
Math.floor(Math.random() * (10 - 2 + 1)) + 2 // random number between 2 and 10
```

Create a bookmarklet to clear browser storage (i.e. session storage and local storage):

```txt
javascript:(function(){sessionStorage.clear();localStorage.clear()}());
```

Besides `removeEventListener()`, you may use `AbortController#abort()` to remove an event listener:

```javascript
const { abort, signal } = new AbortController();
element.addEventListener('click', handleClick, { signal });

abort(); // removes event listener
```

Timeout fetch requests with `AbortSignal.timeout()`:

```javascript
fetch(url, {
  // ...
  signal: AbortSignal.timeout(5000), // abort after 5 seconds
});
```

Safely parse a number:

```typescript
function parseNumber(input: string) {
  if (input.trim() === '') {
    return;
  }

  const value = Number(input);

  if (!Number.isFinite(value)) {
    return;
  }

  return value;
}
```

Do something when the DOM is ready:

```javascript
window.addEventListener('DOMContentLoaded', (event) => {
  // The HTML document has been completely parsed, and all deferred scripts have downloaded and executed
});
```

Lazy load a script:

```javascript
const script = document.createElement('script');
script.async = true; // or defer
script.src = 'path/to/file.js';
script.onload = () => {} // callback if needed

document.querySelector('head').appendChild(script);
```

Promise wrapper to avoid try/catch:

```javascript
function promiseWrapper(promise) {
  return promise
    .then((data) => [, data])
    .catch((error) => [error]);
}

const [error, data] = await promiseWrapper(doAsyncStuff());
```

## ES5

* [Getter accessors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get)
* [Setter accessors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set)
* [Trailing commas in object literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)
* [Trailing commas in array literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)
* [Reserved word property names](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Reserved_word_usage)
* [`Object.create()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
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

* [Modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules), [`import`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import), and [`export`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) statements
* [Proper tail calls (tail call optimization)](https://kangax.github.io/compat-table/es6/#test-proper_tail_calls_(tail_call_optimisation))
* [Default parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)
* [Rest parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)
* [Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)
* [Shorthand object property/method names and computed properies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#New_notations_in_ECMAScript_2015)
* [`for...of` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)
* [Octal numbers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Numbers_and_dates#Octal_numbers)
* [Binary numbers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Numbers_and_dates#Binary_numbers)
* [Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
* [RegExp `y` and `u` flags](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#Parameters)
* [Destructuring assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
* [Unicode code point escapes](https://kangax.github.io/compat-table/es6/#test-Unicode_code_point_escapes)
* [`new.target`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new.target)
* [`const`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
* [`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
* [Block-level functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions#Block-level_functions)
* [Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
* [`class`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
* [`super`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super)
* [Generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*)
* [Typed arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray)
* [`Map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)
* [`Set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)
* [`WeakMap`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)
* [`WeakSet`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakSet)
* [`Proxy`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
* [`Reflect`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Reflect)
* [`Promise`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [`Symbol`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)
* [`Object.assign()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
* [`Object.getOwnPropertySymbols()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertySymbols)
* [`Object.is()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is)
* [`Object.setPrototypeOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/setPrototypeOf)
* [Function `name` property](https://kangax.github.io/compat-table/es6/#test-function_name_property)
* [`String.fromCodePoint()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint)
* [`String.raw()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/raw)
* [`String.prototype.codePointAt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt)
* [`String.prototype.normalize()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize)
* [`String.prototype.repeat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)
* [`String.prototype.startsWith()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)
* [`String.prototype.startsWith()` throws on `RegExp`](https://kangax.github.io/compat-table/es6/#test-String.prototype_methods_String.prototype.startsWith_throws_on_RegExp)
* [`String.prototype.endsWith()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
* [`String.prototype.endsWith()` throws on `RegExp`](https://kangax.github.io/compat-table/es6/#test-String.prototype_methods_String.prototype.endsWith_throws_on_RegExp)
* [`String.prototype.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
* [`String.prototype[@@iterator]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/@@iterator)
* [`String` iterator prototype chain](https://kangax.github.io/compat-table/es6/#test-String.prototype_methods_String_iterator_prototype_chain)
* [`RegExp.prototype.flags`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/flags)
* [`RegExp.prototype[@@match]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/@@match)
* [`RegExp.prototype[@@replace]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/@@replace)
* [`RegExp.prototype[@@split]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/@@split)
* [`RegExp.prototype[@@search]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/@@search)
* [`get RegExp[@@species]`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/@@species)
* [`Array.from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
* [`Array.of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of)
* [`get Array[@@species]`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@species)
* [`Array.prototype.copyWithin()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)
* [`Array.prototype.find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
* [`Array.prototype.findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
* [`Array.prototype.fill()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
* [`Array.prototype.keys()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/keys)
* [`Array.prototype.values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values)
* [`Array.prototype.entries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)
* [`Array.prototype[@@iterator]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@iterator)
* [`Array.prototype[@@unscopables]`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@unscopables)
* [`Array` iterator prototype chain](https://kangax.github.io/compat-table/es6/#test-Array.prototype_methods_Array_iterator_prototype_chain)
* [`Number.isFinite()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isFinite)
* [`Number.isInteger()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger)
* [`Number.isSafeInteger()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isSafeInteger)
* [`Number.isNaN()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)
* [`Number.parseFloat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/parseFloat)
* [`Number.parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/parseInt)
* [`Number.EPSILON`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/EPSILON)
* [`Number.MIN_SAFE_INTEGER`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MIN_SAFE_INTEGER)
* [`Number.MAX_SAFE_INTEGER`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER)
* [`Math.clz32()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/clz32)
* [`Math.imul()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/imul)
* [`Math.sign()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign)
* [`Math.log10()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/log10)
* [`Math.log2()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/log2)
* [`Math.log1p()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/log1p)
* [`Math.expm1()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/expm1)
* [`Math.cosh()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/cosh)
* [`Math.sinh()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sinh)
* [`Math.tanh()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/tanh)
* [`Math.acosh()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/acosh)
* [`Math.asinh()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/asinh)
* [`Math.atanh()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/atanh)
* [`Math.trunc()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc)
* [`Math.fround()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/fround)
* [`Math.cbrt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/cbrt)
* [`Math.hypot()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/hypot)
* [`Date.prototype[@@toPrimitive]`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/@@toPrimitive)
* [`Array` is subclassable](https://kangax.github.io/compat-table/es6/#test-Array_is_subclassable)
* [`RegExp` is subclassable](https://kangax.github.io/compat-table/es6/#test-RegExp_is_subclassable)
* [`Function` is subclassable](https://kangax.github.io/compat-table/es6/#test-Function_is_subclassable)
* [`Promise` is subclassable](https://kangax.github.io/compat-table/es6/#test-Promise_is_subclassable)
* [`Boolean` is subclassable](https://kangax.github.io/compat-table/es6/#test-miscellaneous_subclassables)
* [`Number` is subclassable](https://kangax.github.io/compat-table/es6/#test-miscellaneous_subclassables)
* [`String` is subclassable](https://kangax.github.io/compat-table/es6/#test-miscellaneous_subclassables)
* [`Error` is subclassable](https://kangax.github.io/compat-table/es6/#test-miscellaneous_subclassables)
* [`Map` is subclassable](https://kangax.github.io/compat-table/es6/#test-miscellaneous_subclassables)
* [`Set` is subclassable](https://kangax.github.io/compat-table/es6/#test-miscellaneous_subclassables)
* [Prototype of bound functions](https://kangax.github.io/compat-table/es6/#test-prototype_of_bound_functions)
* [`Proxy`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
* [`Object` static methods accept primitives](https://kangax.github.io/compat-table/es6/#test-Object_static_methods_accept_primitives)
* [Own property order](https://kangax.github.io/compat-table/es6/#test-own_property_order)
* [Updated identifier syntax](https://kangax.github.io/compat-table/es6/#test-Updated_identifier_syntax)
* [Miscellaneous](https://kangax.github.io/compat-table/es6/#test-miscellaneous)

## ES2016

* [`Array.prototype.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
* [Exponentiation operator (`**`)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Exponentiation)

## ES2017

* [`Object.values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)
* [`Object.entries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
* [`Object.getOwnPropertyDescriptors()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptors)
* [`String.prototype.padStart()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart)
* [`String.prototype.padEnd()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd)
* [Trailing commas in function parameter lists](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)
* [Trailing commas in function argument lists](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas)
* [`async` functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) and [`await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
* [`SharedArrayBuffer`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer)
* [`Atomics`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Atomics)

## ES2018

* [Object rest/spread properties](https://kangax.github.io/compat-table/es2016plus/#test-object_rest/spread_properties)
* [`Promise.prototype.finally()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/finally)
* [`s` (dotAll) flag for regular expressions](https://kangax.github.io/compat-table/es2016plus/#test-s_(dotAll)_flag_for_regular_expressions)
* [`RegExp` named capture groups](https://kangax.github.io/compat-table/es2016plus/#test-RegExp_named_capture_groups)
* [`RegExp` Lookbehind Assertions](https://kangax.github.io/compat-table/es2016plus/#test-RegExp_Lookbehind_Assertions)
* [`RegExp` Unicode Property Escapes](https://kangax.github.io/compat-table/es2016plus/#test-RegExp_Unicode_Property_Escapes)
* [Async generators](https://kangax.github.io/compat-table/es2016plus/#test-Asynchronous_Iterators_async_generators)
* [`for await...of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of)

## ES2019

* [`Object.fromEntries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries)
* [`String.prototype.trimStart()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart)
* [`String.prototype.trimEnd()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd)
* [`Array.prototype.flat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)
* [`Array.prototype.flatMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)
* [Optional `catch` binding](https://kangax.github.io/compat-table/es2016plus/#test-optional_catch_binding)
* [`Symbol.prototype.description`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/description)
* [`Function.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/toString)

## ES2020

* [`import()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#Dynamic_Imports)
* [`BigInt`](https://developer.mozilla.org/en-US/docs/Glossary/BigInt)
* [`Promise.allSettled()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled)
* [`globalThis`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis)
* [Specifying `for...in` enumeration order](https://github.com/tc39/proposal-for-in-order)
* [Optional chaining](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)
* [Nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator)

## Links

* [Mozilla Developer Network Web Docs](https://developer.mozilla.org/)
* [ECMAScript compatibility table](https://kangax.github.io/compat-table/)
* [Finished proposals](https://github.com/tc39/proposals/blob/master/finished-proposals.md)
* [Active proposals](https://github.com/tc39/proposals#active-proposals)
* [The TC39 Process](https://tc39.es/process-document/)
