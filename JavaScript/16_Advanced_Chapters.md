# 16_Advanced_Chapters.md

### Table of Contents

| No. | Topic |
| --- | ------ |
| 1 | [Iterator](#1-iterator) |
| 2 | [Iterable](#2-iterable) |
| 3 | [Symbol.iterator](#3-symboliterator) |
| 4 | [for...of](#4-forof) |
| 5 | [Generator Function](#5-generator-function) |
| 6 | [Generator Object](#6-generator-object) |
| 7 | [yield keyword](#7-yield-keyword) |
| 8 | [yield*](#8-yield) |
| 9 | [.next()](#9-next) |
| 10 | [.return()](#10-return) |
| 11 | [Generator vs Function](#11-generator-vs-function) |
| 12 | [Async Generator](#12-async-generator) |
| 13 | [for await...of](#13-for-awaitof) |

---

## 1. Iterator
- An object that defines a sequence 
- And returns values one by one using .next() method that returns { value, done }.

```js
const it = [10, 20][Symbol.iterator]();  
console.log(it.next().value); // 10 ✅ only value  
console.log(it.next());       // { value: 20, done: false } ✅ full object  
console.log(it.next());       // { value: undefined, done: true } ✅ iteration finished
```

---

## 2. Iterable
An object that can be looped using **for...of** or spread **(...)**.

`[1,2,3] or 'abc' are iterables.`

---

## 3. Symbol.iterator
Built-in key that defines how an object becomes iterable.

`[1,2,3][Symbol.iterator]()`

---

## 4. for...of
Uses the iterator internally to loop through values.

`for (const v of [1,2,3]) console.log(v);`

---

## 5. Generator Function
A special function that pauses and resumes with **yield.**

`function* gen(){yield 1; yield 2;}`

---

## 6. Generator Object
Calling a generator creates an iterator.

`const g = gen(); g.next();`

---

## 7. yield keyword
Pauses generator execution and returns a value.

`function* g(){yield 'A';}`

---

## 8. yield*
Delegates control to another generator or iterable.

`function* g(){yield* [1,2,3];}`

---

## 9. .next()
Resumes generator and returns { value, done }.

`g.next();`

---

## 10. .return()
Ends generator early and sets **done: true.**

`g.return('end');`

---

## 11. Generator vs Function
Normal fn runs completely; generator runs step-by-step.

`function* g(){yield 1; yield 2;}`

---

## 12. Async Generator
Yields Promises, used with **for await...of.**

`async function* g(){yield 1; yield 2;}`

---

## 13. for await...of
Iterates over async iterables (Promises).

`for await (let v of g()) console.log(v);`

---