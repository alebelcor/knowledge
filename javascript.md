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
