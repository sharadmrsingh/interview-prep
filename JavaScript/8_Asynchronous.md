# 8_Asynchronous.md

### Table of Contents

| No. | Topic |
| --- | ------ |
| 1 | [Callback](#1-callback) |
| 2 | [Promise](#2-promise) |
| 3 | [async / await](#3-async--await) |
| 4 | [Event Loop](#4-event-loop) |
| 5 | [Debounce](#5-debounce) |
| 6 | [Throttle](#6-throttle) |

---

## 1. Callback
Fn passed as arg to another fn

`setTimeout(()=>console.log('Hi'),1000)`

---

## 2. Promise
An object representing the result of an asynchronous operation (pending, fulfilled, or rejected).

**In short:** Object for async result: pending→fulfilled/rejected

**Ex 1 line**: `new Promise(res=>res('done'))`

---

## 3. async / await
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

## 4. Event Loop
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

## 5. Debounce
Limits fn call rate after delay

`debounce(fn,300)`

---

## 6. Throttle
Limits fn calls within interval

`throttle(fn,500)`

---