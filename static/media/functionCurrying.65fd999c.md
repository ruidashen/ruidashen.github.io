```js
const sum = (a, b, c) => {
  return a + b + c;
};

const curry = (fn) => {
  let judge = (...args) => {
    if (args.length === fn.length) return fn(...args);
    return (...arg) => {
      return judge(...args, ...arg);
    };
  };
  return judge;
};

const curriedSum = curry(sum);

console.log(curriedSum(1)(2)(3)); // 6
console.log(curriedSum(1, 2)(3)); // 6
console.log(curriedSum(1)(2, 3)); // 6
```
