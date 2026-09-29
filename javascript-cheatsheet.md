# 🟨 JavaScript Complete Cheat Sheet — Basics to Advanced
*Based on MDN JavaScript documentation. Simple, crisp, beginner-friendly.*

---

## 📑 Table of Contents
1. [Getting Started](#1-getting-started)
2. [Variables](#2-variables)
3. [Data Types](#3-data-types)
4. [Type Conversion](#4-type-conversion)
5. [Operators](#5-operators)
6. [Conditionals](#6-conditionals)
7. [Loops](#7-loops)
8. [Functions](#8-functions)
9. [Strings & Methods](#9-strings--methods)
10. [Numbers & Math](#10-numbers--math)
11. [Arrays & Methods](#11-arrays--methods)
12. [Objects](#12-objects)
13. [Destructuring, Spread & Rest](#13-destructuring-spread--rest)
14. [Scope, Hoisting & Closures](#14-scope-hoisting--closures)
15. [`this` Keyword](#15-this-keyword)
16. [Classes & OOP](#16-classes--oop)
17. [Prototypes & Inheritance](#17-prototypes--inheritance)
18. [Error Handling](#18-error-handling)
19. [JSON](#19-json)
20. [Timers](#20-timers)
21. [Asynchronous JavaScript](#21-asynchronous-javascript)
22. [Fetch API (HTTP Requests)](#22-fetch-api-http-requests)
23. [DOM Manipulation](#23-dom-manipulation)
24. [Events](#24-events)
25. [Browser Storage](#25-browser-storage)
26. [Modules (import/export)](#26-modules-importexport)
27. [Map, Set, WeakMap, WeakSet](#27-map-set-weakmap-weakset)
28. [Iterators & Generators](#28-iterators--generators)
29. [Symbols](#29-symbols)
30. [Regular Expressions](#30-regular-expressions)
31. [Date & Time](#31-date--time)
32. [Advanced Concepts](#32-advanced-concepts)
33. [Modern Operators (ES2020+)](#33-modern-operators-es2020)
34. [Strict Mode & Best Practices](#34-strict-mode--best-practices)

---

## 1. Getting Started

| Syntax | Meaning |
|---|---|
| `<script src="app.js"></script>` | Link JS file to HTML (place before `</body>`) |
| `console.log(x)` | Print value to console (for debugging) |
| `console.error(x)` | Print error message |
| `console.warn(x)` | Print warning |
| `console.table(arr)` | Print array/object as a table |
| `alert("Hi")` | Popup message box |
| `prompt("Name?")` | Popup asking user input (returns string) |
| `confirm("Sure?")` | Popup with OK/Cancel (returns true/false) |
| `// comment` | Single-line comment |
| `/* comment */` | Multi-line comment |

---

## 2. Variables

| Syntax | Meaning |
|---|---|
| `let x = 5;` | Variable that **can be changed** later. Block-scoped. ✅ Use this |
| `const x = 5;` | Variable that **cannot be reassigned**. Block-scoped. ✅ Use by default |
| `var x = 5;` | Old way. Function-scoped, hoisted. ❌ Avoid |

**Rules for names:** must start with letter, `_` or `$`. Case-sensitive. Use `camelCase`.

> 💡 `const` objects/arrays can still have their **contents** changed — only reassignment is blocked.

---

## 3. Data Types

### Primitive Types (stored by value)
| Type | Example | Meaning |
|---|---|---|
| `String` | `"hello"` | Text |
| `Number` | `42`, `3.14` | Integers & decimals (one type for both) |
| `BigInt` | `123n` | Very large integers |
| `Boolean` | `true`, `false` | Yes/No values |
| `undefined` | `let x;` | Declared but no value given |
| `null` | `let x = null;` | Intentionally empty value |
| `Symbol` | `Symbol("id")` | Unique identifier |

### Reference Types (stored by reference)
| Type | Example |
|---|---|
| `Object` | `{name: "Ram"}` |
| `Array` | `[1, 2, 3]` |
| `Function` | `function(){}` |

### Checking Types
| Syntax | Result |
|---|---|
| `typeof "hi"` | `"string"` |
| `typeof 42` | `"number"` |
| `typeof null` | `"object"` ⚠️ (famous JS bug) |
| `typeof undefined` | `"undefined"` |
| `Array.isArray([1,2])` | `true` — correct way to check arrays |
| `x instanceof Object` | Checks if x is instance of a class/type |

---

## 4. Type Conversion

| Syntax | Meaning |
|---|---|
| `String(123)` | Number → `"123"` |
| `Number("123")` | String → `123` |
| `Number("abc")` | → `NaN` (Not a Number) |
| `parseInt("42px")` | → `42` (reads number from start of string) |
| `parseFloat("3.14m")` | → `3.14` |
| `Boolean(value)` | Any value → true/false |
| `+"5"` | Quick string → number (`5`) |
| `5 + ""` | Quick number → string (`"5"`) |

**Falsy values** (become `false`): `0`, `""`, `null`, `undefined`, `NaN`, `false`
**Everything else is truthy** (including `"0"`, `[]`, `{}`)

---

## 5. Operators

### Arithmetic
| Operator | Meaning |
|---|---|
| `+ - * /` | Add, subtract, multiply, divide |
| `%` | Remainder (modulus): `10 % 3` → `1` |
| `**` | Power: `2 ** 3` → `8` |
| `++` / `--` | Increase / decrease by 1 |

### Assignment
| Operator | Same as |
|---|---|
| `x += 5` | `x = x + 5` |
| `x -= 5` | `x = x - 5` |
| `x *= 5` | `x = x * 5` |
| `x /= 5` | `x = x / 5` |
| `x %= 5` | `x = x % 5` |
| `x **= 2` | `x = x ** 2` |

### Comparison
| Operator | Meaning |
|---|---|
| `==` | Equal (converts types) ⚠️ `"5" == 5` is `true` |
| `===` | Strictly equal (type + value) ✅ Always use this |
| `!=` | Not equal (converts types) |
| `!==` | Strictly not equal ✅ |
| `> < >= <=` | Greater / less than |

### Logical
| Operator | Meaning |
|---|---|
| `&&` | AND — true if **both** are true |
| `\|\|` | OR — true if **at least one** is true |
| `!` | NOT — flips true/false |

### Ternary (short if/else)
```js
let result = age >= 18 ? "Adult" : "Minor";
// Reads as: condition ? valueIfTrue : valueIfFalse
```

---

## 6. Conditionals

| Syntax | Meaning |
|---|---|
| `if (cond) {...}` | Run code if condition is true |
| `else if (cond) {...}` | Check another condition |
| `else {...}` | Run if nothing above matched |

### switch — for comparing one value to many options
```js
switch (day) {
  case "Mon": ...; break;   // break stops fall-through
  case "Tue": ...; break;
  default: ...;             // runs if no case matches
}
```

---

## 7. Loops

| Syntax | Use When |
|---|---|
| `for (let i = 0; i < 5; i++) {...}` | You know how many times to repeat |
| `while (cond) {...}` | Repeat until condition becomes false |
| `do {...} while (cond);` | Same, but runs **at least once** |
| `for (const item of array) {...}` | Loop through array **values** ✅ |
| `for (const key in object) {...}` | Loop through object **keys** |
| `array.forEach(item => {...})` | Run a function for each array item |

### Loop Control
| Keyword | Meaning |
|---|---|
| `break` | Exit the loop completely |
| `continue` | Skip current round, go to next |
| `label:` | Name a loop so `break label` can exit outer loops |

---

## 8. Functions

| Syntax | Meaning |
|---|---|
| `function greet(name) { return "Hi " + name; }` | Function declaration (hoisted — usable before defined) |
| `const greet = function(name) {...};` | Function expression (not hoisted) |
| `const greet = (name) => "Hi " + name;` | Arrow function — short syntax ✅ |
| `const add = (a, b = 10) => a + b;` | Default parameter (`b` is 10 if not given) |
| `function sum(...nums) {...}` | Rest parameter — collects all arguments into an array |
| `(function(){ ... })();` | IIFE — runs immediately once |
| `return value;` | Send value back; function stops here |

### Arrow Function Shortcuts
```js
const square = x => x * x;        // one param: no ( ) needed
const hello = () => "Hi";         // no params: empty ( )
const add = (a, b) => a + b;      // one line: no { } or return needed
const obj = () => ({ a: 1 });     // returning object: wrap in ( )
```

> ⚠️ Arrow functions do **not** have their own `this` — they borrow it from surrounding code.

### Callback Function — a function passed to another function
```js
function process(data, callback) { callback(data); }
process("hi", msg => console.log(msg));  // "hi"
```

---

## 9. Strings & Methods

| Syntax | Result / Meaning |
|---|---|
| `` `Hello ${name}` `` | Template literal — insert variables into text ✅ |
| `str.length` | Number of characters |
| `str[0]` / `str.charAt(0)` | First character |
| `str.at(-1)` | Last character |
| `str.toUpperCase()` | `"HI"` |
| `str.toLowerCase()` | `"hi"` |
| `str.trim()` | Remove spaces from both ends |
| `str.trimStart()` / `str.trimEnd()` | Remove spaces from one side |
| `str.includes("lo")` | `true` if text contains "lo" |
| `str.startsWith("He")` | `true` if starts with "He" |
| `str.endsWith("lo")` | `true` if ends with "lo" |
| `str.indexOf("l")` | Position of first "l" (−1 if not found) |
| `str.lastIndexOf("l")` | Position of last "l" |
| `str.slice(1, 4)` | Cut portion from index 1 to 3 (end not included) |
| `str.substring(1, 4)` | Same as slice (but no negative index) |
| `str.replace("a", "b")` | Replace first "a" with "b" |
| `str.replaceAll("a", "b")` | Replace **all** "a" with "b" |
| `str.split(",")` | Break string into array: `"a,b"` → `["a","b"]` |
| `str.concat(s2)` | Join strings (or just use `+`) |
| `str.repeat(3)` | `"hihihi"` |
| `str.padStart(5, "0")` | `"00042"` — pad from left to length 5 |
| `str.padEnd(5, "*")` | `"42***"` |
| `str.charCodeAt(0)` | Unicode number of a character |
| `String.fromCharCode(65)` | `"A"` — character from Unicode number |

> 💡 Strings are **immutable** — methods return a **new** string; the original never changes.

---

## 10. Numbers & Math

| Syntax | Result / Meaning |
|---|---|
| `num.toFixed(2)` | Round to 2 decimals, returns **string**: `"3.14"` |
| `num.toString()` | Number → string |
| `num.toString(2)` | Convert to binary string |
| `Number.isInteger(5)` | `true` |
| `Number.isNaN(x)` | Safe NaN check |
| `Number.MAX_SAFE_INTEGER` | Largest safe integer |
| `Infinity` / `-Infinity` | Result of dividing by 0 |

### Math Object
| Syntax | Result |
|---|---|
| `Math.round(4.5)` | `5` — nearest integer |
| `Math.floor(4.9)` | `4` — round down |
| `Math.ceil(4.1)` | `5` — round up |
| `Math.trunc(4.9)` | `4` — chop off decimals |
| `Math.abs(-7)` | `7` — positive value |
| `Math.pow(2, 3)` | `8` |
| `Math.sqrt(16)` | `4` |
| `Math.cbrt(27)` | `3` — cube root |
| `Math.min(1, 2, 3)` | `1` |
| `Math.max(1, 2, 3)` | `3` |
| `Math.random()` | Random decimal between 0 and 1 |
| `Math.floor(Math.random() * 10) + 1` | Random integer 1–10 |
| `Math.PI` | `3.14159...` |

---

## 11. Arrays & Methods

### Creating & Accessing
| Syntax | Meaning |
|---|---|
| `const arr = [1, 2, 3];` | Create array |
| `arr[0]` | First item |
| `arr.at(-1)` | Last item ✅ |
| `arr.length` | Number of items |
| `Array.from("abc")` | `["a","b","c"]` — make array from iterable |
| `Array.of(1, 2, 3)` | `[1,2,3]` |

### Add / Remove (these CHANGE the original array)
| Syntax | Meaning |
|---|---|
| `arr.push(x)` | Add to **end** |
| `arr.pop()` | Remove from **end** (returns removed item) |
| `arr.unshift(x)` | Add to **start** |
| `arr.shift()` | Remove from **start** |
| `arr.splice(1, 2)` | Remove 2 items starting at index 1 |
| `arr.splice(1, 0, "new")` | Insert "new" at index 1 (remove 0) |
| `arr.sort()` | Sort alphabetically ⚠️ |
| `arr.sort((a, b) => a - b)` | Sort numbers ascending ✅ |
| `arr.sort((a, b) => b - a)` | Sort numbers descending |
| `arr.reverse()` | Reverse order |
| `arr.fill(0)` | Fill all with 0 |

### Search & Check (do NOT change the array)
| Syntax | Meaning |
|---|---|
| `arr.includes(3)` | `true` if 3 exists |
| `arr.indexOf(3)` | Position of 3 (−1 if not found) |
| `arr.find(x => x > 2)` | **First value** matching condition |
| `arr.findIndex(x => x > 2)` | **Index** of first match |
| `arr.findLast(x => x > 2)` | Last matching value |
| `arr.some(x => x > 2)` | `true` if **at least one** matches |
| `arr.every(x => x > 2)` | `true` if **all** match |

### Transform (return a NEW array — very important! ✅)
| Syntax | Meaning |
|---|---|
| `arr.map(x => x * 2)` | New array with each item changed |
| `arr.filter(x => x > 2)` | New array with only matching items |
| `arr.reduce((total, x) => total + x, 0)` | Combine all items into one value (0 = starting total) |
| `arr.slice(1, 3)` | Copy portion (original untouched) |
| `arr.concat(arr2)` | Join arrays into new one |
| `arr.flat()` | Flatten nested arrays one level: `[1,[2,3]]` → `[1,2,3]` |
| `arr.flat(Infinity)` | Flatten completely |
| `arr.flatMap(x => [x, x*2])` | map + flat in one step |
| `arr.join("-")` | Array → string: `[1,2]` → `"1-2"` |
| `arr.toSorted()` / `arr.toReversed()` | Sorted/reversed **copy** (original safe) |
| `[...arr]` | Quick copy of an array |

### Simple example of the "big three":
```js
const nums = [1, 2, 3, 4];
nums.map(n => n * 2);            // [2, 4, 6, 8]   → transform each
nums.filter(n => n % 2 === 0);   // [2, 4]         → keep matching
nums.reduce((sum, n) => sum + n, 0); // 10          → combine to one
```

---

## 12. Objects

| Syntax | Meaning |
|---|---|
| `const user = { name: "Ram", age: 25 };` | Create object (key: value pairs) |
| `user.name` | Read property (dot notation) |
| `user["name"]` | Read property (bracket — for dynamic/spaced keys) |
| `user.city = "Chennai";` | Add / update property |
| `delete user.age;` | Remove property |
| `"name" in user` | `true` if key exists |
| `user.greet = function() {...}` | Method — function inside object |
| `{ name, age }` | Shorthand — same as `{ name: name, age: age }` |
| `{ [key]: value }` | Computed key — key name from a variable |

### Object Utility Methods
| Syntax | Meaning |
|---|---|
| `Object.keys(obj)` | Array of keys: `["name","age"]` |
| `Object.values(obj)` | Array of values: `["Ram", 25]` |
| `Object.entries(obj)` | Array of pairs: `[["name","Ram"],["age",25]]` |
| `Object.assign({}, obj)` | Shallow copy / merge objects |
| `Object.freeze(obj)` | Lock object — no changes allowed |
| `Object.isFrozen(obj)` | Check if frozen |
| `Object.fromEntries(pairs)` | Pairs array → object (reverse of entries) |
| `structuredClone(obj)` | **Deep copy** (nested objects copied too) ✅ |

### Optional Chaining — safe access
```js
user?.address?.city   // undefined instead of crash if address missing
user?.greet?.()       // call method only if it exists
```

---

## 13. Destructuring, Spread & Rest

### Destructuring — unpack values into variables
| Syntax | Meaning |
|---|---|
| `const { name, age } = user;` | Pull properties out of object |
| `const { name: n } = user;` | Rename while pulling (`n` = user.name) |
| `const { city = "NA" } = user;` | Default if property missing |
| `const [a, b] = [1, 2];` | Pull values out of array |
| `const [first, , third] = arr;` | Skip items with empty slot |
| `const { a: { b } } = obj;` | Nested destructuring |
| `function show({ name }) {...}` | Destructure directly in parameters |
| `[a, b] = [b, a];` | Swap two variables ✨ |

### Spread `...` — expand items OUT
| Syntax | Meaning |
|---|---|
| `[...arr1, ...arr2]` | Merge arrays |
| `{...obj1, ...obj2}` | Merge objects (later keys win) |
| `Math.max(...nums)` | Pass array items as separate arguments |
| `[...str]` | String → array of characters |

### Rest `...` — collect items IN
| Syntax | Meaning |
|---|---|
| `function f(...args)` | All arguments → array |
| `const [first, ...others] = arr;` | First item, then rest as array |
| `const { name, ...rest } = obj;` | One property, rest as new object |

---

## 14. Scope, Hoisting & Closures

### Scope — where a variable is visible
| Type | Meaning |
|---|---|
| Global scope | Declared outside everything — visible everywhere |
| Function scope | Declared inside a function — visible only there |
| Block scope | `let`/`const` inside `{ }` — visible only inside that block |

### Hoisting — declarations move to top before code runs
| Declaration | Behavior |
|---|---|
| `var` | Hoisted, value is `undefined` until assigned ⚠️ |
| `let` / `const` | Hoisted but **locked** (error if used before line) ✅ |
| `function f(){}` | Fully hoisted — can call before it's defined |

### Closure — a function that "remembers" outer variables
```js
function counter() {
  let count = 0;              // private variable
  return () => ++count;       // inner function remembers count
}
const add = counter();
add(); // 1
add(); // 2  ← count survived between calls!
```
**Why it matters:** used for private data, counters, and function factories.

---

## 15. `this` Keyword

`this` = "the object that is currently calling the function"

| Where used | `this` refers to |
|---|---|
| Alone / global | `window` (browser) or `undefined` (strict mode) |
| Object method `obj.fn()` | The object `obj` |
| Regular function | `undefined` (strict) / `window` |
| Arrow function | Whatever `this` is in the **surrounding** code (no own `this`) |
| Event handler | The HTML element that fired the event |
| Class method | The class instance |

### Controlling `this` manually
| Syntax | Meaning |
|---|---|
| `fn.call(obj, a, b)` | Call fn with `this = obj`, arguments separate |
| `fn.apply(obj, [a, b])` | Same, but arguments as array |
| `fn.bind(obj)` | Returns a **new function** permanently tied to obj |

---

## 16. Classes & OOP

```js
class Person {
  constructor(name, age) {   // runs when object is created
    this.name = name;
    this.age = age;
  }
  greet() {                  // method
    return `Hi, I'm ${this.name}`;
  }
}
const p = new Person("Ram", 25);  // create object (instance)
p.greet();                        // "Hi, I'm Ram"
```

| Syntax | Meaning |
|---|---|
| `class Name {}` | Define a class (blueprint for objects) |
| `constructor()` | Setup function — runs on `new` |
| `new Person(...)` | Create an instance |
| `static hello() {}` | Method on the **class itself**, not instances: `Person.hello()` |
| `#secret` | Private field — only accessible inside the class |
| `get fullName() {}` | Getter — read like a property: `p.fullName` |
| `set fullName(v) {}` | Setter — assign like a property: `p.fullName = "x"` |

### Inheritance
| Syntax | Meaning |
|---|---|
| `class Student extends Person {}` | Student gets everything Person has |
| `super(name, age)` | Call parent's constructor (must be first line) |
| `super.greet()` | Call parent's version of a method |
| Method override | Redefine a method in child → child's version wins |

### 4 OOP Pillars (simple definitions)
| Pillar | Meaning |
|---|---|
| **Encapsulation** | Keep data + methods together; hide internals (`#private`) |
| **Inheritance** | Child class reuses parent's code (`extends`) |
| **Polymorphism** | Same method name, different behavior in each class |
| **Abstraction** | Show only what's needed, hide complexity |

---

## 17. Prototypes & Inheritance

Every JS object has a hidden link to a **prototype** — a shared object it borrows methods from. This is how JS does inheritance under the hood (classes are just cleaner syntax over this).

| Syntax | Meaning |
|---|---|
| `Object.getPrototypeOf(obj)` | Get the prototype |
| `obj.__proto__` | Old way to access prototype ❌ avoid |
| `Person.prototype.sayHi = fn` | Add method shared by ALL instances |
| `Object.create(proto)` | New object with chosen prototype |
| `obj.hasOwnProperty("x")` | `true` if property is on obj itself (not inherited) |

**Prototype chain:** `myArray → Array.prototype → Object.prototype → null`
(When you call `arr.map()`, JS finds `map` on `Array.prototype`.)

---

## 18. Error Handling

```js
try {
  // risky code
} catch (error) {
  console.log(error.message);   // runs if error happens
} finally {
  // always runs (cleanup)
}
```

| Syntax | Meaning |
|---|---|
| `try {...}` | Code that might fail |
| `catch (err) {...}` | Handle the error (`err.name`, `err.message`, `err.stack`) |
| `finally {...}` | Runs no matter what |
| `throw new Error("msg")` | Create your own error |
| `throw new TypeError("msg")` | Specific error types: TypeError, RangeError, SyntaxError, ReferenceError |

### Custom Error Class
```js
class ValidationError extends Error {
  constructor(msg) { super(msg); this.name = "ValidationError"; }
}
```

---

## 19. JSON

JSON = text format for storing/sending data. Keys must be in `"double quotes"`.

| Syntax | Meaning |
|---|---|
| `JSON.stringify(obj)` | Object → JSON string (for sending/saving) |
| `JSON.stringify(obj, null, 2)` | Pretty-print with 2-space indent |
| `JSON.parse(str)` | JSON string → object (for reading) |

> ⚠️ JSON cannot store functions, `undefined`, or Symbols — they get dropped.

---

## 20. Timers

| Syntax | Meaning |
|---|---|
| `setTimeout(fn, 2000)` | Run `fn` once after 2 seconds |
| `setInterval(fn, 1000)` | Run `fn` every 1 second, forever |
| `clearTimeout(id)` | Cancel a timeout |
| `clearInterval(id)` | Stop an interval |

```js
const id = setInterval(() => console.log("tick"), 1000);
clearInterval(id);   // stop it
```

---

## 21. Asynchronous JavaScript

**Why:** JS runs one line at a time. Async lets slow tasks (network, timers) run in the background without freezing the page.

### 1) Callbacks (old way)
Function passed in, called when work finishes. Nesting many = "callback hell" ❌

### 2) Promises (better)
A Promise = "I'll give you a value later." Three states: **pending → fulfilled** or **rejected**.

| Syntax | Meaning |
|---|---|
| `new Promise((resolve, reject) => {...})` | Create a promise |
| `promise.then(value => {...})` | Runs on success |
| `promise.catch(err => {...})` | Runs on failure |
| `promise.finally(() => {...})` | Runs either way |
| `Promise.resolve(x)` | Instantly fulfilled promise |
| `Promise.reject(err)` | Instantly rejected promise |

### Promise Combinators (run many promises together)
| Syntax | Meaning |
|---|---|
| `Promise.all([p1, p2])` | Wait for **all**; fails if ANY fails |
| `Promise.allSettled([p1, p2])` | Wait for all; never fails, gives each result |
| `Promise.race([p1, p2])` | First to finish (success OR failure) wins |
| `Promise.any([p1, p2])` | First to **succeed** wins |

### 3) async / await (best ✅ — modern way)
```js
async function getData() {          // async = function returns a promise
  try {
    const res = await fetch(url);   // await = pause here until done
    const data = await res.json();
    return data;
  } catch (err) {
    console.log("Failed:", err);
  }
}
```

| Syntax | Meaning |
|---|---|
| `async function f() {}` | Marks function as async (always returns a Promise) |
| `await promise` | Wait for the promise result (only inside async functions) |
| `try/catch` | Handle errors with await |

### Event Loop (how JS handles async) — simple picture
1. **Call stack** — runs your code line by line
2. **Web APIs** — browser handles timers/fetch in background
3. **Task queues** — finished callbacks wait here
4. **Event loop** — moves waiting callbacks to the stack when it's empty

> Microtasks (promises) always run **before** macrotasks (setTimeout).

---

## 22. Fetch API (HTTP Requests)

### GET — read data
```js
const res = await fetch("https://api.example.com/users");
if (!res.ok) throw new Error(res.status);   // check for 404/500
const data = await res.json();              // parse JSON body
```

### POST — send data
```js
await fetch(url, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Ram" })
});
```

| Piece | Meaning |
|---|---|
| `method` | `"GET"`, `"POST"`, `"PUT"`, `"PATCH"`, `"DELETE"` |
| `headers` | Extra info (content type, auth tokens) |
| `body` | Data to send (stringified) |
| `res.ok` | `true` if status 200–299 |
| `res.status` | Status code number (200, 404, 500...) |
| `res.json()` | Body → object (returns promise) |
| `res.text()` | Body → plain text |

---

## 23. DOM Manipulation

DOM = the page as a tree of objects that JS can read and change.

### Selecting Elements
| Syntax | Meaning |
|---|---|
| `document.querySelector(".btn")` | **First** match (any CSS selector) ✅ |
| `document.querySelectorAll("li")` | **All** matches (NodeList — use forEach) ✅ |
| `document.getElementById("id")` | By id |
| `document.getElementsByClassName("c")` | By class (live collection) |
| `document.getElementsByTagName("p")` | By tag |

### Changing Content
| Syntax | Meaning |
|---|---|
| `el.textContent = "Hi"` | Change text (safe) ✅ |
| `el.innerHTML = "<b>Hi</b>"` | Change HTML ⚠️ risky with user input |
| `el.value` | Get/set input field value |

### Changing Style & Classes
| Syntax | Meaning |
|---|---|
| `el.style.color = "red"` | Inline style (camelCase: `backgroundColor`) |
| `el.classList.add("active")` | Add a class ✅ |
| `el.classList.remove("active")` | Remove a class |
| `el.classList.toggle("dark")` | Add if missing, remove if present |
| `el.classList.contains("active")` | Check if class exists |

### Attributes
| Syntax | Meaning |
|---|---|
| `el.getAttribute("href")` | Read attribute |
| `el.setAttribute("src", "a.png")` | Set attribute |
| `el.removeAttribute("disabled")` | Remove attribute |
| `el.dataset.userId` | Read `data-user-id="..."` custom attributes |

### Creating / Removing Elements
| Syntax | Meaning |
|---|---|
| `document.createElement("div")` | Make new element |
| `parent.append(el)` | Add at end (also accepts text) |
| `parent.prepend(el)` | Add at start |
| `el.before(x)` / `el.after(x)` | Insert as sibling |
| `el.remove()` | Delete element |
| `el.cloneNode(true)` | Copy element (true = with children) |
| `el.insertAdjacentHTML("beforeend", html)` | Insert HTML at position |

### Traversing (moving around the tree)
| Syntax | Meaning |
|---|---|
| `el.parentElement` | Go to parent |
| `el.children` | All child elements |
| `el.firstElementChild` / `el.lastElementChild` | First/last child |
| `el.nextElementSibling` / `el.previousElementSibling` | Next/previous element |
| `el.closest(".card")` | Nearest ancestor matching selector ✅ |

---

## 24. Events

```js
button.addEventListener("click", (e) => {
  console.log("Clicked!", e.target);
});
```

| Syntax | Meaning |
|---|---|
| `el.addEventListener("click", fn)` | Run fn on event ✅ |
| `el.removeEventListener("click", fn)` | Stop listening (fn must be named) |
| `e.target` | The element that triggered the event |
| `e.currentTarget` | The element the listener is attached to |
| `e.preventDefault()` | Stop default action (e.g., form reload, link jump) |
| `e.stopPropagation()` | Stop event from bubbling to parents |
| `{ once: true }` | Third argument — listener runs only one time |

### Common Event Types
| Category | Events |
|---|---|
| Mouse | `click`, `dblclick`, `mousedown`, `mouseup`, `mouseover`, `mouseout`, `mousemove` |
| Keyboard | `keydown`, `keyup` (use `e.key` for the pressed key) |
| Form | `submit`, `change`, `input`, `focus`, `blur` |
| Page | `DOMContentLoaded` (HTML ready), `load` (everything loaded), `scroll`, `resize` |

### Event Bubbling & Delegation
- **Bubbling:** events travel from clicked element UP through parents.
- **Delegation:** put ONE listener on the parent to handle all children ✅
```js
list.addEventListener("click", e => {
  if (e.target.matches("li")) console.log("li clicked:", e.target.textContent);
});
```

---

## 25. Browser Storage

| Feature | localStorage | sessionStorage |
|---|---|---|
| Lifetime | Forever (until cleared) | Until tab is closed |

| Syntax | Meaning |
|---|---|
| `localStorage.setItem("key", value)` | Save (value stored as string) |
| `localStorage.getItem("key")` | Read (returns string or null) |
| `localStorage.removeItem("key")` | Delete one |
| `localStorage.clear()` | Delete all |

**Storing objects:** `setItem("user", JSON.stringify(obj))` → `JSON.parse(getItem("user"))`

Other storage: **Cookies** (sent to server, small), **IndexedDB** (large structured data).

---

## 26. Modules (import/export)

Split code into files. Use `<script type="module" src="app.js">` in HTML.

| Syntax | Meaning |
|---|---|
| `export const x = 5;` | Named export (many per file) |
| `export function f() {}` | Named export of function |
| `export default MyClass;` | Default export (ONE per file) |
| `import { x, f } from "./utils.js";` | Import named exports (exact names) |
| `import { x as y } from "./u.js";` | Rename while importing |
| `import MyClass from "./c.js";` | Import default (any name) |
| `import * as utils from "./u.js";` | Import everything as one object |
| `const mod = await import("./m.js");` | Dynamic import — load only when needed |

---

## 27. Map, Set, WeakMap, WeakSet

### Map — key→value pairs, keys can be ANY type (better than object for this)
| Syntax | Meaning |
|---|---|
| `const m = new Map();` | Create |
| `m.set("key", value)` | Add / update |
| `m.get("key")` | Read |
| `m.has("key")` | Check exists |
| `m.delete("key")` | Remove |
| `m.size` | Count |
| `for (const [k, v] of m)` | Loop pairs |

### Set — collection of UNIQUE values
| Syntax | Meaning |
|---|---|
| `const s = new Set([1, 2, 2]);` | Creates `{1, 2}` — duplicates removed |
| `s.add(x)` / `s.delete(x)` / `s.has(x)` | Add / remove / check |
| `[...new Set(arr)]` | Remove duplicates from array ✨ |

### WeakMap / WeakSet
Keys must be objects; entries auto-deleted when object is garbage-collected. Used for private data & caching.

---

## 28. Iterators & Generators

### Iterator — object with `.next()` returning `{ value, done }`
Anything usable in `for...of` (arrays, strings, Maps, Sets) is **iterable**.

### Generator — function that can pause and resume
```js
function* counter() {     // note the *
  yield 1;                // pause here, give 1
  yield 2;                // next call resumes here
  yield 3;
}
const g = counter();
g.next();  // { value: 1, done: false }
g.next();  // { value: 2, done: false }
```

| Syntax | Meaning |
|---|---|
| `function* name() {}` | Define generator |
| `yield value` | Pause and output a value |
| `yield* otherGen()` | Delegate to another generator |
| `gen.next()` | Resume to the next yield |
| `for (const v of gen())` | Loop through all yielded values |
| `async function*` + `for await...of` | Async generators (stream data) |

---

## 29. Symbols

Symbol = a guaranteed-unique value. Used as hidden object keys so they never clash.

| Syntax | Meaning |
|---|---|
| `const id = Symbol("desc")` | Create unique symbol |
| `obj[id] = 123` | Use as hidden key (skipped by loops & JSON) |
| `Symbol.for("app")` | Get/create from global registry (shareable) |
| `Symbol.iterator` | Well-known symbol — makes an object work with `for...of` |

---

## 30. Regular Expressions

Pattern matching for strings. Written between slashes: `/pattern/flags`

| Syntax | Meaning |
|---|---|
| `/abc/` | Match the exact text "abc" |
| `\d` `\w` `\s` | Digit / word char / whitespace |
| `\D` `\W` `\S` | NOT digit / word char / whitespace |
| `.` | Any single character |
| `^` / `$` | Start / end of string |
| `*` | 0 or more times |
| `+` | 1 or more times |
| `?` | 0 or 1 time (optional) |
| `{2,4}` | Between 2 and 4 times |
| `[abc]` | Any one of a, b, c |
| `[^abc]` | Anything EXCEPT a, b, c |
| `[a-z]` | Range a to z |
| `(x|y)` | x OR y; parentheses also capture groups |
| Flags: `g` `i` `m` | Global (all matches) / ignore case / multiline |

### Using Regex
| Syntax | Meaning |
|---|---|
| `regex.test(str)` | `true`/`false` — does it match? |
| `str.match(regex)` | Get matches |
| `str.matchAll(regex)` | All matches with details (needs `g`) |
| `str.replace(regex, "new")` | Replace matches |
| `str.search(regex)` | Index of first match |
| `str.split(regex)` | Split by pattern |

Example: `/^\S+@\S+\.\S+$/.test(email)` → simple email check

---

## 31. Date & Time

| Syntax | Meaning |
|---|---|
| `new Date()` | Current date & time |
| `new Date("2026-07-06")` | From date string |
| `new Date(2026, 6, 6)` | Year, month (0-based! 6 = July), day |
| `Date.now()` | Current timestamp in milliseconds |
| `d.getFullYear()` | 2026 |
| `d.getMonth()` | 0–11 ⚠️ (January = 0) |
| `d.getDate()` | Day of month (1–31) |
| `d.getDay()` | Day of week (0 = Sunday) |
| `d.getHours()` / `getMinutes()` / `getSeconds()` | Time parts |
| `d.getTime()` | Timestamp (ms since 1970) |
| `d.setFullYear(2030)` | Change parts (set* versions exist for all) |
| `d.toISOString()` | `"2026-07-06T10:30:00.000Z"` |
| `d.toLocaleDateString("en-IN")` | `"6/7/2026"` — local format |
| `d.toLocaleTimeString()` | Local time format |
| `date2 - date1` | Difference in milliseconds |

---

## 32. Advanced Concepts

### Execution Context & Call Stack
Each function call creates a "context" pushed onto the **call stack**; popped off when done. Too many nested calls = *stack overflow*.

### Shallow vs Deep Copy
| Copy | Meaning |
|---|---|
| Shallow (`{...obj}`, `Object.assign`) | Top level copied; **nested objects still shared** ⚠️ |
| Deep (`structuredClone(obj)`) | Everything copied — fully independent ✅ |

### Pure Functions & Immutability
- **Pure function:** same input → same output, changes nothing outside itself ✅
- **Immutability:** don't modify data; create updated copies (`map`, `filter`, spread)

### Higher-Order Functions
Functions that **take** or **return** other functions (`map`, `filter`, event listeners are all HOFs).

### Currying
Turning `f(a, b)` into `f(a)(b)` — each call takes one argument.
```js
const add = a => b => a + b;
add(2)(3); // 5
```

### Debounce & Throttle (performance patterns)
| Pattern | Meaning |
|---|---|
| Debounce | Wait until user STOPS (e.g., search box — run after typing pauses) |
| Throttle | Run at most once per interval (e.g., scroll handler) |

### Memoization — cache results of expensive functions
```js
const cache = {};
function slowSquare(n) {
  if (n in cache) return cache[n];    // return saved answer
  return cache[n] = n * n;            // compute once, save
}
```

### Garbage Collection
JS automatically frees memory for values no longer reachable. Avoid leaks: clear intervals, remove unused listeners.

### Proxy & Reflect (meta-programming)
| Syntax | Meaning |
|---|---|
| `new Proxy(obj, handler)` | Intercept operations on an object (get, set...) |
| `handler = { get(t, key) {...} }` | Custom behavior when reading properties |
| `Reflect.get(obj, key)` | Standard functions for object operations |

### Web APIs Worth Knowing
| API | Purpose |
|---|---|
| `navigator.geolocation` | User's location |
| `IntersectionObserver` | Detect element visible on screen (lazy loading) |
| `MutationObserver` | Watch DOM changes |
| `Web Workers` | Run JS in background thread |
| `requestAnimationFrame(fn)` | Smooth animations |
| `navigator.clipboard.writeText(x)` | Copy to clipboard |
| `history.pushState()` | Change URL without reload (SPA routing) |

---

## 33. Modern Operators (ES2020+)

| Syntax | Meaning |
|---|---|
| `a ?? b` | Nullish coalescing — b only if a is `null`/`undefined` (unlike `\|\|`, keeps `0` and `""`) |
| `a ??= b` | Assign b only if a is null/undefined |
| `a \|\|= b` | Assign b only if a is falsy |
| `a &&= b` | Assign b only if a is truthy |
| `obj?.prop` | Optional chaining — safe access, no crash |
| `arr.at(-1)` | Negative indexing |
| `Object.hasOwn(obj, "key")` | Modern own-property check |
| `123_456_789` | Numeric separators for readability |
| `arr.toSorted() / toReversed() / toSpliced() / with()` | Non-mutating array copies (ES2023) |
| `Object.groupBy(arr, fn)` | Group array items into an object (ES2024) |
| `Promise.withResolvers()` | Get promise + resolve + reject together (ES2024) |

---

## 34. Strict Mode & Best Practices

| Practice | Why |
|---|---|
| `"use strict";` | Catches silent errors (auto-on in modules & classes) |
| Use `const` by default, `let` if needed, never `var` | Prevents accidental bugs |
| Always `===` and `!==` | Avoid weird type coercion |
| Prefer `map/filter/reduce` over manual loops | Cleaner, no mutation |
| Use template literals over `+` concatenation | Readable |
| Use `async/await` over `.then()` chains | Readable async code |
| Use `textContent` unless you truly need `innerHTML` | Prevents XSS attacks |
| Name things clearly (`getUserById` not `gub`) | Future-you will thank you |
| Handle errors: `try/catch` + check `res.ok` | Apps shouldn't crash silently |
| Keep functions small — one job each | Easy to test & reuse |

---

## 🗺️ Suggested Learning Path

1. **Basics** → Sections 1–7 (variables, types, operators, conditions, loops)
2. **Core** → Sections 8–13 (functions, strings, arrays, objects, destructuring)
3. **Deep JS** → Sections 14–18 (scope, closures, `this`, classes, errors)
4. **Async & Web** → Sections 19–26 (JSON, promises, fetch, DOM, events, storage, modules)
5. **Advanced** → Sections 27–34 (Map/Set, generators, regex, patterns, modern features)

*Practice each section by building tiny projects: calculator → todo list → quiz app → weather app (fetch) → notes app (localStorage).*

📚 Full reference: [developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
