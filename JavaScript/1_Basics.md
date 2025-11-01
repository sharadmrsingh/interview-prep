# 🧱 1_Basics.md

Covers JS fundamentals, data handling, and behavior basics.

---

### Table of Contents

| No. | Topic |
| --- | ------ |
| 1 | [var, let, const](#1-var-let-const) |
| 2 | [Hoisting](#2-hoisting) |
| 3 | [Scope](#3-scope) |
| 4 | [NaN](#4-nan) |

---

## 1. var, let, const  
- `var` → function scope  
- `let` & `const` → block scope  
- `const` → value can’t be changed  

---

## 2. Hoisting  
JavaScript moves **declarations** to the top during compilation.  
**Example:**
```js
console.log(a); var a = 5; // undefined
```

---

## 3. Scope
Defines where a variable is accessible

`function test(){let x=1}`

---

## 4. NaN
Not-a-Number, type is Number

`typeof NaN // "number"`

---