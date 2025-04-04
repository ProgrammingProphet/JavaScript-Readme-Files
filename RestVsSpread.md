In JavaScript, the **spread operator (`...`)** and **rest operator (`...`)** look the same but serve different purposes depending on how they are used.

---

## **1. Spread Operator (`...`)**  
The **spread operator** is used to **expand** elements of an array, object, or iterable into individual elements.

### **Use Cases of Spread Operator**
1. **Expanding Arrays**
   ```javascript
   let numbers = [1, 2, 3];
   let newNumbers = [...numbers, 4, 5]; 
   console.log(newNumbers); // [1, 2, 3, 4, 5]
   ```

2. **Copying Arrays (Shallow Copy)**
   ```javascript
   let arr1 = [10, 20, 30];
   let arr2 = [...arr1]; 
   console.log(arr2); // [10, 20, 30]
   ```

3. **Merging Arrays**
   ```javascript
   let arr1 = [1, 2, 3];
   let arr2 = [4, 5, 6];
   let mergedArr = [...arr1, ...arr2];
   console.log(mergedArr); // [1, 2, 3, 4, 5, 6]
   ```

4. **Spreading in Objects**
   ```javascript
   let obj1 = { a: 1, b: 2 };
   let obj2 = { ...obj1, c: 3 };
   console.log(obj2); // { a: 1, b: 2, c: 3 }
   ```

5. **Passing Elements to a Function**
   ```javascript
   function sum(a, b, c) {
       return a + b + c;
   }
   let nums = [1, 2, 3];
   console.log(sum(...nums)); // 6
   ```

---

## **2. Rest Operator (`...`)**  
The **rest operator** is used to **collect multiple elements into a single variable** inside function parameters.

### **Use Cases of Rest Operator**
1. **Handling Function Parameters**
   ```javascript
   function sum(...numbers) {
       return numbers.reduce((total, num) => total + num, 0);
   }
   console.log(sum(1, 2, 3, 4)); // 10
   ```

2. **Collecting Remaining Arguments**
   ```javascript
   function showDetails(name, ...hobbies) {
       console.log(`${name}'s hobbies:`, hobbies);
   }
   showDetails("Vikram", "Coding", "Music", "Traveling");
   // Output: Vikram's hobbies: [ 'Coding', 'Music', 'Traveling' ]
   ```

3. **Destructuring with Rest Operator**
   ```javascript
   let [first, second, ...rest] = [10, 20, 30, 40, 50];
   console.log(first); // 10
   console.log(second); // 20
   console.log(rest); // [30, 40, 50]
   ```

---

## **Key Differences**
| Feature           | Spread Operator (`...`) | Rest Operator (`...`) |
|------------------|----------------------|---------------------|
| **Purpose**      | Expands elements | Collects elements |
| **Used in**      | Arrays, objects, function calls | Function parameters, array destructuring |
| **Position**     | Used in function calls and literals | Used in function parameter definitions |
| **Example**      | `let arr = [...nums]` | `function(...args) {}` |

---

### **Quick Summary**
- **Spread (`...`)**: Expands elements (used for copying, merging, passing values).  
- **Rest (`...`)**: Gathers multiple elements into a single array (used in functions and destructuring).  

