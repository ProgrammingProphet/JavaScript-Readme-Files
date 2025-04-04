
---

## ✅ Scenario: You have a file called `mathUtils.js`

### 📁 `mathUtils.js`
```js
// Named exports
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}

// Default export
export default function multiply(a, b) {
  return a * b;
}
```

---

## ✅ Now, let's import this in another file `app.js`

### 📁 `app.js`
```js
// Import default + named together
import multiply, { add, subtract } from './mathUtils.js';

console.log("Add:", add(10, 5));         // Output: 15
console.log("Subtract:", subtract(10, 5)); // Output: 5
console.log("Multiply:", multiply(10, 5)); // Output: 50
```

> 🔥 `multiply` is the **default export**, and `{ add, subtract }` are **named exports**.

---

## ✅ Another Example: Rename while importing

```js
import product, { add as addition, subtract as subtraction } from './mathUtils.js';

console.log("Addition:", addition(3, 2));     // 5
console.log("Subtraction:", subtraction(3, 2)); // 1
console.log("Product:", product(3, 2));         // 6
```

> 🧠 You can rename both default and named imports!

---

## 🧪 Quick Summary

| Concept            | Syntax Example                             |
|--------------------|---------------------------------------------|
| Named Export        | `export function add() {}`                 |
| Default Export      | `export default function multiply() {}`    |
| Import Named        | `import { add } from './file.js'`         |
| Import Default      | `import multiply from './file.js'`        |
| Import Both         | `import multiply, { add } from './file.js'` |
| Rename on Import    | `import { add as addition }`              |

---

Want me to generate both files (`mathUtils.js` and `app.js`) as downloadable files or zip? Or want to try a browser-based version with modules?