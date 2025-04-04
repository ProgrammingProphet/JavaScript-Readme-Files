Great question! In **CommonJS (CJS)** — which is the older module system used by Node.js — things work **a bit differently** than in ES Modules.

Let’s break it down: 🧠

---

## 📌 CommonJS Export/Import Syntax

CommonJS uses:

- `module.exports` – for exporting (default and named)
- `require()` – for importing

---

## ✅ Default Export in CommonJS

### 📁 `math.js`
```js
function multiply(a, b) {
  return a * b;
}

module.exports = multiply; // default export
```

### 📁 `app.js`
```js
const multiply = require('./math');

console.log(multiply(3, 4)); // 12
```

✅ Works like a default export.

---

## ✅ Named Exports in CommonJS

### 📁 `math.js`
```js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

// Named exports
module.exports = {
  add,
  subtract
};
```

### 📁 `app.js`
```js
const math = require('./math');

console.log(math.add(10, 5));      // 15
console.log(math.subtract(10, 5)); // 5
```

---

## ❓ Can We Do Named and Default Export Together in CommonJS?

Yes, but it’s **not as clean as ES Modules**. Here's a workaround:

### 📁 `math.js`
```js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

function multiply(a, b) {
  return a * b;
}

// Trick: Attach default and named exports to one object
module.exports = {
  add,
  subtract,
  default: multiply
};
```

### 📁 `app.js`
```js
const math = require('./math');

console.log(math.default(3, 2));   // multiply: 6
console.log(math.add(3, 2));       // add: 5
console.log(math.subtract(3, 2));  // subtract: 1
```

> 😅 You have to access the "default" using `math.default`, which is not ideal.

---

## ✅ Cleaner Alternative in CommonJS

If you really want **default + named**, do this instead:

### 📁 `math.js`
```js
function multiply(a, b) {
  return a * b;
}

function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

// Export default and attach named ones manually
multiply.add = add;
multiply.subtract = subtract;

module.exports = multiply;
```

### 📁 `app.js`
```js
const multiply = require('./math');

console.log(multiply(2, 3));           // 6 (default)
console.log(multiply.add(2, 3));       // 5 (named)
console.log(multiply.subtract(5, 2));  // 3 (named)
```

✅ Feels like both default and named in one import.

---

## 🔚 Summary

| Feature              | CommonJS                      | ES Modules (ESM)                |
|----------------------|-------------------------------|---------------------------------|
| Default Export        | `module.exports = func`        | `export default func`           |
| Named Export          | `module.exports = { func1 }`   | `export { func1 }`              |
| Import Default        | `const func = require(...)`    | `import func from '...'`        |
| Import Named          | `const obj = require(...)`     | `import { func1 } from '...'`   |

---

Would you like me to convert any of these examples into ES Modules or zip the files for testing locally?