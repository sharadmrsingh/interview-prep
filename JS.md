# JavaScript Notes  
**Source:** ChatGPT  

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

## 4. Type coercion
JS auto converts types in ops

`1 + "2" // "12"`

---

## 5. Difference Between `==` and `===`  
- `==` → checks value (with type coercion)  
- `===` → checks value **and** type  

---

## 6. NaN
Not-a-Number, type is Number

`typeof NaN // "number"`

---

## 7. Closure  
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

## 8. Callback
Fn passed as arg to another fn

`setTimeout(()=>console.log('Hi'),1000)`

---

## 9. Higher-Order Function (HOF)
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

## 10. Promise
An object representing the result of an asynchronous operation (pending, fulfilled, or rejected).

**In short:** Object for async result: pending→fulfilled/rejected

**Ex 1 line**: `new Promise(res=>res('done'))`

---

## 11. async / await
Runs synchronously until the first await.

Syntax sugar over Promises to write async code as synchronous.

**One-liner definition:**
👉 async/await makes asynchronous code look synchronous by pausing execution at await until the Promise resolves or rejects.

**Example:**
```js
function fakeApi() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Data received"), 1000);
  });
}

async function getData() {
  console.log("Fetching...");
  const result = await fakeApi(); // wait for promise to resolve
  console.log(result);
}

getData();
console.log("After function call");

```

**Output:**
```r
Fetching...
After function call
Data received
```

**Why this order?**

- **Fetching...** → runs immediately

- **After function call** → async function didn’t block

- **Data received** → printed after 1s (await resolved)

**Another Example:**
```js
async function demo() {
  console.log("1: Start");   // sync
  await Promise.resolve();   // async pause
  console.log("2: After await"); // async resume
}

console.log("A: Before call");
demo();
console.log("B: After call");
```

**Output:**
```pgsql
A: Before call
1: Start
B: After call
2: After await
```

✅ See how:

- “1: Start” ran synchronously.

- At **await**, function paused and returned a Promise.

- Later, “2: After await” ran asynchronously.

---

## 12. Event Loop
**Def. 1:** Mechanism that handles asynchronous callbacks by continously checking & executing pending tasks.

**Def. 2:** Mechanism that handles asynchronous callbacks via call stack + callback queue.

**One-liner definition:**
👉 The event loop continuously checks the call stack, executes sync code first, then handles microtasks (Promises), and finally tasks (setTimeout, setInterval, I/O).

**Example:**
```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout callback");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise resolved");
});

console.log("End");
```

**Output:**
```sql
Start
End
Promise resolved
Timeout callback
```

**Explanation:**

- **Start** → synchronous

- **End** → synchronous

- **Promise resolved** → microtask queue

- **Timeout callback** → task queue

---

## 13. Prototype
Objects inherit props/methods from prototypes/other objects

`arr.__proto__===Array.prototype`

---

## 14. **this** Keyword
Refers to the object that is **calling the function.**

---

## 15. Arrow Function

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

## 16. Destructuring
Unpack values from arrays/objects

`let {x,y}=point`

---

## 17. Spread operator
Expands iterable into individual elems

`let arr=[...a,...b]`

---

## 18. Rest operator
Collects multiple args into array

`function sum(...nums){}`

---

## 19. Template literal
String with embedded expressions

```js
const name = "Test"; 
console.log(`Hi ${name}`); // Hi Test
```

---

## 20. Array methods
map, filter, reduce for clean loops

`[1,2,3].map(x=>x*2)`

---

## 21. Deep vs Shallow copy
Shallow copies refs of nested data, deep copies values

`let b=[...a]`

---

## 22. Event bubbling
Event goes child → parent

`e.stopPropagation()`

---

## 23. IIFE
Immediately Invoked Function Expression

`(()=>console.log('run'))()`

---

## 24. Debounce
Limits fn call rate after delay

`debounce(fn,300)`

---

## 25. Throttle
Limits fn calls within interval

`throttle(fn,500)`

---

## 26. LocalStorage
Stores key-value in browser

`localStorage.setItem('x',1)`

---

## 27. JSON
Data format for APIs

`JSON.parse('{"x":1}')`

---