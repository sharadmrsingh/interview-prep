# 🧩 4_Functions.md

Everything about functions, context, and execution.

---

### Table of Contents

| No. | Topic |
| --- | ------ |
| 1 | [Closure](#1-closure) |
| 2 | [Higher-Order Function (HOF)](#2-higher-order-function-hof) |
| 3 | [Arrow Function](#3-arrow-function) |
| 4 | [Currying](#4-currying) |
| 5 | [Pure Function](#5-pure-function) |
| 6 | [IIFE](#6-iife) |

---

## 1. Closure  
A function that remembers variables from its outer scope even after execution.  

**In short:** Inner fn remembers outer vars even after outer ends

**Ex 1 line:** `function a(){let x=10;return()=>x}`

**Example:**
```js
function outer() {
  let count = 0; // outer variable

  function inner() {
    count++; // inner function uses outer variable
    return count;
  }

  return inner; // return inner function
}

const counter = outer();

console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

---

## 2. Higher-Order Function (HOF)
A **higher-order function** is one that **takes another function as an argument or returns a function.**

**Example**
```js
const hof = fn => fn(5); // takes fn as argument
```

**or**
```js
function outer() { return () => console.log('Hi'); } // returns a function
```

---

## 3. Arrow Function

A shorter function syntax that doesn’t bind its own this.  

**In short:** Short syntax, no its own **this**

**Example:**
```js
const person = {
  name: "Rahul",
  normalFn: function () {
    console.log("Normal:", this.name);
  },
  arrowFn: () => {
    console.log("Arrow:", this.name);
  },
};

person.normalFn(); // "Normal: Rahul" -> `this` refers to person
person.arrowFn();  // "Arrow: undefined" -> `this` comes from outer scope
```

---

## 4. Currying
Currying transforms a function with multiple arguments into a chain of single-argument functions.

```js
const add = a => b => a + b;
console.log(add(2)(3)); // 5
```

---

## 5. Pure Function
Always returns the same output for the same input and causes no side effects.

**Short:** Same I/P=Same O/P, no side effect

```js
const add = (a, b) => a + b; // always predictable, no external change
```

---

## 6. IIFE
Immediately Invoked Function Expression

`(()=>console.log('run'))()`

---