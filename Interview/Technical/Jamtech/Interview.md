# 📘 Jamtech Walkin Technical Interview MERN Question Summary
**Date:** 01/12/25

A structured README-style summary of all the questions asked, grouped by domain.

➡️ **Answers have been added below the questions.**

---

# 📌 Questions (With Answers Added Below)
## 🧑‍💼 Basic

### 1. About Yourself

### 2. Laravel
You mentioned:
- You **know Laravel**.
- You **explained your experience**.
- You clarified that you **did not study PHP much**, your **focus is mainly on JavaScript**.

**Interviewer Remark:**  
> *“Pehle React toh padh lo”* — implying your React fundamentals should be strengthened first.

---

## 🟨 JavaScript

### 1. Boolean — What Values Do They Hold?  
- Can we use the **Boolean object**?

### 2. `Object.assign`  

### 3. Does Java Support Pointers?  

---

## ⚛️ React.js

### 1. `useState` & `useReducer`  

### 2. Custom Hook?  

### 3. Can Two Contexts Share Data?  
Whether **Context A** and **Context B** can communicate.

### 4. Lazy Loading & Suspense  

### 5. `useId`  

### 6. Can We Conditionally Use `useState` & `useEffect`?  

### 7. `useMemo`  
You are a developer you should know its not a school paper that you didn't studied

### 8. Custom Hook — Books Add/Update  
You were asked to **design a custom hook on pen & paper**  
for adding & updating books.

---

## 🟩 Node.js

### 1. How to Make a Custom Logger  

### 2. Have You Used NestJS or Node with Express?  

---

## 📱 React Native

### 1. `FlatList`  
---

## 📝 Feedback

### ❓ **Q:** You asked: *“On which thing should I work?”*  
### 💬 **A:** *“Conversation”*  
Meaning: improve communication, clarity, and structured explanation.

---

# ✅ Answers Section (Short + Examples)

## 🟨 JavaScript

### **1. Boolean — What Values Do They Hold?**
Boolean holds **true** or **false**.  
Other values convert to boolean using truthy/falsy rules.

**Example:**
```js
Boolean(0)       // false
Boolean("Hi")    // true
```

Boolean Object?

Yes, but not recommended because it creates an object, not a primitive.

```new Boolean(false) // object → truthy```

### **2. Object.assign**

Copies properties from source objects to a target object.

```
const target = {a:1};
const src = {b:2};
Object.assign(target, src);
// {a:1, b:2}
```

### **3. Does Java Support Pointers?**

No.
Java removed pointers for safety. It only uses references.

---

## ⚛️ React.js Answers
### **1. useState vs useReducer**

useState → simple state

useReducer → multiple actions / complex logic

```
const [count, setCount] = useState(0);

function reducer(state, action) {
  switch(action.type){
    case "inc": return state + 1;
  }
}
```

### **2. What Is a Custom Hook?**

A reusable logic function starting with use.

```
function useCounter(){
  const [c,setC] = useState(0);
  return {c, inc:()=>setC(c+1)};
}
```

### **3. Can Two Contexts Share Data?**

**Yes — but not directly.**

Two contexts (**Context A** and **Context B**) cannot talk to each other by themselves,
but a **common parent component** can:

- Read both contexts

- Combine their values

- Pass merged data to children

This is the correct pattern.


**✔️ Clear Example**

**🟦 Create Two Contexts**
```
const UserContext = createContext();
const ThemeContext = createContext();
```

**🟩 Parent Component that combines both**
```
function App() {
  const user = { name: "Rahul" };
  const theme = { color: "blue" };

  return (
    <UserContext.Provider value={user}>
      <ThemeContext.Provider value={theme}>
        <Dashboard />
      </ThemeContext.Provider>
    </UserContext.Provider>
  );
}
```

🟧 Child Component reading data from BOTH contexts
```
function Dashboard() {
  const user = useContext(UserContext);
  const theme = useContext(ThemeContext);

  const combined = {
    username: user.name,
    themeColor: theme.color
  };

  return (
    <h1 style={{ color: combined.themeColor }}>
      Hello {combined.username}
    </h1>
  );
}
```

🎯 Easy Explanation

- Context A provides **user data**

- Context B provides **theme data**

- The component **Dashboard** reads **both**, combines them, and uses them together.

**This is how two contexts "share" data — through the component using them.**

### **4. Lazy Loading & Suspense**

Used for code-splitting.

```
const Page = React.lazy(() => import('./Page'));
```

Suspense shows fallback while loading.

### **5. useId**

Used to generate unique IDs (e.g., forms).
```
const id = useId();
<label htmlFor={id}>Name</label>
<input id={id} />
```

### **6. Can We Conditionally Use Hooks?**

❌ No.
Hooks must not be inside conditions or loops.

### **7. useMemo**

Memoizes expensive calculations.
```
const value = useMemo(() => heavyCalc(num), [num]);
```

### **8. Custom Hook — Add/Update Books**
```
function useBooks(){
  const [books, setBooks] = useState([]);

  function add(book){
    setBooks([...books, book]);
  }

  function update(id, data){
    setBooks(books.map(b => b.id===id ? {...b, ...data} : b));
  }

  return {books, add, update};
}
```

---

## 🟩 Node.js Answers
### **1. Custom Logger**
```
const fs = require('fs');

function log(msg){
  fs.appendFileSync('log.txt', `${new Date()} - ${msg}\n`);
}

module.exports = log;
```

### **2. NestJS or Express?**

Express → minimal

NestJS → structured, modular, TypeScript-first.

---

## 📱 React Native
### **1. FlatList**

Efficient list renderer.

```
<FlatList
  data={items}
  renderItem={({item}) => <Text>{item.name}</Text>}
/>
```
