# 2_Operators.md

### Table of Contents

| No. | Topic |
| --- | ------ |
| 1 | [Type coercion](#1-type-coercion) |
| 2 | [Difference Between == and ===](#2-difference-between--and-) |
| 3 | [Short-Circuit Evaluation](#3-short-circuit-evaluation) |

---

## 1. Type coercion
JS auto converts types in ops

`1 + "2" // "12"`

---

## 2. Difference Between `==` and `===`  
- `==` → checks value (with type coercion)  
- `===` → checks value **and** type  

---

## 3. Short-Circuit Evaluation
- In JS, logical operators **&&** and **||** stop evaluating once the result is determined.
- 👉 **&&** returns first falsy, **||** returns first truthy value.

```js
const x = false && "Hi";   // false  
const y = true || "Hello"; // true
```

---