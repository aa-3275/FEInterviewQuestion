# 🚀 Frontend Developer Interview Preparation Guide
### 150+ Questions with Answers | L1 → L3 Levels | HTML · CSS · SCSS · JS · React

---

## 📌 APPROACH TO START WITH

Before diving into questions, follow this structured roadmap:

### Week 1–2: Foundation
- Revise **HTML semantics**, accessibility, forms, media
- Master **CSS box model**, flexbox, grid, specificity, pseudo-selectors
- Brush up **JavaScript fundamentals**: data types, hoisting, closures, scope

### Week 3–4: Intermediate
- Deep-dive into **ES6+**: promises, async/await, destructuring, spread/rest, modules
- Practice **React core**: hooks, lifecycle, props vs state, controlled vs uncontrolled
- Understand **CSS architecture** with SCSS: variables, mixins, nesting, BEM

### Week 5–6: Advanced + Problem Solving
- Study **performance optimization**, lazy loading, memoization, code splitting
- Practice **debugging scenarios** (network tab, console, React DevTools)
- Solve **coding problems** on LeetCode (Easy → Medium, array/string heavy)

### Interview Day Tips
1. **Think aloud** — interviewers value your reasoning process
2. **Clarify requirements** before coding
3. For UI rounds: start with HTML structure → CSS layout → JS behavior
4. For debugging: read errors top-to-bottom, check network tab, isolate the issue
5. Know **why** you chose one approach over another

---

# ═══════════════════════════════════════
# LEVEL 1 (L1) — JUNIOR / 0–2 YRS
# ═══════════════════════════════════════
> *Asked at: Product startups, service companies, junior screening rounds*

---

## 🔷 HTML — L1

### Q1. What is the difference between `<div>` and `<span>`?

**Answer:**
- `<div>` is a **block-level** element — takes full width, starts on a new line. Used for layout sections.
- `<span>` is an **inline** element — takes only the space it needs. Used for styling parts of text.

```html
<div>This is a block</div>
<span>This is inline</span>
```

---

### Q2. What are semantic HTML elements? Give examples.

**Answer:**
Semantic elements clearly describe their meaning to both browser and developer.

Examples: `<header>`, `<footer>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<figure>`, `<time>`

Non-semantic: `<div>`, `<span>` (tell nothing about content)

**Why it matters:** Improves accessibility (screen readers), SEO, and code readability.

---

### Q3. What is the difference between `id` and `class` attributes?

**Answer:**
- `id` — Unique per page. Used for targeting specific elements. Higher CSS specificity.
- `class` — Can be reused on multiple elements. Used for shared styling.

```html
<div id="header">Unique Header</div>
<div class="card">Card 1</div>
<div class="card">Card 2</div>
```

---

### Q4. What is the `alt` attribute in `<img>` and why is it important?

**Answer:**
`alt` provides alternative text for an image when it cannot be displayed.

```html
<img src="logo.png" alt="Company Logo" />
```

**Importance:**
- Accessibility: Screen readers read the `alt` text
- SEO: Helps search engines understand images
- Fallback: Displayed when image fails to load

---

### Q5. What is the difference between `<script>`, `<script async>`, and `<script defer>`?

**Answer:**

| Attribute | Parsing | Execution |
|-----------|---------|-----------|
| (none) | HTML pauses while script downloads & runs | Blocking |
| `async` | HTML continues parsing; script runs immediately when downloaded | Non-blocking, order not guaranteed |
| `defer` | HTML continues parsing; script runs after DOM is ready | Non-blocking, order preserved |

```html
<script src="app.js" defer></script>
```

Best practice: Use `defer` for most scripts, `async` for analytics/ads.

---

### Q6. What is the difference between `<link>` and `<a>` tags?

**Answer:**
- `<link>` — Used in `<head>` to link external resources (CSS, fonts, icons). Not visible.
- `<a>` — Anchor tag used for navigation, creates clickable hyperlinks in content.

```html
<link rel="stylesheet" href="style.css" />  <!-- In head -->
<a href="/about">About Us</a>              <!-- In body -->
```

---

### Q7. What are data attributes (`data-*`)? When would you use them?

**Answer:**
Custom attributes that store extra information on HTML elements without using non-standard attributes.

```html
<button data-user-id="42" data-role="admin">Delete</button>
```

```js
const btn = document.querySelector('button');
console.log(btn.dataset.userId); // "42"
```

Use cases: Passing IDs to JS, toggling UI behavior, storing config values.

---

### Q8. What is the difference between `GET` and `POST` in HTML forms?

**Answer:**
- `GET` — Appends data to URL as query string. Visible in URL, bookmarkable, limited size. Use for search/filters.
- `POST` — Sends data in request body. Not visible in URL, no size limit. Use for login/signup.

```html
<form method="POST" action="/login">
  <input type="email" name="email" />
</form>
```

---

## 🔷 CSS — L1

### Q9. Explain the CSS Box Model.

**Answer:**
Every element is a rectangular box with 4 layers (outside to inside):

```
┌──────────────────────────────┐
│            Margin            │
│  ┌────────────────────────┐  │
│  │        Border          │  │
│  │  ┌──────────────────┐  │  │
│  │  │     Padding      │  │  │
│  │  │  ┌────────────┐  │  │  │
│  │  │  │  Content   │  │  │  │
│  │  │  └────────────┘  │  │  │
│  │  └──────────────────┘  │  │
│  └────────────────────────┘  │
└──────────────────────────────┘
```

- **`content-box`** (default): `width` = content only
- **`border-box`**: `width` includes padding + border (recommended)

```css
* { box-sizing: border-box; }
```

---

### Q10. What is CSS specificity? How is it calculated?

**Answer:**
Specificity determines which CSS rule wins when multiple rules target the same element.

| Selector | Specificity Value |
|----------|------------------|
| Inline style | 1,0,0,0 |
| ID `#id` | 0,1,0,0 |
| Class `.class`, `:hover`, `[attr]` | 0,0,1,0 |
| Element `div`, `p` | 0,0,0,1 |
| `*` (universal) | 0,0,0,0 |

```css
/* specificity: 0,0,1,1 */
p.intro { color: blue; }

/* specificity: 0,1,0,0 — wins */
#main { color: red; }
```

`!important` overrides everything (use sparingly).

---

### Q11. What is the difference between `display: none` and `visibility: hidden`?

**Answer:**
- `display: none` — Element is removed from the DOM flow. Takes no space.
- `visibility: hidden` — Element is invisible but still occupies space in layout.
- `opacity: 0` — Invisible but occupies space and responds to events.

```css
.hidden-none { display: none; }       /* Gone from layout */
.hidden-vis  { visibility: hidden; }  /* Invisible, space preserved */
```

---

### Q12. Explain Flexbox. What are the main properties?

**Answer:**
Flexbox is a one-dimensional layout model for arranging items in a row or column.

```css
.container {
  display: flex;
  flex-direction: row;       /* row | column | row-reverse | column-reverse */
  justify-content: center;   /* Align along main axis */
  align-items: center;       /* Align along cross axis */
  flex-wrap: wrap;           /* Allow wrapping */
  gap: 16px;                 /* Space between items */
}

.item {
  flex: 1;                   /* flex-grow: 1, flex-shrink: 1, flex-basis: 0 */
  align-self: flex-end;      /* Override align-items for this item */
}
```

---

### Q13. What is the difference between `position: relative`, `absolute`, `fixed`, and `sticky`?

**Answer:**

| Value | Reference Point | Scrolls? | Removes from flow? |
|-------|----------------|----------|--------------------|
| `relative` | Its own original position | Yes | No |
| `absolute` | Nearest positioned ancestor | Yes | Yes |
| `fixed` | Viewport | No | Yes |
| `sticky` | Nearest scrollable ancestor | Partially | No |

```css
.parent { position: relative; }
.tooltip { position: absolute; top: 0; right: 0; } /* relative to .parent */
.navbar  { position: sticky; top: 0; }              /* sticks at top while scrolling */
```

---

### Q14. What are CSS pseudo-classes and pseudo-elements? Give examples.

**Answer:**
- **Pseudo-class** — Styles an element in a specific state (`:hover`, `:focus`, `:nth-child()`, `:not()`)
- **Pseudo-element** — Styles a specific part of an element (`::before`, `::after`, `::first-line`)

```css
a:hover { color: blue; }               /* Pseudo-class */
p::first-line { font-weight: bold; }   /* Pseudo-element */
.btn::after { content: " →"; }         /* Inject content */
```

---

### Q15. What is the difference between `em`, `rem`, `px`, `vh`, and `vw`?

**Answer:**

| Unit | Relative To |
|------|-------------|
| `px` | Fixed pixel value |
| `em` | Parent element's font-size |
| `rem` | Root (`html`) element's font-size |
| `vh` | 1% of viewport height |
| `vw` | 1% of viewport width |
| `%` | Parent element's dimension |

```css
html { font-size: 16px; }
h1   { font-size: 2rem; }    /* 32px */
p    { font-size: 1.2em; }   /* 1.2 × parent's font-size */
.hero{ height: 100vh; }      /* Full viewport height */
```

---

## 🔷 SCSS — L1

### Q16. What is SCSS? How is it different from plain CSS?

**Answer:**
SCSS (Sassy CSS) is a CSS preprocessor that adds programming features to CSS. It compiles to plain CSS.

Key features over CSS:
- Variables (`$primary-color: #333`)
- Nesting
- Mixins (reusable code blocks)
- Inheritance (`@extend`)
- Partials and imports

---

### Q17. How do SCSS variables work? Show an example.

**Answer:**
```scss
// _variables.scss
$primary-color: #3498db;
$font-size-base: 16px;
$border-radius: 4px;

// usage
.button {
  background-color: $primary-color;
  font-size: $font-size-base;
  border-radius: $border-radius;
}
```

CSS variables (`--var`) are native, runtime; SCSS variables are compile-time.

---

### Q18. What is nesting in SCSS? Show an example.

**Answer:**
SCSS allows you to nest selectors inside other selectors, mirroring the HTML structure.

```scss
.navbar {
  background: #333;
  
  ul {
    list-style: none;
    margin: 0;
  }
  
  li {
    display: inline-block;
  }
  
  a {
    color: white;
    
    &:hover {
      color: #ddd;  // & refers to parent selector
    }
  }
}
```

⚠️ Avoid nesting more than 3 levels deep — it increases specificity and reduces readability.

---

## 🔷 JavaScript — L1

### Q19. What are the different data types in JavaScript?

**Answer:**
**Primitive types** (7):
- `string`, `number`, `bigint`, `boolean`, `undefined`, `null`, `symbol`

**Reference type** (1):
- `object` (includes arrays, functions, dates)

```js
typeof "hello"      // "string"
typeof 42           // "number"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object" ← famous bug
typeof {}           // "object"
typeof []           // "object"
typeof function(){} // "function"
```

---

### Q20. What is the difference between `==` and `===`?

**Answer:**
- `==` (loose equality) — Compares values after **type coercion**
- `===` (strict equality) — Compares values **and types** (no coercion)

```js
0 == false    // true  (false coerces to 0)
0 === false   // false (different types)
"" == false   // true
"" === false  // false
null == undefined  // true
null === undefined // false
```

**Best practice:** Always use `===` to avoid unexpected bugs.

---

### Q21. What is `var`, `let`, and `const`? What are their differences?

**Answer:**

| | `var` | `let` | `const` |
|--|-------|-------|---------|
| Scope | Function | Block | Block |
| Hoisting | Yes (as `undefined`) | Yes (TDZ) | Yes (TDZ) |
| Re-declare | Yes | No | No |
| Re-assign | Yes | Yes | No |

```js
var x = 1;  // function-scoped, hoisted
let y = 2;  // block-scoped
const z = 3; // block-scoped, can't reassign

// const with objects — reference is const, not the value
const obj = { a: 1 };
obj.a = 2;   // ✅ allowed
obj = {};    // ❌ TypeError
```

---

### Q22. What is hoisting in JavaScript?

**Answer:**
Hoisting is JS's behavior of moving variable and function **declarations** to the top of their scope during compilation.

```js
// Function declarations are fully hoisted
greet(); // ✅ "Hello"
function greet() { console.log("Hello"); }

// var is hoisted but initialized as undefined
console.log(x); // undefined (not error)
var x = 5;

// let/const are hoisted but in Temporal Dead Zone (TDZ)
console.log(y); // ❌ ReferenceError
let y = 10;
```

---

### Q23. What is a closure in JavaScript?

**Answer:**
A closure is a function that **remembers** the variables from its outer scope even after that outer scope has finished executing.

```js
function counter() {
  let count = 0;           // Outer variable
  return function() {
    count++;
    return count;          // Inner function "closes over" count
  };
}

const increment = counter();
increment(); // 1
increment(); // 2
increment(); // 3
// count is not accessible outside, but persists!
```

**Real use cases:** Data privacy, factory functions, memoization, event handlers.

---

### Q24. What is the difference between `null` and `undefined`?

**Answer:**
- `undefined` — Variable declared but not assigned. Default value of uninitialized variables, missing function args, missing object properties.
- `null` — Intentional absence of a value. Must be explicitly assigned.

```js
let a;               // undefined
let b = null;        // null (intentional empty)

function foo(x) {
  console.log(x);    // undefined if not passed
}

const obj = { name: "Alice" };
console.log(obj.age); // undefined — property doesn't exist
```

---

### Q25. What is `typeof` operator? List some quirks.

**Answer:**
```js
typeof 42           // "number"
typeof "hello"      // "string"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof Symbol()     // "symbol"
typeof function(){} // "function"

// Quirks
typeof null         // "object" ← historical bug, null is not an object
typeof []           // "object" ← use Array.isArray() instead
typeof NaN          // "number" ← NaN is technically a number type
```

---

## 🔷 React — L1

### Q26. What is React? Why use it?

**Answer:**
React is a JavaScript library (not a framework) for building **user interfaces**, developed by Meta. It uses a component-based architecture.

**Key benefits:**
- **Virtual DOM** for efficient re-rendering
- **Component reusability** — build once, use everywhere
- **Unidirectional data flow** — predictable state management
- Large **ecosystem** (React Router, Redux, etc.)
- **JSX** — HTML-like syntax in JavaScript

---

### Q27. What is JSX?

**Answer:**
JSX (JavaScript XML) is a syntax extension that allows you to write HTML-like code inside JavaScript.

```jsx
// JSX
const element = <h1 className="title">Hello, World!</h1>;

// Compiles to:
const element = React.createElement('h1', { className: 'title' }, 'Hello, World!');
```

Rules:
- Must return a **single root element** (or Fragment `<>`)
- Use `className` instead of `class`
- Self-close empty tags: `<img />`, `<br />`
- JS expressions inside `{}`

---

### Q28. What is the difference between props and state?

**Answer:**

| | Props | State |
|--|-------|-------|
| Ownership | Passed by parent | Managed within component |
| Mutable? | Read-only | Mutable via setter |
| Re-renders? | Yes, when parent changes | Yes, when updated |

```jsx
// Props — passed from parent
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

// State — internal
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

---

### Q29. What are React Hooks? Name the commonly used ones.

**Answer:**
Hooks are functions that let you "hook into" React state and lifecycle from **functional components**.

| Hook | Purpose |
|------|---------|
| `useState` | Local state management |
| `useEffect` | Side effects (API calls, subscriptions) |
| `useContext` | Consume React context |
| `useRef` | Access DOM elements, persist values without re-render |
| `useMemo` | Memoize expensive computations |
| `useCallback` | Memoize functions |
| `useReducer` | Complex state logic |

Rules of Hooks:
1. Only call at the **top level** (not inside loops/conditions)
2. Only call from **React functions** (components or custom hooks)

---

### Q30. What does `useState` return and how do you use it?

**Answer:**
`useState` returns an array of `[currentValue, setterFunction]`.

```jsx
import { useState } from 'react';

function App() {
  const [name, setName] = useState('');         // string state
  const [count, setCount] = useState(0);        // number state
  const [user, setUser] = useState(null);       // object/null state

  return (
    <div>
      <input value={name} onChange={e => setName(e.target.value)} />
      <button onClick={() => setCount(prev => prev + 1)}>
        Count: {count}
      </button>
    </div>
  );
}
```

Use the **functional update form** `setCount(prev => prev + 1)` when new state depends on old state.

---

# ═══════════════════════════════════════
# LEVEL 2 (L2) — MID-LEVEL / 2–5 YRS
# ═══════════════════════════════════════
> *Asked at: Product companies, FAANG subsidiaries, Series A/B startups*

---

## 🔷 JavaScript — L2

### Q31. Explain the Event Loop in JavaScript.

**Answer:**
JavaScript is **single-threaded** but handles async operations via the Event Loop.

```
Call Stack → Web APIs → Callback Queue → Event Loop → Call Stack
```

1. **Call Stack**: Executes synchronous code
2. **Web APIs**: Handle async (setTimeout, fetch, DOM events)
3. **Callback Queue** (Macrotask): setTimeout, setInterval callbacks
4. **Microtask Queue**: Promises (`.then`), `queueMicrotask`, `MutationObserver`
5. **Event Loop**: Continuously checks if call stack is empty, then processes **microtasks first**, then one macrotask

```js
console.log('1');
setTimeout(() => console.log('2'), 0);
Promise.resolve().then(() => console.log('3'));
console.log('4');
// Output: 1, 4, 3, 2
```

Microtasks always run before the next macrotask.

---

### Q32. What is the difference between `call`, `apply`, and `bind`?

**Answer:**
All three set the `this` context explicitly.

```js
const person = { name: 'Alice' };

function greet(city, country) {
  console.log(`${this.name} from ${city}, ${country}`);
}

// call — invoke immediately, args as comma-separated
greet.call(person, 'Mumbai', 'India');

// apply — invoke immediately, args as array
greet.apply(person, ['Mumbai', 'India']);

// bind — returns NEW function with this bound, invoke later
const greetAlice = greet.bind(person, 'Mumbai');
greetAlice('India'); // invoke later
```

---

### Q33. What are Promises? How do you handle multiple promises?

**Answer:**
A Promise represents a value that may be available now, in the future, or never.

States: `pending` → `fulfilled` or `rejected`

```js
const fetchUser = () => new Promise((resolve, reject) => {
  fetch('/api/user')
    .then(res => res.json())
    .then(resolve)
    .catch(reject);
});

// Sequential
const result = await fetchUser();

// Parallel (all must succeed)
const [users, posts] = await Promise.all([fetchUsers(), fetchPosts()]);

// Parallel (first to settle)
const first = await Promise.race([fast(), slow()]);

// Parallel (all settle, get results regardless of failure)
const results = await Promise.allSettled([fetchA(), fetchB()]);

// First successful
const first = await Promise.any([fetchA(), fetchB()]);
```

---

### Q34. Explain `async/await`. How does it differ from Promises?

**Answer:**
`async/await` is **syntactic sugar** over Promises. It makes async code look and behave like synchronous code.

```js
// Promise chain
function loadData() {
  return fetch('/api')
    .then(res => res.json())
    .then(data => process(data))
    .catch(err => handleError(err));
}

// Same with async/await — cleaner!
async function loadData() {
  try {
    const res = await fetch('/api');
    const data = await res.json();
    return process(data);
  } catch (err) {
    handleError(err);
  }
}
```

Differences:
- `async/await` is cleaner for sequential async operations
- Both still use Promise under the hood
- Error handling via `try/catch` instead of `.catch()`

---

### Q35. What is the difference between deep copy and shallow copy?

**Answer:**

**Shallow copy** — copies only the top-level properties. Nested objects are still referenced.

```js
const original = { a: 1, b: { c: 2 } };

// Shallow copies
const copy1 = { ...original };
const copy2 = Object.assign({}, original);

copy1.b.c = 99;
console.log(original.b.c); // 99 — original mutated!
```

**Deep copy** — copies all nested levels, fully independent.

```js
// Deep copies
const deep1 = JSON.parse(JSON.stringify(original)); // loses functions, Date, undefined
const deep2 = structuredClone(original);            // modern, best practice
```

---

### Q36. What is prototypal inheritance in JavaScript?

**Answer:**
Every JS object has an internal `[[Prototype]]` link. When you access a property, JS first looks at the object itself, then up the prototype chain.

```js
const animal = {
  speak() { console.log(`${this.name} makes a sound`); }
};

const dog = Object.create(animal);
dog.name = 'Rex';
dog.speak(); // "Rex makes a sound" — inherited from animal

// With classes (syntactic sugar over prototype chain)
class Animal {
  constructor(name) { this.name = name; }
  speak() { console.log(`${this.name} makes a sound`); }
}

class Dog extends Animal {
  speak() { console.log(`${this.name} barks`); }
}
```

---

### Q37. What are JavaScript Generators?

**Answer:**
Generators are functions that can be paused and resumed. They use `function*` syntax and `yield`.

```js
function* idGenerator() {
  let id = 1;
  while (true) {
    yield id++;
  }
}

const gen = idGenerator();
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3
```

Use cases: Lazy evaluation, infinite sequences, async control flow, state machines.

---

### Q38. What is debouncing and throttling?

**Answer:**

**Debounce** — Waits until the user *stops* performing an action before firing. Resets timer on each call.

```js
function debounce(fn, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}
// Use case: search input (fire only after user stops typing)
const onSearch = debounce(fetchResults, 300);
```

**Throttle** — Fires at most once every X milliseconds, regardless of how often called.

```js
function throttle(fn, limit) {
  let lastCall = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      fn.apply(this, args);
    }
  };
}
// Use case: scroll events, resize events
```

---

### Q39. What is `this` in JavaScript? Explain different contexts.

**Answer:**

| Context | Value of `this` |
|---------|----------------|
| Global scope | `window` (browser) / `global` (Node) |
| Regular function | `window` (non-strict) / `undefined` (strict mode) |
| Method call | The object that called the method |
| Arrow function | Inherited from enclosing lexical scope |
| `new` keyword | Newly created object |
| `call/apply/bind` | Explicitly set |

```js
const obj = {
  name: 'Alice',
  greet() { console.log(this.name); },  // 'Alice'
  greetArrow: () => { console.log(this.name); }  // undefined (lexical)
};

// Arrow functions DON'T have their own this
const timer = {
  seconds: 0,
  start() {
    setInterval(() => {
      this.seconds++;  // 'this' = timer object ✅
    }, 1000);
  }
};
```

---

### Q40. Explain the `spread` and `rest` operators.

**Answer:**
Both use `...` syntax but in different positions.

```js
// SPREAD — expands an iterable
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];   // [1, 2, 3, 4, 5]

const obj1 = { a: 1 };
const obj2 = { ...obj1, b: 2 }; // { a: 1, b: 2 }

Math.max(...arr1);               // 3 — spread as args

// REST — collects remaining elements
function sum(...numbers) {       // rest params
  return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4); // 10

const [first, ...rest] = [1, 2, 3, 4];
// first = 1, rest = [2, 3, 4]

const { a, ...others } = { a: 1, b: 2, c: 3 };
// a = 1, others = { b: 2, c: 3 }
```

---

## 🔷 CSS — L2

### Q41. Explain CSS Grid. How is it different from Flexbox?

**Answer:**
CSS Grid is a **2-dimensional** layout system (rows AND columns).
Flexbox is **1-dimensional** (row OR column).

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);   /* 3 equal columns */
  grid-template-rows: auto 200px;
  grid-template-areas:
    "header header header"
    "sidebar main main";
  gap: 16px;
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }

/* Spanning */
.wide { grid-column: 1 / span 2; }
```

**When to use:**
- Grid: Full-page layouts, card grids, complex 2D arrangements
- Flexbox: Navigation bars, centering, single-row/column components

---

### Q42. What is CSS specificity conflict resolution? What is `!important`?

**Answer:**
When two rules target the same element with equal specificity, the **last declared** rule wins (cascade).

```css
/* Both have specificity 0,0,1,0 */
.red { color: red; }
.blue { color: blue; }  /* This wins if applied second in source */
```

`!important` overrides ALL other declarations (including inline styles):
```css
p { color: blue !important; } /* Always wins, avoid using it */
```

Specificity order (highest to lowest):
1. `!important`
2. Inline styles
3. IDs
4. Classes, pseudo-classes, attribute selectors
5. Elements, pseudo-elements

---

### Q43. What are CSS custom properties (variables)?

**Answer:**
Native CSS variables that work at runtime (unlike SCSS variables).

```css
:root {
  --primary: #3498db;
  --font-size: 16px;
  --spacing: 8px;
}

.button {
  background: var(--primary);
  font-size: var(--font-size);
  padding: calc(var(--spacing) * 2);
}

/* Override in a scope */
.dark-theme {
  --primary: #1a73e8;
}
```

CSS variables are **dynamic** (can be changed with JS), SCSS variables are **compiled away**.

---

### Q44. What is BEM methodology in CSS?

**Answer:**
BEM (Block, Element, Modifier) is a CSS naming convention for maintainable, scalable styles.

```
Block__Element--Modifier
```

```html
<div class="card card--featured">
  <h2 class="card__title">Product Name</h2>
  <p class="card__description">Description...</p>
  <button class="card__button card__button--primary">Buy Now</button>
</div>
```

```css
.card { }                           /* Block */
.card--featured { }                 /* Block Modifier */
.card__title { }                    /* Element */
.card__button { }                   /* Element */
.card__button--primary { }          /* Element Modifier */
```

Benefits: Self-documenting, avoids deep nesting, prevents specificity conflicts.

---

### Q45. What is the `z-index` and stacking context?

**Answer:**
`z-index` controls the stacking order of **positioned** elements (not `position: static`).

A **stacking context** is created by:
- `position` + `z-index` (other than auto)
- `opacity < 1`
- `transform`, `filter`, `will-change`
- `isolation: isolate`

```css
/* z-index only works on positioned elements */
.modal    { position: fixed; z-index: 1000; }
.overlay  { position: fixed; z-index: 999; }
.header   { position: sticky; z-index: 100; }

/* Elements in the same stacking context are compared by z-index */
/* Child elements cannot escape their parent stacking context */
.parent { position: relative; z-index: 1; }
.child  { z-index: 9999; } /* Still below elements with z-index: 2 outside parent */
```

---

## 🔷 SCSS — L2

### Q46. What are SCSS mixins? How do they differ from functions?

**Answer:**

**Mixins** — Reusable blocks of CSS declarations (output CSS rules)

```scss
@mixin flex-center($direction: row) {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: $direction;
}

.hero     { @include flex-center(column); }
.nav-item { @include flex-center(); }
```

**Functions** — Return a single computed value (not CSS declarations)

```scss
@function rem($px) {
  @return $px / 16px * 1rem;
}

.title { font-size: rem(24px); } // 1.5rem
```

---

### Q47. What is `@extend` in SCSS? When should you avoid it?

**Answer:**
`@extend` lets one selector inherit styles from another.

```scss
%button-base {           // Placeholder — won't compile on its own
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
}

.btn-primary {
  @extend %button-base;
  background: blue;
}

.btn-secondary {
  @extend %button-base;
  background: gray;
}
```

⚠️ **When to avoid:** Extending non-placeholder selectors can bloat CSS and create unexpected selectors. Use `@include` with mixins instead for complex scenarios.

---

### Q48. Explain SCSS partials and the `@use` rule.

**Answer:**
**Partials** — SCSS files prefixed with `_` (not compiled on their own). Used to modularize styles.

```
styles/
  _variables.scss
  _mixins.scss
  _buttons.scss
  main.scss     ← compiled
```

```scss
// main.scss — modern way with @use
@use 'variables' as vars;
@use 'mixins';

.button {
  color: vars.$primary-color;
  @include mixins.flex-center();
}
```

`@use` is preferred over the older `@import` because it:
- Scopes variables/functions to avoid naming collisions
- Loads each file only once
- Encourages modular architecture

---

## 🔷 React — L2

### Q49. Explain `useEffect` with examples. What are the dependency array rules?

**Answer:**
`useEffect` runs side effects after render.

```jsx
// Runs after EVERY render
useEffect(() => { console.log('rendered'); });

// Runs ONCE on mount (componentDidMount)
useEffect(() => {
  fetchData();
}, []);

// Runs when specific deps change
useEffect(() => {
  document.title = `Count: ${count}`;
}, [count]);

// Cleanup (componentWillUnmount equivalent)
useEffect(() => {
  const timer = setInterval(() => tick(), 1000);
  return () => clearInterval(timer); // Cleanup!
}, []);
```

**Dependency rules:**
- Include all reactive values used inside the effect
- ESLint `react-hooks/exhaustive-deps` rule helps enforce this
- Omitting deps can cause stale closures

---

### Q50. What is the Virtual DOM and how does React's reconciliation work?

**Answer:**
The **Virtual DOM** is a lightweight JS representation of the actual DOM.

**How it works:**
1. On state/prop change, React creates a new Virtual DOM tree
2. **Diffing algorithm** compares new vs. old Virtual DOM (O(n) complexity)
3. Only the actual **changed nodes** are updated in the real DOM (**reconciliation**)

**Keys in lists** help React identify which items changed:
```jsx
// ❌ Bad — React can't efficiently diff
{items.map((item, index) => <li key={index}>{item.name}</li>)}

// ✅ Good — stable, unique key
{items.map(item => <li key={item.id}>{item.name}</li>)}
```

---

### Q51. What is the difference between `useMemo` and `useCallback`?

**Answer:**

**`useMemo`** — Memoizes the **result of a computation**

```jsx
const sortedList = useMemo(() => {
  return [...items].sort((a, b) => a.name.localeCompare(b.name));
}, [items]); // Only re-sorts when items changes
```

**`useCallback`** — Memoizes a **function reference**

```jsx
const handleClick = useCallback((id) => {
  deleteItem(id);
}, [deleteItem]); // Stable reference for child components

// Without useCallback, handleClick is new on every render
// With useCallback, child components won't re-render unnecessarily
```

**When to use:**
- `useMemo`: Expensive calculations, object/array references passed as props
- `useCallback`: Passing callbacks to optimized child components (`React.memo`)

---

### Q52. What is Context API? When would you use it over prop drilling?

**Answer:**
Context provides a way to share values between components without explicitly passing props through every level.

```jsx
// 1. Create context
const ThemeContext = createContext('light');

// 2. Provide it
function App() {
  const [theme, setTheme] = useState('dark');
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Layout />
    </ThemeContext.Provider>
  );
}

// 3. Consume it (anywhere in the tree)
function Button() {
  const { theme } = useContext(ThemeContext);
  return <button className={theme}>Click</button>;
}
```

**Use Context for:** theme, auth state, language/locale, user preferences.

**Don't use for:** high-frequency updates, server data (use React Query/SWR instead).

---

### Q53. What is React.memo and when should you use it?

**Answer:**
`React.memo` is a HOC that prevents a functional component from re-rendering if its props haven't changed.

```jsx
// Without memo — re-renders every time parent renders
function ExpensiveComponent({ data }) {
  return <div>{/* complex rendering */}</div>;
}

// With memo — skips re-render if data is the same
const ExpensiveComponent = React.memo(function({ data }) {
  return <div>{/* complex rendering */}</div>;
});

// Custom comparison
const Component = React.memo(MyComp, (prevProps, nextProps) => {
  return prevProps.id === nextProps.id; // true = skip re-render
});
```

**Use when:**
- Component renders frequently with same props
- Component has expensive render logic
- Component receives stable prop references (use `useCallback/useMemo` for functions/objects)

---

### Q54. Explain React component lifecycle (both class and hooks equivalent).

**Answer:**

| Lifecycle Phase | Class Method | Hook Equivalent |
|----------------|-------------|-----------------|
| Mount | `componentDidMount` | `useEffect(() => {}, [])` |
| Update | `componentDidUpdate` | `useEffect(() => {}, [dep])` |
| Unmount | `componentWillUnmount` | `useEffect(() => { return cleanup; }, [])` |
| Render optimization | `shouldComponentUpdate` | `React.memo` / `useMemo` |
| Error catching | `componentDidCatch` | Error Boundary (still class-based) |

```jsx
// Full lifecycle with hooks
function MyComponent({ userId }) {
  const [user, setUser] = useState(null);
  
  useEffect(() => {
    // componentDidMount + componentDidUpdate
    fetchUser(userId).then(setUser);
    
    return () => {
      // componentWillUnmount cleanup
      cancelPendingRequests();
    };
  }, [userId]);
  
  return user ? <Profile user={user} /> : <Loading />;
}
```

---

# ═══════════════════════════════════════
# LEVEL 3 (L3) — SENIOR / 5+ YRS
# ═══════════════════════════════════════
> *Asked at: FAANG, unicorn startups, senior/lead engineering roles*

---

## 🔷 JavaScript — L3

### Q55. Explain JavaScript's memory management and garbage collection.

**Answer:**
JS automatically manages memory via **mark-and-sweep garbage collection**.

**Memory lifecycle:**
1. **Allocate** — Memory assigned when you create variables/objects
2. **Use** — Read/write operations
3. **Release** — GC reclaims unreachable memory

**Common memory leaks:**
```js
// 1. Global variables
function leak() { globalVar = 'this never gets collected'; }

// 2. Forgotten timers
const timer = setInterval(() => expensiveTask(), 1000);
// Must clearInterval(timer) when component unmounts

// 3. Closures holding large objects
function createHeavyMemory() {
  const largeData = new Array(1000000).fill('data');
  return function() { return largeData[0]; }; // largeData never GC'd
}

// 4. Detached DOM nodes
let el = document.getElementById('btn');
document.body.removeChild(el); // removed from DOM
// but el variable still references it — not GC'd until el = null
```

---

### Q56. What are WeakMap and WeakSet? When to use them?

**Answer:**
`WeakMap`/`WeakSet` hold **weak references** — they don't prevent garbage collection.

```js
// WeakMap — key must be an object
const cache = new WeakMap();

function processUser(user) {
  if (cache.has(user)) return cache.get(user);
  const result = expensiveOp(user);
  cache.set(user, result);      // When user is GC'd, this entry auto-removed
  return result;
}

// WeakSet — store objects without preventing GC
const visitedNodes = new WeakSet();
function traverse(node) {
  if (visitedNodes.has(node)) return;
  visitedNodes.add(node);
  // process node...
}
```

**Use cases:** Caching, DOM node metadata, tracking object state without memory leaks.

---

### Q57. What is the Proxy object in JavaScript?

**Answer:**
`Proxy` intercepts and customizes fundamental operations on objects.

```js
const handler = {
  get(target, prop) {
    console.log(`Getting ${prop}`);
    return prop in target ? target[prop] : `Property ${prop} not found`;
  },
  set(target, prop, value) {
    if (typeof value !== 'number') throw new TypeError('Only numbers allowed');
    target[prop] = value;
    return true;
  }
};

const obj = new Proxy({}, handler);
obj.age = 25;          // OK
obj.age = 'twenty';    // TypeError
console.log(obj.age);  // "Getting age" → 25
console.log(obj.name); // "Getting name" → "Property name not found"
```

**Real-world use:** Vue 3's reactivity system, data validation, logging, API mocking.

---

### Q58. What is tail call optimization (TCO)?

**Answer:**
TCO allows the JS engine to reuse the current stack frame for tail-recursive calls instead of creating a new one, preventing stack overflow.

```js
// Regular recursion — can cause stack overflow
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1); // Not a tail call — multiplication happens after
}

// Tail call — last operation is the recursive call
function factorialTCO(n, acc = 1) {
  if (n <= 1) return acc;
  return factorialTCO(n - 1, n * acc); // Tail call — nothing after this
}
```

Note: TCO is specified in ES6 but only Safari fully supports it. In practice, use iterative solutions for deep recursion.

---

## 🔷 CSS — L3

### Q59. What are CSS containment and `will-change`? How do they improve performance?

**Answer:**

**`contain`** — Isolates an element from the rest of the document for rendering optimizations.

```css
.card {
  contain: layout paint; /* Browser only needs to recalculate this box */
}
```
Values: `layout` (layout changes don't affect outside), `paint` (visuals don't bleed outside), `strict` (both + size).

**`will-change`** — Hints the browser to prepare a GPU layer in advance.

```css
.animated-element {
  will-change: transform; /* Browser pre-composites this layer */
}

/* Dynamically set only when needed */
element.addEventListener('mouseenter', () => {
  el.style.willChange = 'transform';
});
element.addEventListener('animationend', () => {
  el.style.willChange = 'auto'; // Reset!
});
```

⚠️ Don't overuse `will-change` — it consumes GPU memory. Apply only to actually animating elements.

---

### Q60. Explain Critical Rendering Path and how to optimize it.

**Answer:**
The CRP is the sequence of steps the browser takes to render a page:

```
HTML → DOM
CSS → CSSOM
DOM + CSSOM → Render Tree → Layout → Paint → Composite
```

**Optimizations:**
```html
<!-- 1. Inline critical CSS above the fold -->
<style>/* critical styles */</style>

<!-- 2. Defer non-critical CSS -->
<link rel="preload" href="styles.css" as="style" onload="this.rel='stylesheet'">

<!-- 3. Defer/async scripts -->
<script defer src="app.js"></script>

<!-- 4. Preload key resources -->
<link rel="preload" href="hero-font.woff2" as="font" crossorigin>
```

```css
/* 5. Avoid layout thrashing — batch reads/writes */
/* 6. Use transform/opacity for animations (compositor thread) */
.animate { transform: translateX(100px); } /* GPU composited */
/* vs */
.bad { left: 100px; } /* Triggers layout */
```

---

## 🔷 React — L3

### Q61. What is Concurrent Mode in React? What is `useTransition`?

**Answer:**
Concurrent Mode allows React to **interrupt** rendering to handle more urgent updates, keeping the UI responsive.

**`useTransition`** — Marks state updates as non-urgent, allowing React to defer them.

```jsx
import { useTransition, useState } from 'react';

function SearchPage() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);
  const [isPending, startTransition] = useTransition();

  function handleChange(e) {
    setQuery(e.target.value); // Urgent — update input immediately

    startTransition(() => {
      // Non-urgent — can be interrupted/deferred
      setResults(heavySearch(e.target.value));
    });
  }

  return (
    <div>
      <input value={query} onChange={handleChange} />
      {isPending ? <Spinner /> : <ResultsList results={results} />}
    </div>
  );
}
```

`useDeferredValue` — Similar but for deferring a derived value.

---

### Q62. How does React's reconciler (Fiber) work?

**Answer:**
React Fiber is the reconciliation engine introduced in React 16. It's a complete rewrite of the core algorithm.

**Key concepts:**
- **Fiber** — Lightweight JS object representing a unit of work (one component)
- **Work loop** — Processes fibers in small chunks, can be paused/resumed/aborted
- **Two phases:**
  1. **Render phase** (async, interruptible): Builds the Fiber tree, computes changes — no DOM mutations
  2. **Commit phase** (synchronous): Applies DOM mutations, runs effects

**Why it matters:**
- Enables time-slicing (Concurrent Mode)
- Supports `Suspense`, `useTransition`, streaming SSR
- Better prioritization of updates (user interactions > data fetching)

---

### Q63. What is Server-Side Rendering (SSR) vs. Static Site Generation (SSG) vs. Client-Side Rendering (CSR)?

**Answer:**

| | CSR | SSR | SSG |
|--|-----|-----|-----|
| Where rendered | Browser | Server per request | Build time |
| First paint | Slow | Fast | Fastest |
| SEO | Poor | Good | Excellent |
| Dynamic data | Yes | Yes | Limited |
| TTFB | Fast | Slower | Fastest |
| Example | Create React App | Next.js SSR | Next.js SSG, Gatsby |

```jsx
// Next.js SSR — runs on every request
export async function getServerSideProps() {
  const data = await fetchData();
  return { props: { data } };
}

// Next.js SSG — runs at build time
export async function getStaticProps() {
  const data = await fetchData();
  return { props: { data }, revalidate: 60 }; // ISR
}
```

ISR (Incremental Static Regeneration) — SSG pages that revalidate in the background.

---

### Q64. How do you optimize React performance in a large application?

**Answer:**

1. **Code splitting** with `React.lazy` + `Suspense`
```jsx
const LazyComponent = React.lazy(() => import('./HeavyComponent'));
<Suspense fallback={<Loading />}><LazyComponent /></Suspense>
```

2. **Memoization** — `React.memo`, `useMemo`, `useCallback`

3. **Virtualization** for long lists — `react-window`, `react-virtual`
```jsx
<FixedSizeList height={400} itemCount={10000} itemSize={50}>
  {Row}
</FixedSizeList>
```

4. **Avoid anonymous functions** in JSX (create new reference each render)
```jsx
// ❌ Bad
<Button onClick={() => handleClick(id)} />
// ✅ Good  
<Button onClick={handleClick} />
```

5. **Avoid premature optimization** — profile first with React DevTools Profiler

6. **State colocation** — keep state as low in the tree as possible

7. **Batch updates** — React 18 automatically batches all updates

---

# ═══════════════════════════════════════
# UI PROBLEMS
# ═══════════════════════════════════════

### Q65. Build a responsive navigation bar with hamburger menu.

**Answer:**
```html
<nav class="navbar">
  <div class="brand">Logo</div>
  <button class="hamburger" id="menu-toggle" aria-label="Toggle menu">☰</button>
  <ul class="nav-links" id="nav-links">
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>
```

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: #333;
}

.hamburger { display: none; color: white; font-size: 1.5rem; background: none; border: none; }

@media (max-width: 768px) {
  .hamburger { display: block; }
  .nav-links {
    display: none;
    flex-direction: column;
    width: 100%;
    position: absolute;
    top: 60px;
    left: 0;
    background: #333;
  }
  .nav-links.open { display: flex; }
}
```

```js
document.getElementById('menu-toggle').addEventListener('click', () => {
  document.getElementById('nav-links').classList.toggle('open');
});
```

---

### Q66. Create a CSS-only accordion component.

**Answer:**
```html
<div class="accordion">
  <input type="checkbox" id="section1" class="accordion-toggle">
  <label for="section1" class="accordion-header">Section 1</label>
  <div class="accordion-content">
    <p>Content for section 1...</p>
  </div>
</div>
```

```css
.accordion-toggle { display: none; }

.accordion-content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
}

.accordion-toggle:checked ~ .accordion-content {
  max-height: 500px; /* Large enough for content */
}

.accordion-header {
  cursor: pointer;
  padding: 1rem;
  background: #f0f0f0;
  display: block;
}

.accordion-header::after { content: ' +'; float: right; }
.accordion-toggle:checked ~ .accordion-header::after { content: ' -'; }
```

---

### Q67. Build a React star rating component.

**Answer:**
```jsx
import { useState } from 'react';

function StarRating({ maxStars = 5, onRate }) {
  const [rating, setRating] = useState(0);
  const [hover, setHover] = useState(0);

  return (
    <div className="star-rating" role="group" aria-label="Star rating">
      {Array.from({ length: maxStars }, (_, i) => i + 1).map(star => (
        <button
          key={star}
          className={`star ${star <= (hover || rating) ? 'filled' : ''}`}
          onClick={() => { setRating(star); onRate?.(star); }}
          onMouseEnter={() => setHover(star)}
          onMouseLeave={() => setHover(0)}
          aria-label={`Rate ${star} star${star > 1 ? 's' : ''}`}
        >
          ★
        </button>
      ))}
      <span>Rating: {rating}/{maxStars}</span>
    </div>
  );
}

export default StarRating;
```

---

### Q68. Build an infinite scroll component in React.

**Answer:**
```jsx
import { useState, useEffect, useRef, useCallback } from 'react';

function InfiniteScroll() {
  const [items, setItems] = useState([]);
  const [page, setPage] = useState(1);
  const [loading, setLoading] = useState(false);
  const [hasMore, setHasMore] = useState(true);
  const observer = useRef();

  const lastItemRef = useCallback(node => {
    if (loading) return;
    if (observer.current) observer.current.disconnect();
    
    observer.current = new IntersectionObserver(entries => {
      if (entries[0].isIntersecting && hasMore) {
        setPage(prev => prev + 1);
      }
    });
    
    if (node) observer.current.observe(node);
  }, [loading, hasMore]);

  useEffect(() => {
    setLoading(true);
    fetchItems(page).then(newItems => {
      setItems(prev => [...prev, ...newItems]);
      setHasMore(newItems.length > 0);
      setLoading(false);
    });
  }, [page]);

  return (
    <div>
      {items.map((item, i) => (
        <div key={item.id} ref={i === items.length - 1 ? lastItemRef : null}>
          {item.name}
        </div>
      ))}
      {loading && <div>Loading...</div>}
    </div>
  );
}
```

---

# ═══════════════════════════════════════
# DEBUGGING PROBLEMS
# ═══════════════════════════════════════

### Q69. Why is `this` undefined in a React class component method?

**Answer:**
```jsx
// ❌ Problem
class Button extends React.Component {
  handleClick() {
    console.log(this.state.count); // TypeError: Cannot read property 'state' of undefined
  }
  render() {
    return <button onClick={this.handleClick}>Click</button>;
  }
}
```

**Reason:** When you pass `this.handleClick` as a callback, it loses its `this` binding.

```jsx
// ✅ Fix 1: Bind in constructor
constructor(props) {
  super(props);
  this.handleClick = this.handleClick.bind(this);
}

// ✅ Fix 2: Arrow function class property
handleClick = () => { console.log(this.state.count); }

// ✅ Fix 3: Arrow function in JSX (creates new fn each render - not ideal)
<button onClick={() => this.handleClick()}>Click</button>
```

---

### Q70. Debug: Why is the state not updating immediately?

**Answer:**
```jsx
// ❌ Problem
function Counter() {
  const [count, setCount] = useState(0);
  
  function handleClick() {
    setCount(count + 1);
    console.log(count); // Still shows old value!
  }
}
```

**Reason:** `setState` is **asynchronous**. The `count` variable is captured in the closure at render time and doesn't reflect the queued update.

```jsx
// ✅ Fix: Use useEffect to observe updated state
useEffect(() => {
  console.log(count); // Runs after state update
}, [count]);

// ✅ Fix: Use functional update for dependent state
setCount(prev => {
  const newCount = prev + 1;
  console.log(newCount); // You have the new value here
  return newCount;
});
```

---

### Q71. Debug: An API call fires on every render. Fix it.

**Answer:**
```jsx
// ❌ Problem — no dependency array
useEffect(() => {
  fetch('/api/data').then(r => r.json()).then(setData);
}); // Runs on every render → infinite loop if setData triggers re-render!

// ✅ Fix — empty array for mount-only
useEffect(() => {
  fetch('/api/data').then(r => r.json()).then(setData);
}, []); // Only on mount
```

---

### Q72. Debug: Memory leak in useEffect.

**Answer:**
```jsx
// ❌ Problem — state update on unmounted component
useEffect(() => {
  fetchData().then(data => {
    setData(data); // ⚠️ Component might be unmounted by now
  });
}, []);

// ✅ Fix — use cleanup flag
useEffect(() => {
  let isMounted = true;
  
  fetchData().then(data => {
    if (isMounted) setData(data); // Only update if still mounted
  });
  
  return () => { isMounted = false; }; // Cleanup
}, []);

// ✅ Better Fix — AbortController
useEffect(() => {
  const controller = new AbortController();
  
  fetch('/api/data', { signal: controller.signal })
    .then(r => r.json())
    .then(setData)
    .catch(err => { if (err.name !== 'AbortError') setError(err); });
  
  return () => controller.abort();
}, []);
```

---

### Q73. Debug: CSS styles not applying. Troubleshoot steps.

**Answer:**
Systematic debugging approach:

1. **Check if selector is correct** — Inspect element in DevTools, verify the rule appears in Styles panel
2. **Check specificity** — A more specific rule may be overriding
3. **Check cascade order** — Later rule wins at same specificity
4. **Check for typos** — Wrong class name, missing dash
5. **Check `display` type** — e.g., `width` doesn't work on inline elements
6. **Check parent constraints** — Parent might be `overflow: hidden`, wrong display context
7. **Check inheritance** — Some properties don't inherit (`border`, `padding`)
8. **Check computed styles** — Look at the "Computed" tab in DevTools to see final applied value

```css
/* Common pitfall: wrong element type */
span { width: 200px; } /* ❌ width doesn't work on inline elements */
span { display: inline-block; width: 200px; } /* ✅ */
```

---

# ═══════════════════════════════════════
# RESULT-BASED PROBLEMS
# ═══════════════════════════════════════

### Q74. What is the output of the following code?

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```

**Answer:** `3, 3, 3`

**Why:** `var` is function-scoped. By the time setTimeout callbacks run (after the loop), `i` is already `3`.

**Fix with `let`:**
```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
// Output: 0, 1, 2 — let is block-scoped, creates new binding per iteration
```

---

### Q75. What is the output?

```js
console.log(typeof null);
console.log(null instanceof Object);
console.log(null == undefined);
console.log(null === undefined);
```

**Answer:**
```
"object"   // Historical bug — null is NOT actually an object
false      // null is not an instance of Object
true       // Loose equality — only null == undefined and undefined == null
false      // Strict equality — different types
```

---

### Q76. What will this print?

```js
const a = [1, 2, 3];
const b = a;
b.push(4);
console.log(a);
console.log(a === b);
```

**Answer:**
```js
[1, 2, 3, 4]  // a is mutated because b holds reference to same array
true           // a and b point to the same object in memory
```

---

### Q77. What is the output?

```js
function foo() {
  console.log(this);
}
const bar = { foo };
bar.foo();       // ?
foo();           // ?
const baz = bar.foo;
baz();           // ?
```

**Answer:**
```
bar.foo()  → { foo: [Function: foo] }  (this = bar)
foo()      → window / global           (this = global, non-strict)
baz()      → window / global           (method extracted, loses context)
```

---

### Q78. What does this React code do? What's the bug?

```jsx
function Counter() {
  const [count, setCount] = useState(0);
  
  useEffect(() => {
    const id = setInterval(() => {
      setCount(count + 1);
    }, 1000);
    return () => clearInterval(id);
  }, []);
  
  return <div>{count}</div>;
}
```

**Answer:**
**Bug:** Stale closure. The `count` inside the interval callback is always `0` because the effect runs only once (`[]`) and captures `count = 0`.

**Result:** Counter always shows `1` (0 + 1 forever).

**Fix:**
```jsx
useEffect(() => {
  const id = setInterval(() => {
    setCount(prev => prev + 1); // Use functional update — doesn't need count in closure
  }, 1000);
  return () => clearInterval(id);
}, []);
```

---

# ═══════════════════════════════════════
# LIFECYCLE BASED PROBLEMS
# ═══════════════════════════════════════

### Q79. When does a React component re-render?

**Answer:**
A component re-renders when:
1. Its **state** changes (`setState` / `useState` setter)
2. Its **props** change (parent re-renders, new value passed)
3. Its **context** value changes (if consuming via `useContext`)
4. Its **parent** re-renders (even if props are same — unless `React.memo`)
5. `forceUpdate()` is called (class components)

**Preventing unnecessary re-renders:**
```jsx
// Wrap component with React.memo
const Child = React.memo(({ value }) => <div>{value}</div>);

// Stable function reference
const handler = useCallback(() => {}, []);

// Stable object reference
const config = useMemo(() => ({ key: 'value' }), []);
```

---

### Q80. Explain the order of useEffect hooks with multiple effects.

**Answer:**
Multiple `useEffect` hooks run in the **order they are declared**, after the browser has painted.

```jsx
function Component() {
  useEffect(() => {
    console.log('Effect 1');
    return () => console.log('Cleanup 1');
  }, []);

  useEffect(() => {
    console.log('Effect 2');
    return () => console.log('Cleanup 2');
  }, []);
}

// On mount:    Effect 1, Effect 2
// On unmount:  Cleanup 1, Cleanup 2 (in order)
```

On update: All cleanups run first (for previous render), then all effects.

---

### Q81. What is `useLayoutEffect` vs `useEffect`?

**Answer:**

| | `useEffect` | `useLayoutEffect` |
|--|-------------|-------------------|
| Timing | After browser paint | After DOM mutations, before paint |
| Async? | Yes (non-blocking) | No (synchronous, blocks paint) |
| Use for | Data fetching, subscriptions | DOM measurements, preventing flicker |

```jsx
// useLayoutEffect — read DOM measurements before browser paints
useLayoutEffect(() => {
  const height = ref.current.getBoundingClientRect().height;
  setHeight(height); // Won't cause visible flicker
}, []);

// useEffect — same code would cause flicker (paint with wrong height, then repaint)
```

---

# ═══════════════════════════════════════
# DEBUGGING SCENARIOS IN REAL PROJECTS
# ═══════════════════════════════════════

### Q82. Scenario: Your React app loads slowly on first visit. How do you debug and fix it?

**Answer:**

**Step 1: Identify the problem**
- Open Chrome DevTools → Network tab → Disable cache → Reload
- Check bundle size (large JS files?)
- Run Lighthouse audit

**Step 2: Common culprits & fixes**

```jsx
// 1. Large bundle — code split routes
const Home = React.lazy(() => import('./pages/Home'));
const Dashboard = React.lazy(() => import('./pages/Dashboard'));

// 2. Large images — use next-gen formats, lazy loading
<img src="hero.webp" loading="lazy" alt="..." />

// 3. Render-blocking resources
<link rel="preload" href="critical.css" as="style">
<script defer src="app.js"></script>

// 4. Unused dependencies — check bundle analyzer
// npx webpack-bundle-analyzer stats.json
```

**Step 3: Metrics to track**
- LCP (Largest Contentful Paint) < 2.5s
- FID/INP < 200ms
- CLS < 0.1

---

### Q83. Scenario: Infinite re-render loop in React. How do you debug it?

**Answer:**

**Symptoms:** Browser tab freezes, "Maximum update depth exceeded" error.

**Common causes:**
```jsx
// 1. setState inside useEffect with no deps or wrong deps
useEffect(() => {
  setCount(count + 1); // ❌ count changes → effect runs → count changes...
}); // Missing dependency array

// Fix: Add proper deps or remove state update from effect

// 2. New object/array reference in deps
const options = { theme: 'dark' }; // New reference every render
useEffect(() => { fetchData(options); }, [options]); // ❌ infinite loop

// Fix: useMemo or move options outside component
const options = useMemo(() => ({ theme: 'dark' }), []);

// 3. setState during render
function Component() {
  const [x, setX] = useState(0);
  setX(1); // ❌ setState during render → re-render → setState...
  return <div>{x}</div>;
}
```

**Debug tool:** React DevTools Profiler — shows what triggered re-renders.

---

### Q84. Scenario: API data shows in console but not on screen.

**Answer:**

```jsx
// Common causes to check:

// 1. State not set correctly
fetch('/api/users')
  .then(res => res.json())
  .then(data => {
    console.log(data);  // Shows data
    setUsers(data.users); // ❌ data.users is undefined? Check structure
    // ✅ setUsers(data);
  });

// 2. Conditional render hiding it
{users && users.map(u => <div key={u.id}>{u.name}</div>)}
// Check: is users null vs empty array?

// 3. Wrong key causing weird behavior
// 4. Component not subscribing to the right state

// Debug steps:
// - Add console.log in render to check state value
// - Check React DevTools component state
// - Verify API response structure in Network tab
```

---

# ═══════════════════════════════════════
# FOLDER STRUCTURE CONFIGURATION
# ═══════════════════════════════════════

### Q85. What is a good folder structure for a large React application?

**Answer:**

```
src/
├── api/                    # API layer
│   ├── client.js           # Axios/fetch configuration
│   ├── userApi.js
│   └── productApi.js
├── assets/                 # Static files
│   ├── images/
│   ├── fonts/
│   └── icons/
├── components/             # Reusable UI components
│   ├── Button/
│   │   ├── Button.jsx
│   │   ├── Button.module.scss
│   │   ├── Button.test.jsx
│   │   └── index.js        # Re-export
│   ├── Modal/
│   └── Form/
├── features/               # Feature-based modules (Redux Toolkit slices)
│   ├── auth/
│   │   ├── authSlice.js
│   │   ├── Login.jsx
│   │   └── useAuth.js
│   └── products/
├── hooks/                  # Custom hooks
│   ├── useFetch.js
│   ├── useDebounce.js
│   └── useLocalStorage.js
├── pages/                  # Route-level components
│   ├── Home/
│   ├── Dashboard/
│   └── Profile/
├── store/                  # Redux store configuration
│   └── store.js
├── styles/                 # Global SCSS
│   ├── _variables.scss
│   ├── _mixins.scss
│   ├── _reset.scss
│   └── main.scss
├── utils/                  # Pure utility functions
│   ├── formatDate.js
│   ├── validators.js
│   └── constants.js
├── App.jsx
└── main.jsx
```

---

### Q86. What is the Barrel pattern in file exports?

**Answer:**
Barrel files (`index.js`) re-export from multiple files, simplifying imports.

```
components/
  Button/
    Button.jsx
    index.js   ← "barrel"
  Input/
    Input.jsx
    index.js
  index.js     ← root barrel
```

```js
// components/Button/index.js
export { default } from './Button';
export * from './Button';

// components/index.js — root barrel
export { default as Button } from './Button';
export { default as Input } from './Input';
export { default as Modal } from './Modal';

// Import from anywhere in app
import { Button, Input, Modal } from '@/components';
```

⚠️ Large barrel files can hurt tree-shaking in some bundlers. Use with care.

---

# ═══════════════════════════════════════
# CODING QUESTIONS
# ═══════════════════════════════════════

### Q87. Implement debounce from scratch.

**Answer:**
```js
function debounce(fn, delay) {
  let timerId = null;
  
  return function(...args) {
    if (timerId) clearTimeout(timerId);
    
    timerId = setTimeout(() => {
      fn.apply(this, args);
      timerId = null;
    }, delay);
  };
}

// Usage
const search = debounce((query) => fetchResults(query), 300);
input.addEventListener('input', (e) => search(e.target.value));
```

---

### Q88. Implement a `flatDeep` function to flatten nested arrays.

**Answer:**
```js
// Recursive approach
function flatDeep(arr, depth = Infinity) {
  if (depth === 0) return arr.slice();
  return arr.reduce((acc, val) => {
    if (Array.isArray(val)) {
      acc.push(...flatDeep(val, depth - 1));
    } else {
      acc.push(val);
    }
    return acc;
  }, []);
}

flatDeep([1, [2, [3, [4]]]]);     // [1, 2, 3, 4]
flatDeep([1, [2, [3, [4]]]], 2); // [1, 2, 3, [4]]

// Native: arr.flat(Infinity)
```

---

### Q89. Implement `pipe` and `compose` functions.

**Answer:**
```js
// pipe — applies functions left-to-right
const pipe = (...fns) => x => fns.reduce((v, f) => f(v), x);

// compose — applies functions right-to-left
const compose = (...fns) => x => fns.reduceRight((v, f) => f(v), x);

const double = x => x * 2;
const addOne = x => x + 1;
const square = x => x * x;

const transform = pipe(double, addOne, square);
transform(3); // square(addOne(double(3))) = square(7) = 49

const transform2 = compose(square, addOne, double);
transform2(3); // same result: 49
```

---

### Q90. Implement `memoize` function.

**Answer:**
```js
function memoize(fn) {
  const cache = new Map();
  
  return function(...args) {
    const key = JSON.stringify(args);
    
    if (cache.has(key)) {
      console.log('Cache hit');
      return cache.get(key);
    }
    
    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

const expensiveCalc = memoize((n) => {
  console.log('Computing...');
  return n * n;
});

expensiveCalc(5); // Computing... → 25
expensiveCalc(5); // Cache hit → 25
```

---

### Q91. Flatten a deeply nested object.

**Answer:**
```js
function flattenObject(obj, prefix = '', result = {}) {
  for (const key in obj) {
    const newKey = prefix ? `${prefix}.${key}` : key;
    
    if (typeof obj[key] === 'object' && obj[key] !== null && !Array.isArray(obj[key])) {
      flattenObject(obj[key], newKey, result);
    } else {
      result[newKey] = obj[key];
    }
  }
  return result;
}

flattenObject({ a: { b: { c: 1 }, d: 2 }, e: 3 });
// { 'a.b.c': 1, 'a.d': 2, 'e': 3 }
```

---

### Q92. Implement `Promise.all` from scratch.

**Answer:**
```js
function promiseAll(promises) {
  return new Promise((resolve, reject) => {
    if (promises.length === 0) return resolve([]);
    
    const results = new Array(promises.length);
    let resolved = 0;
    
    promises.forEach((promise, i) => {
      Promise.resolve(promise).then(value => {
        results[i] = value;
        resolved++;
        if (resolved === promises.length) resolve(results);
      }).catch(reject);
    });
  });
}
```

---

### Q93. Build a custom `useDebounce` hook.

**Answer:**
```jsx
import { useState, useEffect } from 'react';

function useDebounce(value, delay = 300) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => setDebouncedValue(value), delay);
    return () => clearTimeout(timer); // Cleanup on each value change
  }, [value, delay]);

  return debouncedValue;
}

// Usage
function SearchBar() {
  const [query, setQuery] = useState('');
  const debouncedQuery = useDebounce(query, 400);

  useEffect(() => {
    if (debouncedQuery) fetchResults(debouncedQuery);
  }, [debouncedQuery]);

  return <input value={query} onChange={e => setQuery(e.target.value)} />;
}
```

---

### Q94. Implement a custom `useFetch` hook.

**Answer:**
```jsx
import { useState, useEffect, useRef } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  const abortRef = useRef(null);

  useEffect(() => {
    if (!url) return;
    
    abortRef.current = new AbortController();
    setLoading(true);
    setError(null);

    fetch(url, { signal: abortRef.current.signal })
      .then(res => {
        if (!res.ok) throw new Error(`HTTP error ${res.status}`);
        return res.json();
      })
      .then(setData)
      .catch(err => {
        if (err.name !== 'AbortError') setError(err.message);
      })
      .finally(() => setLoading(false));

    return () => abortRef.current.abort();
  }, [url]);

  return { data, loading, error };
}

// Usage
function UserProfile({ id }) {
  const { data, loading, error } = useFetch(`/api/users/${id}`);
  if (loading) return <Spinner />;
  if (error) return <Error message={error} />;
  return <Profile user={data} />;
}
```

---

### Q95. Build a generic pagination component.

**Answer:**
```jsx
function Pagination({ currentPage, totalPages, onPageChange }) {
  const pages = [];

  // Generate visible page numbers with ellipsis
  for (let i = 1; i <= totalPages; i++) {
    if (
      i === 1 || i === totalPages ||
      (i >= currentPage - 2 && i <= currentPage + 2)
    ) {
      pages.push(i);
    } else if (pages[pages.length - 1] !== '...') {
      pages.push('...');
    }
  }

  return (
    <nav aria-label="Pagination">
      <button disabled={currentPage === 1} onClick={() => onPageChange(currentPage - 1)}>
        ← Prev
      </button>
      {pages.map((page, i) =>
        page === '...' ? (
          <span key={`ellipsis-${i}`}>...</span>
        ) : (
          <button
            key={page}
            onClick={() => onPageChange(page)}
            aria-current={page === currentPage ? 'page' : undefined}
            className={page === currentPage ? 'active' : ''}
          >
            {page}
          </button>
        )
      )}
      <button disabled={currentPage === totalPages} onClick={() => onPageChange(currentPage + 1)}>
        Next →
      </button>
    </nav>
  );
}
```

---

# ═══════════════════════════════════════
# ADDITIONAL L1 / L2 / L3 QUESTIONS
# ═══════════════════════════════════════

### Q96. What is event delegation? Why is it useful?

**Answer:**
Event delegation attaches a single event listener to a **parent** to handle events from its children (using event bubbling).

```js
// ❌ Without delegation — 1000 listeners for 1000 items
document.querySelectorAll('.list-item').forEach(item => {
  item.addEventListener('click', handleClick);
});

// ✅ With delegation — 1 listener on parent
document.querySelector('.list').addEventListener('click', (e) => {
  if (e.target.matches('.list-item')) {
    handleClick(e.target);
  }
});
```

**Benefits:** Better performance, works for dynamically added elements, less memory usage.

---

### Q97. What are Web Workers? When would you use them?

**Answer:**
Web Workers run scripts in a **background thread** separate from the main thread, preventing UI freezing.

```js
// main.js
const worker = new Worker('worker.js');
worker.postMessage({ data: largeArray }); // Send data
worker.onmessage = (e) => setResult(e.data); // Receive result

// worker.js
self.onmessage = (e) => {
  const result = heavyComputation(e.data.data); // Runs off main thread
  self.postMessage(result);
};
```

**Use cases:** Image processing, data parsing, complex calculations, encryption.

---

### Q98. What is lazy loading? Implement it for images.

**Answer:**
Lazy loading defers loading of off-screen resources until they're needed.

```html
<!-- Native HTML lazy loading -->
<img src="photo.jpg" loading="lazy" alt="Photo" />
```

```js
// Intersection Observer approach
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const img = entry.target;
      img.src = img.dataset.src; // Load actual image
      observer.unobserve(img);
    }
  });
}, { rootMargin: '100px' });

document.querySelectorAll('img[data-src]').forEach(img => observer.observe(img));
```

```html
<img data-src="photo.jpg" src="placeholder.jpg" alt="Photo" />
```

---

### Q99. What is Tree Shaking? How does it work?

**Answer:**
Tree shaking eliminates dead code (unused exports) from your bundle during build time.

```js
// math.js
export const add = (a, b) => a + b;
export const multiply = (a, b) => a * b; // Not used anywhere
export const divide = (a, b) => a / b;   // Not used anywhere

// main.js
import { add } from './math'; // Only add is bundled
```

**Requirements:**
- ES modules (`import/export`, not CommonJS `require`)
- Bundler support (Webpack, Rollup, Vite)
- `"sideEffects": false` in package.json (if applicable)

---

### Q100. What is CORS? How do you handle CORS issues in development?

**Answer:**
CORS (Cross-Origin Resource Sharing) is a browser security mechanism that blocks requests from a different origin (protocol + domain + port).

```
Frontend: http://localhost:3000
API:      http://localhost:5000  ← Different port = different origin!
```

**Server fix (add headers):**
```js
// Express
app.use(cors({ origin: 'http://localhost:3000' }));

// Response headers
Access-Control-Allow-Origin: http://localhost:3000
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
```

**Dev proxy fix (Vite / CRA):**
```js
// vite.config.js
server: {
  proxy: {
    '/api': { target: 'http://localhost:5000', changeOrigin: true }
  }
}
```

---

### Q101. What is `localStorage` vs `sessionStorage` vs cookies?

**Answer:**

| | localStorage | sessionStorage | Cookies |
|--|-------------|----------------|---------|
| Capacity | ~5MB | ~5MB | ~4KB |
| Expiry | Never | Session end | Set expiry |
| Server access | No | No | Yes (with header) |
| Cross-tab | Yes | No | Yes |

```js
// localStorage
localStorage.setItem('theme', 'dark');
localStorage.getItem('theme'); // 'dark'
localStorage.removeItem('theme');

// Cookies
document.cookie = "user=alice; expires=Fri, 31 Dec 2025 23:59:59 GMT; path=/";

// Prefer:
// - localStorage for large client-side data (cart, preferences)
// - Cookies for auth tokens (httpOnly, secure flags)
// - sessionStorage for one-session data (form steps)
```

---

### Q102. Explain the difference between synchronous and asynchronous JavaScript.

**Answer:**
- **Synchronous**: Code executes line by line, blocking the next line until current completes
- **Asynchronous**: Operations that take time (I/O, network) are delegated; code continues without waiting

```js
// Synchronous — blocks
const data = fs.readFileSync('file.txt'); // Blocks entire thread
console.log(data);
console.log('Done'); // Only after file is read

// Asynchronous — non-blocking
fs.readFile('file.txt', (err, data) => {
  console.log(data); // Runs when file is ready
});
console.log('Done'); // Runs immediately, before file is read
```

---

### Q103. What is the difference between `Array.map()`, `forEach()`, `filter()`, and `reduce()`?

**Answer:**

```js
const nums = [1, 2, 3, 4, 5];

// map — transform each item, returns NEW array of same length
const doubled = nums.map(n => n * 2); // [2, 4, 6, 8, 10]

// forEach — iterate with side effects, returns undefined
nums.forEach(n => console.log(n)); // undefined (no return value)

// filter — keep items matching condition, returns NEW array (may be shorter)
const evens = nums.filter(n => n % 2 === 0); // [2, 4]

// reduce — accumulate values into single result
const sum = nums.reduce((acc, n) => acc + n, 0); // 15
const grouped = nums.reduce((acc, n) => {
  (n % 2 === 0 ? acc.even : acc.odd).push(n);
  return acc;
}, { even: [], odd: [] });
// { even: [2, 4], odd: [1, 3, 5] }
```

---

### Q104. What are `Symbol`, `BigInt`, and `Map` / `Set`?

**Answer:**

```js
// Symbol — unique, immutable identifier
const id = Symbol('id');
const id2 = Symbol('id');
id === id2; // false — each Symbol is unique

// BigInt — integers larger than Number.MAX_SAFE_INTEGER
const big = 9007199254740991n + 1n; // 9007199254740992n

// Map — key-value store, any type as key (vs Object: only strings)
const map = new Map();
map.set({ name: 'key' }, 'value');
map.set(42, 'number key');
map.size; // 2

// Set — collection of unique values
const set = new Set([1, 2, 2, 3, 3]);
set.size; // 3 — [1, 2, 3]
set.has(2); // true
```

---

### Q105. What is the difference between `==` null check and optional chaining `?.`?

**Answer:**

```js
const user = { profile: { name: 'Alice' } };

// Without optional chaining — error prone
const city = user && user.address && user.address.city; // Old way

// Optional chaining — short-circuits to undefined
const city = user?.address?.city; // undefined (no error)
const zip = user?.address?.zipCode ?? 'N/A'; // 'N/A' (nullish coalescing)

// Works with methods too
user.getAddress?.(); // Calls if method exists
arr?.[0]?.name;      // Safe array access
```

---

### Q106. What is `Array.from()` and when do you use it?

**Answer:**
`Array.from()` creates an array from array-like or iterable objects.

```js
// NodeList to Array (for .map, .filter)
const divs = Array.from(document.querySelectorAll('div'));
divs.map(div => div.className);

// String to Array
Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']

// Arguments object
function sum() {
  return Array.from(arguments).reduce((a, b) => a + b, 0);
}

// Create array of N items
Array.from({ length: 5 }, (_, i) => i + 1); // [1, 2, 3, 4, 5]

// Set to Array
Array.from(new Set([1, 2, 2, 3])); // [1, 2, 3]
```

---

### Q107. What are CSS animations vs CSS transitions?

**Answer:**

**Transitions** — Animate between two states (triggered by state change)
```css
.button {
  background: blue;
  transition: background 0.3s ease, transform 0.2s;
}
.button:hover {
  background: darkblue;
  transform: scale(1.05);
}
```

**Animations** — Define keyframe sequences (can loop, auto-run)
```css
@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

.loader {
  animation: spin 1s linear infinite;
  animation-delay: 0.2s;
  animation-fill-mode: forwards; /* Keep end state after animation */
}
```

**Performance tip:** Animate only `transform` and `opacity` — they use the GPU compositor and don't trigger layout.

---

### Q108. What is the `<picture>` element and responsive images?

**Answer:**
The `<picture>` element provides multiple image sources for different scenarios.

```html
<!-- Art direction — different crops for different viewports -->
<picture>
  <source media="(max-width: 768px)" srcset="hero-mobile.webp" type="image/webp">
  <source media="(max-width: 768px)" srcset="hero-mobile.jpg">
  <source srcset="hero-desktop.webp" type="image/webp">
  <img src="hero-desktop.jpg" alt="Hero image" loading="lazy">
</picture>

<!-- Srcset for resolution switching -->
<img
  src="photo-400.jpg"
  srcset="photo-400.jpg 400w, photo-800.jpg 800w, photo-1200.jpg 1200w"
  sizes="(max-width: 600px) 100vw, (max-width: 1200px) 50vw, 33vw"
  alt="Photo"
/>
```

---

### Q109. What is the difference between `Array.find()` and `Array.findIndex()`?

**Answer:**
```js
const users = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
  { id: 3, name: 'Charlie' }
];

// find — returns the first matching ITEM (or undefined)
const user = users.find(u => u.id === 2);
// { id: 2, name: 'Bob' }

// findIndex — returns the INDEX of first match (or -1)
const index = users.findIndex(u => u.id === 2);
// 1

// Use case
const idx = users.findIndex(u => u.id === 2);
if (idx !== -1) {
  users[idx] = { ...users[idx], name: 'Robert' }; // Update
}
```

---

### Q110. What is `Object.keys()`, `Object.values()`, `Object.entries()`?

**Answer:**
```js
const user = { name: 'Alice', age: 30, role: 'admin' };

Object.keys(user);    // ['name', 'age', 'role']
Object.values(user);  // ['Alice', 30, 'admin']
Object.entries(user); // [['name', 'Alice'], ['age', 30], ['role', 'admin']]

// Useful with Object.fromEntries — transform object
const transformed = Object.fromEntries(
  Object.entries(user)
    .filter(([key]) => key !== 'role')
    .map(([key, val]) => [key, typeof val === 'string' ? val.toUpperCase() : val])
);
// { name: 'ALICE', age: 30 }
```

---

### Q111. What are Higher Order Components (HOC) in React?

**Answer:**
A HOC is a function that takes a component and returns a new enhanced component.

```jsx
// HOC that adds loading/error handling
function withDataFetching(WrappedComponent, fetchFn) {
  return function EnhancedComponent(props) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
      fetchFn().then(setData).finally(() => setLoading(false));
    }, []);

    if (loading) return <Spinner />;
    return <WrappedComponent data={data} {...props} />;
  };
}

// Usage
const UserListWithData = withDataFetching(UserList, fetchUsers);

// Modern alternative: Custom hooks (preferred over HOCs)
```

---

### Q112. What is the Render Props pattern?

**Answer:**
A technique where a component's prop is a function that returns JSX, giving control of rendering to the parent.

```jsx
// Mouse tracker using render prop
function MouseTracker({ render }) {
  const [position, setPosition] = useState({ x: 0, y: 0 });
  
  return (
    <div onMouseMove={e => setPosition({ x: e.clientX, y: e.clientY })}>
      {render(position)} {/* Call the render prop */}
    </div>
  );
}

// Usage
<MouseTracker render={({ x, y }) => (
  <p>Mouse is at {x}, {y}</p>
)} />

// Also valid using children as function
<MouseTracker>
  {({ x, y }) => <p>Mouse is at {x}, {y}</p>}
</MouseTracker>
```

---

### Q113. What are compound components in React?

**Answer:**
A pattern where components work together through shared implicit state.

```jsx
// Compound component example
function Tabs({ children }) {
  const [activeTab, setActiveTab] = useState(0);
  return (
    <TabsContext.Provider value={{ activeTab, setActiveTab }}>
      <div className="tabs">{children}</div>
    </TabsContext.Provider>
  );
}

Tabs.List = function TabList({ children }) {
  return <div role="tablist">{children}</div>;
};

Tabs.Tab = function Tab({ index, children }) {
  const { activeTab, setActiveTab } = useContext(TabsContext);
  return (
    <button role="tab" aria-selected={activeTab === index} onClick={() => setActiveTab(index)}>
      {children}
    </button>
  );
};

Tabs.Panel = function Panel({ index, children }) {
  const { activeTab } = useContext(TabsContext);
  return activeTab === index ? <div role="tabpanel">{children}</div> : null;
};

// Usage
<Tabs>
  <Tabs.List>
    <Tabs.Tab index={0}>Tab 1</Tabs.Tab>
    <Tabs.Tab index={1}>Tab 2</Tabs.Tab>
  </Tabs.List>
  <Tabs.Panel index={0}>Content 1</Tabs.Panel>
  <Tabs.Panel index={1}>Content 2</Tabs.Panel>
</Tabs>
```

---

### Q114. What are Error Boundaries in React?

**Answer:**
Error Boundaries are class components that catch JavaScript errors in their child component tree and display a fallback UI.

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false, error: null };

  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }

  componentDidCatch(error, errorInfo) {
    logErrorToService(error, errorInfo.componentStack);
  }

  render() {
    if (this.state.hasError) {
      return (
        <div>
          <h2>Something went wrong</h2>
          <button onClick={() => this.setState({ hasError: false })}>Try Again</button>
        </div>
      );
    }
    return this.props.children;
  }
}

// Usage
<ErrorBoundary>
  <MyBuggyComponent />
</ErrorBoundary>
```

Note: Error boundaries don't catch errors in event handlers, async code, or SSR.

---

### Q115. How do you handle forms in React? Controlled vs Uncontrolled.

**Answer:**

**Controlled** — React state drives the input value
```jsx
function ControlledForm() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log({ email, password });
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="email" value={email} onChange={e => setEmail(e.target.value)} />
      <input type="password" value={password} onChange={e => setPassword(e.target.value)} />
      <button type="submit">Login</button>
    </form>
  );
}
```

**Uncontrolled** — DOM handles the value (access via `ref`)
```jsx
function UncontrolledForm() {
  const emailRef = useRef();
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(emailRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="email" ref={emailRef} defaultValue="" />
      <button type="submit">Submit</button>
    </form>
  );
}
```

For complex forms, consider **React Hook Form** or **Formik**.

---

### Q116. What is the `key` prop in React lists and why does it matter?

**Answer:**
`key` is a special prop that helps React identify which items have changed, been added, or removed.

```jsx
// ❌ Using index as key — causes bugs with reordering/deletion
{items.map((item, index) => <Item key={index} item={item} />)}

// ✅ Using stable unique ID
{items.map(item => <Item key={item.id} item={item} />)}
```

**What goes wrong with index keys:**
- When you delete/reorder items, React incorrectly matches old components to new items
- State (inputs, animations) gets mixed up between items
- Unnecessary re-renders

**Rule:** Use a stable, unique ID from your data. Never use index unless list is truly static.

---

### Q117. Explain `useReducer`. When would you choose it over `useState`?

**Answer:**
`useReducer` manages complex state logic with a pure reducer function.

```jsx
const initialState = { count: 0, loading: false, error: null };

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT': return { ...state, count: state.count + 1 };
    case 'DECREMENT': return { ...state, count: state.count - 1 };
    case 'FETCH_START': return { ...state, loading: true };
    case 'FETCH_SUCCESS': return { ...state, loading: false, data: action.payload };
    case 'FETCH_ERROR': return { ...state, loading: false, error: action.payload };
    default: return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  
  return (
    <div>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>+</button>
      <span>{state.count}</span>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>-</button>
    </div>
  );
}
```

**Choose `useReducer` when:**
- Multiple state values updated together
- Next state depends on previous
- Complex state transitions (like a state machine)
- Sharing state logic (testable pure functions)

---

### Q118. What is Suspense in React? How does it work with data fetching?

**Answer:**
`Suspense` lets components "wait" for async operations to complete before rendering.

```jsx
// Code splitting (stable)
const Profile = React.lazy(() => import('./Profile'));

function App() {
  return (
    <Suspense fallback={<LoadingSpinner />}>
      <Profile />
    </Suspense>
  );
}

// Data fetching (React 18 + compatible libraries like SWR/React Query)
function UserProfile({ id }) {
  // Library throws a promise if data isn't ready → Suspense catches it
  const user = useSuspenseQuery(['user', id], () => fetchUser(id));
  return <Profile user={user} />;
}

<Suspense fallback={<ProfileSkeleton />}>
  <UserProfile id={1} />
</Suspense>
```

---

### Q119. What is the difference between `<React.Fragment>` and `<>`?

**Answer:**
Both avoid adding extra DOM nodes as wrappers. `<>` is shorthand syntax.

```jsx
// Long form — supports the 'key' prop (needed in lists)
function Items({ items }) {
  return items.map(item => (
    <React.Fragment key={item.id}>
      <dt>{item.term}</dt>
      <dd>{item.description}</dd>
    </React.Fragment>
  ));
}

// Shorthand — cleaner but doesn't support 'key'
function Layout() {
  return (
    <>
      <header>Header</header>
      <main>Content</main>
      <footer>Footer</footer>
    </>
  );
}
```

---

### Q120. What is the Stale Closure problem? How do you fix it?

**Answer:**
A stale closure occurs when a function captures an outdated value from a closure because it wasn't updated when state changed.

```jsx
// ❌ Stale closure
function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const id = setInterval(() => {
      console.log(count); // Always 0 — captured at mount
      setCount(count + 1); // Always sets to 1 (0+1)
    }, 1000);
    return () => clearInterval(id);
  }, []); // count not in deps
}

// ✅ Fix 1: Functional update
setCount(prev => prev + 1); // No need to capture count

// ✅ Fix 2: Add to dependency array
useEffect(() => {
  // ... uses count
}, [count]); // Re-subscribe when count changes

// ✅ Fix 3: useRef for mutable reference
const countRef = useRef(count);
countRef.current = count;
setInterval(() => console.log(countRef.current), 1000);
```

---

## 🔷 Performance & Advanced Questions

### Q121. What is Core Web Vitals? Explain LCP, FID/INP, CLS.

**Answer:**
Core Web Vitals are Google's metrics for measuring user experience:

| Metric | Stands For | Measures | Good Threshold |
|--------|-----------|----------|----------------|
| LCP | Largest Contentful Paint | Loading performance | < 2.5s |
| INP | Interaction to Next Paint | Responsiveness | < 200ms |
| CLS | Cumulative Layout Shift | Visual stability | < 0.1 |

**Improving each:**
- **LCP:** Preload hero images, optimize server response, eliminate render-blocking resources
- **INP:** Break up long tasks, use `useTransition`, avoid heavy JS on interaction
- **CLS:** Set `width/height` on images/videos, avoid inserting content above existing content

---

### Q122. What is a Service Worker? What is a PWA?

**Answer:**
**Service Worker** — A JS file that runs in the background (separate thread), intercepts network requests, enables caching, push notifications, and offline functionality.

```js
// sw.js
self.addEventListener('fetch', event => {
  event.respondWith(
    caches.match(event.request)
      .then(response => response || fetch(event.request))
  );
});

// Register
navigator.serviceWorker.register('/sw.js');
```

**PWA (Progressive Web App)** — A web app that uses service workers + manifest to provide app-like experience:
- Installable on home screen
- Works offline
- Push notifications
- Fast loading

Required: `manifest.json`, HTTPS, Service Worker

---

### Q123. Explain micro-frontends architecture.

**Answer:**
Micro-frontends extend the microservices concept to the frontend — splitting a large frontend app into smaller, independently deployable pieces owned by different teams.

**Approaches:**
1. **Module Federation** (Webpack 5) — Share code between separately deployed apps at runtime
2. **iFrames** — Strong isolation but poor UX
3. **Web Components** — Custom elements as shared building blocks
4. **Single-SPA** — Framework for composing multiple SPAs

**Pros:** Independent deployments, tech stack flexibility, team autonomy
**Cons:** Complexity, duplicate dependencies, shared state challenges

---

### Q124. What is Accessibility (a11y)? Name key practices.

**Answer:**
Web accessibility ensures sites are usable by people with disabilities.

```html
<!-- Semantic HTML (most important) -->
<nav> <main> <article> <!-- Use semantic tags -->

<!-- ARIA attributes when semantics aren't enough -->
<button aria-label="Close dialog" aria-expanded="false">X</button>
<div role="alert" aria-live="polite">Error: Invalid email</div>

<!-- Images -->
<img src="chart.png" alt="Bar chart showing 40% increase in sales" />
<img src="decoration.png" alt="" />  <!-- Decorative: empty alt -->

<!-- Forms -->
<label for="email">Email address</label>
<input id="email" type="email" aria-required="true" />

<!-- Focus management -->
button:focus-visible { outline: 2px solid blue; } /* Never outline: none */

<!-- Color contrast: 4.5:1 for normal text, 3:1 for large text (WCAG AA) -->
<!-- Keyboard navigation: all interactive elements must be keyboard accessible -->
```

---

### Q125. What is the difference between authentication and authorization?

**Answer:**
- **Authentication (AuthN)** — Verifying *who* you are (login with username/password, OAuth, biometrics)
- **Authorization (AuthZ)** — Verifying *what* you're allowed to do (admin vs. user permissions)

```jsx
// React route protection
function PrivateRoute({ children }) {
  const { user } = useAuth();
  
  if (!user) {
    return <Navigate to="/login" replace />; // Not authenticated
  }
  
  return children;
}

// Role-based access
function AdminPanel() {
  const { user } = useAuth();
  
  if (user.role !== 'admin') {
    return <Forbidden />; // Authenticated but not authorized
  }
  
  return <AdminDashboard />;
}
```

---

### Q126. What is XSS and how do you prevent it in React?

**Answer:**
XSS (Cross-Site Scripting) — An attacker injects malicious scripts into web pages viewed by other users.

**React's built-in protection:** JSX automatically escapes values before rendering.

```jsx
// ✅ Safe — React escapes this
const userInput = '<script>alert("XSS")</script>';
<div>{userInput}</div> // Renders as text, not HTML

// ❌ Dangerous — dangerouslySetInnerHTML bypasses sanitization
<div dangerouslySetInnerHTML={{ __html: userInput }} />

// If you must render HTML, sanitize first
import DOMPurify from 'dompurify';
<div dangerouslySetInnerHTML={{ __html: DOMPurify.sanitize(userInput) }} />
```

**Prevention:**
- Never use `dangerouslySetInnerHTML` with unsanitized user input
- Use `Content-Security-Policy` headers
- Sanitize all user-generated content

---

### Q127. What is React Query / TanStack Query? When would you use it?

**Answer:**
React Query is a data-fetching and server state management library.

```jsx
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query';

// Fetch data
function UserList() {
  const { data, isLoading, error } = useQuery({
    queryKey: ['users'],
    queryFn: () => fetch('/api/users').then(r => r.json()),
    staleTime: 5 * 60 * 1000, // 5 minutes
  });

  if (isLoading) return <Spinner />;
  if (error) return <Error />;
  return data.map(user => <UserCard key={user.id} user={user} />);
}

// Mutate data
function DeleteButton({ userId }) {
  const queryClient = useQueryClient();
  const mutation = useMutation({
    mutationFn: (id) => fetch(`/api/users/${id}`, { method: 'DELETE' }),
    onSuccess: () => queryClient.invalidateQueries({ queryKey: ['users'] }), // Refetch
  });
  
  return <button onClick={() => mutation.mutate(userId)}>Delete</button>;
}
```

**Use when:** You need caching, background refetching, optimistic updates, pagination, infinite scroll.

---

### Q128. What is TypeScript? Why use it in a React project?

**Answer:**
TypeScript is a typed superset of JavaScript that compiles to plain JS.

```tsx
// Define types for props
interface ButtonProps {
  label: string;
  onClick: () => void;
  variant?: 'primary' | 'secondary' | 'danger';
  disabled?: boolean;
}

// Component is type-safe
const Button: React.FC<ButtonProps> = ({ label, onClick, variant = 'primary', disabled }) => {
  return (
    <button
      className={`btn btn-${variant}`}
      onClick={onClick}
      disabled={disabled}
    >
      {label}
    </button>
  );
};

// Type for API response
interface User {
  id: number;
  name: string;
  email: string;
  role: 'admin' | 'user';
}

async function fetchUser(id: number): Promise<User> {
  const res = await fetch(`/api/users/${id}`);
  return res.json();
}
```

**Benefits:** Catch bugs at compile time, better IDE autocomplete, self-documenting code, safer refactoring.

---

### Q129. What is Redux? When should you use it?

**Answer:**
Redux is a predictable state management library based on a single store, pure reducers, and unidirectional data flow.

```js
// Redux Toolkit (modern Redux)
import { createSlice, configureStore } from '@reduxjs/toolkit';

const cartSlice = createSlice({
  name: 'cart',
  initialState: { items: [], total: 0 },
  reducers: {
    addItem: (state, action) => {
      state.items.push(action.payload);  // Immer allows "mutations"
      state.total += action.payload.price;
    },
    removeItem: (state, action) => {
      state.items = state.items.filter(item => item.id !== action.payload);
    }
  }
});

export const { addItem, removeItem } = cartSlice.actions;
const store = configureStore({ reducer: { cart: cartSlice.reducer } });
```

**Use Redux when:**
- Large app with complex, deeply-nested state
- State needs to be shared across many components
- Need time-travel debugging, state persistence

**Don't use for:** Simple apps, server data (use React Query), form state (use RHF).

---

### Q130. What is Next.js and its key features?

**Answer:**
Next.js is a React framework that provides production-ready features out of the box.

**Key features:**

```
1. File-based routing
   pages/index.js        → /
   pages/about.js        → /about
   pages/blog/[slug].js  → /blog/:slug

2. Multiple rendering strategies per page
   - SSR: getServerSideProps
   - SSG: getStaticProps
   - ISR: getStaticProps + revalidate
   - CSR: standard React hooks

3. API Routes
   pages/api/users.js → /api/users (serverless function)

4. Image Optimization
   import Image from 'next/image';
   <Image src="/photo.jpg" width={500} height={300} alt="..." />

5. App Router (Next.js 13+)
   app/page.tsx → Server Component by default
   'use client' → Client Component
```

---

## 🎯 BONUS: Common Coding Challenges at Tech Companies

### Q131. Implement a simple Virtual DOM diffing algorithm.

```js
function diff(oldVNode, newVNode) {
  if (!newVNode) return { type: 'REMOVE' };
  if (!oldVNode) return { type: 'ADD', node: newVNode };
  if (typeof oldVNode !== typeof newVNode ||
      (typeof oldVNode === 'string' && oldVNode !== newVNode)) {
    return { type: 'REPLACE', node: newVNode };
  }
  if (oldVNode.tag !== newVNode.tag) {
    return { type: 'REPLACE', node: newVNode };
  }
  
  const propPatches = diffProps(oldVNode.props, newVNode.props);
  const childPatches = diffChildren(oldVNode.children, newVNode.children);
  
  return { type: 'PATCH', propPatches, childPatches };
}
```

---

### Q132. Write a function to find the most frequently appearing element in an array.

```js
function mostFrequent(arr) {
  const freq = arr.reduce((map, val) => {
    map[val] = (map[val] || 0) + 1;
    return map;
  }, {});
  
  return Object.entries(freq).reduce((max, [val, count]) => 
    count > max.count ? { val, count } : max
  , { val: null, count: 0 }).val;
}

mostFrequent([1, 3, 2, 3, 3, 1, 2, 3]); // 3
```

---

### Q133. Implement event emitter / pub-sub pattern.

```js
class EventEmitter {
  constructor() {
    this.events = {};
  }
  
  on(event, listener) {
    if (!this.events[event]) this.events[event] = [];
    this.events[event].push(listener);
    return () => this.off(event, listener); // Return unsubscribe
  }
  
  off(event, listener) {
    this.events[event] = (this.events[event] || []).filter(l => l !== listener);
  }
  
  emit(event, ...args) {
    (this.events[event] || []).forEach(listener => listener(...args));
  }
  
  once(event, listener) {
    const wrapper = (...args) => {
      listener(...args);
      this.off(event, wrapper);
    };
    this.on(event, wrapper);
  }
}

const emitter = new EventEmitter();
const unsub = emitter.on('login', user => console.log(`Welcome ${user}`));
emitter.emit('login', 'Alice'); // "Welcome Alice"
unsub(); // Remove listener
```

---

## 📚 Quick Reference: Topics by Company

| Company Type | L1 Focus | L2 Focus | L3 Focus |
|-------------|---------|---------|---------|
| Service Companies | HTML, CSS basics, JS fundamentals | ES6, React hooks, SCSS | System design, performance |
| Product Startups | React, state management | Custom hooks, optimization | Architecture, scalability |
| FAANG/Big Tech | All of above + DSA | Advanced JS internals, patterns | Distributed systems, security |
| Fintech | Security, forms | TypeScript, testing | Compliance, performance |
| E-commerce | UI, responsive design | Cart, payments UX | Performance, PWA |

---

## ✅ Interview Preparation Checklist

- [ ] HTML: Semantics, forms, accessibility, meta tags
- [ ] CSS: Box model, flexbox, grid, specificity, animations, responsive
- [ ] SCSS: Variables, mixins, nesting, @use, BEM
- [ ] JS Basic: Data types, hoisting, closures, `this`, prototypes
- [ ] JS ES6+: Arrow functions, destructuring, template literals, modules, classes, iterators
- [ ] JS Advanced: Promises, async/await, event loop, generators, proxy, symbols
- [ ] JS Patterns: Currying, composition, IIFE, design patterns, functional programming
- [ ] React: Hooks, lifecycle, context, patterns, optimization
- [ ] Performance: Core Web Vitals, code splitting, lazy loading
- [ ] Debugging: DevTools, common React bugs, CSS issues
- [ ] Coding: Implement common utilities from scratch
- [ ] System Design: Folder structure, component architecture

---

*Good luck with your interviews! 🚀 Consistency > Cramming. Review 10 questions per day.*

---

# ═══════════════════════════════════════
# COMPLETE JS / ES6+ DEEP DIVE
# ═══════════════════════════════════════
> *All missing topics: ES6 features, OOP, Functional Programming, Design Patterns, DOM, Error Handling, Modules, Iterators, and more*

---

## 🔶 ES6 FEATURES — Complete Reference

### Q134. What are Arrow Functions? How are they different from regular functions?

**Answer:**
Arrow functions are a concise syntax for writing functions introduced in ES6.

```js
// Regular function
function add(a, b) { return a + b; }

// Arrow function
const add = (a, b) => a + b;           // Implicit return
const square = x => x * x;             // Single param — no parens needed
const greet = () => 'Hello!';          // No params
const getObj = () => ({ id: 1 });      // Return object — wrap in ()

// Multi-line
const process = (x) => {
  const result = x * 2;
  return result + 1;
};
```

**Key differences:**

| | Regular Function | Arrow Function |
|--|-----------------|----------------|
| `this` binding | Dynamic (depends on caller) | Lexical (inherits from enclosing scope) |
| `arguments` object | Yes | No (use rest params) |
| `new` keyword | Can be constructor | ❌ Cannot be constructor |
| `prototype` | Has it | No prototype property |
| Named | Can be named/anonymous | Always anonymous |

```js
// this difference — most important!
const timer = {
  id: 42,
  startRegular() {
    setTimeout(function() {
      console.log(this.id); // undefined — 'this' is window/undefined
    }, 100);
  },
  startArrow() {
    setTimeout(() => {
      console.log(this.id); // 42 — 'this' inherited from startArrow
    }, 100);
  }
};
```

---

### Q135. What is Destructuring? Show all forms.

**Answer:**
Destructuring extracts values from arrays or properties from objects into distinct variables.

```js
// ─── ARRAY DESTRUCTURING ───
const [a, b, c] = [1, 2, 3];
// a=1, b=2, c=3

// Skip elements
const [first, , third] = [1, 2, 3];
// first=1, third=3

// Default values
const [x = 10, y = 20] = [5];
// x=5, y=20

// Swap variables
let m = 1, n = 2;
[m, n] = [n, m];
// m=2, n=1

// Rest in array
const [head, ...tail] = [1, 2, 3, 4];
// head=1, tail=[2,3,4]

// ─── OBJECT DESTRUCTURING ───
const user = { name: 'Alice', age: 30, city: 'Mumbai' };

const { name, age } = user;

// Rename while destructuring
const { name: userName, age: userAge } = user;
// userName='Alice', userAge=30

// Default values
const { name, role = 'user' } = user;
// role='user' (not in object)

// Nested destructuring
const { address: { street, zip } } = { address: { street: 'MG Road', zip: '400001' } };

// Rest in object
const { name: n, ...rest } = user;
// n='Alice', rest={ age: 30, city: 'Mumbai' }

// ─── IN FUNCTION PARAMETERS ───
function display({ name, age = 18, role = 'guest' }) {
  console.log(`${name}, ${age}, ${role}`);
}
display({ name: 'Bob', age: 25 });

// ─── FUNCTION RETURN ───
function getCoords() { return { x: 10, y: 20 }; }
const { x, y } = getCoords();
```

---

### Q136. What are Template Literals? What are Tagged Templates?

**Answer:**

**Template Literals** — String literals allowing embedded expressions and multi-line strings.

```js
const name = 'Alice';
const age = 30;

// Expression interpolation
const msg = `Hello, ${name}! You are ${age} years old.`;

// Multi-line strings (no \n needed)
const html = `
  <div class="card">
    <h2>${name}</h2>
    <p>Age: ${age}</p>
  </div>
`;

// Expressions inside ${}
const price = 100;
const tax = 0.18;
console.log(`Total: ₹${(price * (1 + tax)).toFixed(2)}`);

// Nested template literals
const items = ['JS', 'React', 'CSS'];
const list = `Skills: ${items.map(s => `<li>${s}</li>`).join('')}`;
```

**Tagged Templates** — A function that processes a template literal.

```js
function highlight(strings, ...values) {
  return strings.reduce((result, str, i) => {
    return result + str + (values[i] !== undefined
      ? `<mark>${values[i]}</mark>`
      : '');
  }, '');
}

const skill = 'JavaScript';
const years = 3;
const output = highlight`I know ${skill} for ${years} years.`;
// "I know <mark>JavaScript</mark> for <mark>3</mark> years."
```

Real-world tagged templates: `styled-components`, `gql` (GraphQL queries), `sql`.

---

### Q137. What are Default Parameters in functions?

**Answer:**
```js
// ES5 way — verbose
function greet(name) {
  name = name || 'Guest';
  return `Hello, ${name}!`;
}

// ES6 default parameters
function greet(name = 'Guest', greeting = 'Hello') {
  return `${greeting}, ${name}!`;
}
greet();               // "Hello, Guest!"
greet('Alice');        // "Hello, Alice!"
greet('Bob', 'Hi');   // "Hi, Bob!"

// Default can be an expression or function call
function createId(prefix = 'ID', num = Math.random()) {
  return `${prefix}-${num}`;
}

// Defaults can reference earlier params
function createRange(start, end = start + 10) {
  return [start, end];
}
createRange(5); // [5, 15]

// undefined triggers default; null does NOT
greet(undefined); // "Hello, Guest!" — default used
greet(null);      // "Hello, null!" — null is a value, no default
```

---

### Q138. What are ES6 Modules (`import` / `export`)? Types of exports?

**Answer:**

```js
// ─── NAMED EXPORTS ───
// math.js
export const PI = 3.14159;
export function add(a, b) { return a + b; }
export function multiply(a, b) { return a * b; }

// Import named
import { add, multiply } from './math.js';
import { add as sum } from './math.js';        // Alias
import * as MathUtils from './math.js';         // Namespace import

// ─── DEFAULT EXPORT ───
// One per file
export default function App() { return <div>App</div>; }

// Import default (any name)
import App from './App.js';
import MyApp from './App.js';  // Can rename freely

// ─── MIXED ───
export default class EventEmitter { }
export const VERSION = '1.0.0';

import EventEmitter, { VERSION } from './EventEmitter.js';

// ─── RE-EXPORTS ───
// index.js — barrel file
export { Button } from './Button.js';
export { default as Modal } from './Modal.js';
export * from './utils.js';

// ─── DYNAMIC IMPORTS ───
const module = await import('./heavyModule.js');
// Returns a promise — useful for code splitting
```

**ES Modules vs CommonJS:**

| | ES Modules | CommonJS |
|--|-----------|---------|
| Syntax | `import/export` | `require/module.exports` |
| Loading | Static (compile-time) | Dynamic (runtime) |
| Tree-shakeable | Yes | No |
| Browser native | Yes | No (needs bundler) |
| Top-level await | Yes | No |

---

### Q139. What are ES6 Classes? How do they relate to prototypes?

**Answer:**
ES6 classes are **syntactic sugar** over prototype-based inheritance. They don't introduce a new OOP model.

```js
class Animal {
  // Class field (ES2022 — public)
  species = 'Unknown';
  
  // Private field (ES2022)
  #health = 100;

  constructor(name, sound) {
    this.name = name;
    this.sound = sound;
  }

  // Instance method
  speak() {
    return `${this.name} says ${this.sound}`;
  }

  // Getter
  get info() {
    return `${this.name} (${this.species})`;
  }

  // Setter
  set nickname(val) {
    this.name = val.trim();
  }

  // Static method — called on class, not instance
  static create(name, sound) {
    return new Animal(name, sound);
  }

  // Private method
  #heal(amount) {
    this.#health = Math.min(100, this.#health + amount);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name, 'Woof');    // Must call super() first
    this.tricks = [];
  }

  learn(trick) {
    this.tricks.push(trick);
  }

  // Override parent method
  speak() {
    return `${super.speak()} and knows ${this.tricks.length} tricks`;
  }
}

const dog = new Dog('Rex');
dog.speak();      // "Rex says Woof and knows 0 tricks"
dog.learn('sit');
dog.speak();      // "Rex says Woof and knows 1 tricks"

// Under the hood — still prototypes!
Dog.prototype.__proto__ === Animal.prototype; // true
```

---

### Q140. What is the `for...of` loop? How is it different from `for...in`?

**Answer:**

```js
// for...of — iterates over VALUES of iterables (arrays, strings, maps, sets, generators)
const arr = [10, 20, 30];
for (const val of arr) {
  console.log(val); // 10, 20, 30
}

// Works on strings
for (const char of 'hello') {
  console.log(char); // h, e, l, l, o
}

// With Map
const map = new Map([['a', 1], ['b', 2]]);
for (const [key, val] of map) {
  console.log(key, val); // a 1, b 2
}

// for...in — iterates over KEYS (enumerable properties) of an object
const obj = { x: 1, y: 2, z: 3 };
for (const key in obj) {
  console.log(key); // x, y, z
}

// ⚠️ Pitfall: for...in also iterates inherited prototype properties
// Always use hasOwnProperty check or Object.keys() instead
for (const key in obj) {
  if (obj.hasOwnProperty(key)) { ... }
}
```

| | `for...of` | `for...in` |
|--|-----------|-----------|
| Iterates | Values | Keys/property names |
| Works on | Iterables (array, string, map, set) | Objects |
| Prototype chain | No | Yes (includes inherited) |

---

### Q141. What are Iterators and Iterables? How do they work?

**Answer:**
An **Iterable** is an object with a `[Symbol.iterator]()` method.
An **Iterator** is an object with a `next()` method returning `{ value, done }`.

```js
// Custom Iterable
const range = {
  from: 1,
  to: 5,
  [Symbol.iterator]() {
    let current = this.from;
    const last = this.to;
    return {
      next() {
        return current <= last
          ? { value: current++, done: false }
          : { value: undefined, done: true };
      }
    };
  }
};

for (const num of range) console.log(num); // 1 2 3 4 5
const arr = [...range]; // [1, 2, 3, 4, 5]

// Generator as iterator (cleaner)
function* rangeGen(from, to) {
  for (let i = from; i <= to; i++) yield i;
}
for (const n of rangeGen(1, 5)) console.log(n);
```

Built-in iterables: `Array`, `String`, `Map`, `Set`, `arguments`, DOM NodeList.

---

### Q142. What is `Symbol.iterator`, `Symbol.toPrimitive`, and other well-known Symbols?

**Answer:**
Symbols are used as unique keys that enable hooking into JS language internals.

```js
// Symbol.iterator — make an object iterable
class InfiniteCounter {
  [Symbol.iterator]() {
    let n = 0;
    return { next: () => ({ value: n++, done: false }) };
  }
}

// Symbol.toPrimitive — control type conversion
class Money {
  constructor(amount, currency) {
    this.amount = amount;
    this.currency = currency;
  }
  [Symbol.toPrimitive](hint) {
    if (hint === 'number') return this.amount;
    if (hint === 'string') return `${this.amount} ${this.currency}`;
    return this.amount; // default
  }
}
const price = new Money(100, 'USD');
+price;        // 100 (number hint)
`${price}`;   // "100 USD" (string hint)

// Symbol.hasInstance — customize instanceof
class EvenNumber {
  static [Symbol.hasInstance](num) {
    return num % 2 === 0;
  }
}
2 instanceof EvenNumber; // true
3 instanceof EvenNumber; // false

// Symbol.toStringTag — customize Object.prototype.toString
class Queue {
  get [Symbol.toStringTag]() { return 'Queue'; }
}
Object.prototype.toString.call(new Queue()); // "[object Queue]"
```

---

### Q143. What is the Nullish Coalescing operator (`??`) and Logical Assignment operators?

**Answer:**

```js
// ?? — returns right side only if left is null or undefined (NOT falsy)
const name = null ?? 'Guest';       // 'Guest'
const count = 0 ?? 10;              // 0 ← (0 is not null/undefined)
const text = '' ?? 'default';       // '' ← (empty string is not null/undefined)

// vs || (OR) — returns right side for ANY falsy value
const count2 = 0 || 10;             // 10 ← treats 0 as falsy
const text2 = '' || 'default';      // 'default' ← treats '' as falsy

// ??= (Nullish Assignment) — assign only if null/undefined
let user = null;
user ??= 'Guest';   // user = 'Guest'

let score = 0;
score ??= 100;      // score stays 0 (not null/undefined)

// ||= (Logical OR Assignment) — assign if falsy
let a = 0;
a ||= 42;           // a = 42 (0 is falsy)

// &&= (Logical AND Assignment) — assign if truthy
let b = 5;
b &&= b * 2;        // b = 10 (5 is truthy, so assign)

let c = 0;
c &&= c * 2;        // c stays 0 (0 is falsy, short-circuit)
```

---

### Q144. What is Optional Chaining (`?.`) in depth?

**Answer:**
```js
const user = {
  name: 'Alice',
  address: {
    street: '123 MG Road'
    // no city property
  },
  getFullName: () => 'Alice Smith'
};

// Without optional chaining — verbose and error-prone
const city = user && user.address && user.address.city;

// With optional chaining
const city = user?.address?.city;           // undefined (no error)
const zip  = user?.address?.zipCode;        // undefined

// Method calls
const fullName = user?.getFullName?.();     // 'Alice Smith'
const missing  = user?.nonExistentMethod?.(); // undefined

// Array indexing
const users = [{ name: 'Alice' }];
const secondUser = users?.[1]?.name;        // undefined (safe)

// Combined with nullish coalescing
const displayCity = user?.address?.city ?? 'City not set';
// 'City not set'

// Practical: optional chaining with dynamic keys
const key = 'name';
user?.[key];  // 'Alice'
```

---

### Q145. What are Getters and Setters in JavaScript objects?

**Answer:**
```js
// Object literal
const circle = {
  _radius: 5,
  get radius() { return this._radius; },
  set radius(val) {
    if (val < 0) throw new RangeError('Radius must be positive');
    this._radius = val;
  },
  get area() {
    return Math.PI * this._radius ** 2; // Computed property, no setter
  }
};

circle.radius;       // 5 — getter called
circle.radius = 10;  // setter called
circle.area;         // 314.159... — computed on access

// Class-based getters/setters
class Temperature {
  #celsius;
  
  constructor(celsius) { this.#celsius = celsius; }
  
  get fahrenheit() { return this.#celsius * 9/5 + 32; }
  set fahrenheit(f) { this.#celsius = (f - 32) * 5/9; }
  
  get celsius() { return this.#celsius; }
  set celsius(c) { this.#celsius = c; }
}

const temp = new Temperature(100);
temp.fahrenheit; // 212
temp.fahrenheit = 32;
temp.celsius;    // 0
```

---

### Q146. What is `Object.freeze()` vs `Object.seal()` vs `const`?

**Answer:**

```js
// const — prevents reassignment of the variable, NOT mutation of the value
const obj = { a: 1 };
obj.a = 2;   // ✅ allowed — mutating the object
obj = {};    // ❌ TypeError — reassignment blocked

// Object.freeze() — prevents ALL modifications (add, delete, modify)
const frozen = Object.freeze({ a: 1, b: 2 });
frozen.a = 99;     // Silent fail (or TypeError in strict mode)
frozen.c = 3;      // Silent fail
delete frozen.a;   // Silent fail
console.log(frozen); // { a: 1, b: 2 } — unchanged

// ⚠️ Shallow freeze — nested objects are NOT frozen
const obj2 = Object.freeze({ nested: { x: 1 } });
obj2.nested.x = 99; // ✅ Works! nested is not frozen

// Object.seal() — prevents add/delete, but allows MODIFYING existing properties
const sealed = Object.seal({ a: 1, b: 2 });
sealed.a = 99;     // ✅ allowed — modifying existing
sealed.c = 3;      // ❌ silent fail — can't add
delete sealed.a;   // ❌ silent fail — can't delete

// Check
Object.isFrozen(frozen); // true
Object.isSealed(sealed); // true
Object.isExtensible(obj); // true (can add properties)
```

---

### Q147. What is `Object.create()` and how does it differ from `new`?

**Answer:**
```js
// Object.create(proto) — creates a new object with proto as its prototype
const personProto = {
  greet() { return `Hi, I'm ${this.name}`; }
};

const alice = Object.create(personProto);
alice.name = 'Alice';
alice.greet(); // "Hi, I'm Alice"

// Object.create(null) — creates object with NO prototype chain
const pureMap = Object.create(null);
pureMap.key = 'value';
// No toString, hasOwnProperty, etc. — useful as a pure hash map

// vs 'new' keyword
function Person(name) { this.name = name; }
Person.prototype.greet = function() { return `Hi, I'm ${this.name}`; };

const bob = new Person('Bob');
// new: creates object, sets __proto__ to Person.prototype, calls constructor

// Under the hood, new does:
function simulateNew(Constructor, ...args) {
  const obj = Object.create(Constructor.prototype);
  const result = Constructor.apply(obj, args);
  return result instanceof Object ? result : obj;
}
```

---

## 🔶 FUNCTIONAL PROGRAMMING IN JS

### Q148. What is a Pure Function? What are Side Effects?

**Answer:**
A **pure function**:
1. Same inputs → always same output (deterministic)
2. No side effects

```js
// ✅ Pure function
function add(a, b) { return a + b; }
function formatName(first, last) { return `${first} ${last}`; }

// ❌ Impure — reads external state
let tax = 0.18;
function getPrice(amount) { return amount * (1 + tax); } // Depends on external 'tax'

// ❌ Impure — mutates input
function addItem(cart, item) {
  cart.push(item);  // Mutates the array!
  return cart;
}

// ✅ Pure version — returns new array
function addItem(cart, item) {
  return [...cart, item]; // Creates new array
}
```

**Side Effects** — Things a function does beyond returning a value:
- Modifying external state
- DOM manipulation
- API calls (I/O)
- Console.log
- Modifying its arguments

---

### Q149. What is Currying? Show a practical example.

**Answer:**
Currying transforms a function with multiple arguments into a sequence of functions, each taking a single argument.

```js
// Normal function
function multiply(a, b) { return a * b; }

// Curried version
function curriedMultiply(a) {
  return function(b) {
    return a * b;
  };
}

// ES6 arrow style
const curry = a => b => a * b;

const double = curry(2);
const triple = curry(3);

double(5); // 10
triple(5); // 15

// Generic curry utility
function curryN(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn.apply(this, args);
    }
    return function(...moreArgs) {
      return curried.apply(this, args.concat(moreArgs));
    };
  };
}

// Practical use case — reusable event handlers
const handleEvent = (type) => (handler) => (event) => {
  if (event.type === type) handler(event);
};

const onSubmit = handleEvent('submit');
const logSubmit = onSubmit((e) => console.log('Form submitted', e));
```

---

### Q150. What is function composition? What is `pipe` vs `compose`?

**Answer:**
Function composition combines multiple functions so the output of one is the input of the next.

```js
// compose — right to left (mathematical convention: f ∘ g = f(g(x)))
const compose = (...fns) => x => fns.reduceRight((v, f) => f(v), x);

// pipe — left to right (more readable for most developers)
const pipe = (...fns) => x => fns.reduce((v, f) => f(v), x);

// Example
const trim      = str => str.trim();
const lowercase = str => str.toLowerCase();
const addDash   = str => str.replace(/\s+/g, '-');
const truncate  = str => str.slice(0, 20);

// pipe reads left-to-right — trim first, then lowercase, then dash, then truncate
const slugify = pipe(trim, lowercase, addDash, truncate);
slugify('  Hello World From React  '); // "hello-world-from-re"

// Async pipe
const asyncPipe = (...fns) => x => fns.reduce(async (v, f) => f(await v), x);

const processUser = asyncPipe(
  validateUser,
  hashPassword,
  saveToDatabase,
  sendWelcomeEmail
);
```

---

### Q151. What are IIFEs? When are they used?

**Answer:**
An IIFE (Immediately Invoked Function Expression) runs as soon as it's defined.

```js
// Classic IIFE syntax
(function() {
  const privateVar = 'I am private';
  console.log('Runs immediately!');
})();

// Arrow function IIFE
(() => {
  console.log('Arrow IIFE');
})();

// IIFE with parameters
(function(global, factory) {
  factory(global);
})(window, function(win) {
  win.myLib = { version: '1.0' };
});

// Async IIFE — common in module setup
(async () => {
  const data = await fetchInitialData();
  initApp(data);
})();
```

**Use cases:**
- Avoid polluting global scope (before ES modules)
- Create private scope/variables
- Initialize async operations at module level
- Library wrappers (jQuery, lodash pattern)

---

### Q152. What is Memoization? How does it differ from Caching?

**Answer:**

```js
// Memoization — caching function results based on inputs
function memoize(fn) {
  const cache = new Map();
  return function(...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) return cache.get(key);
    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

// Example: Fibonacci with memoization
const fib = memoize(function(n) {
  if (n <= 1) return n;
  return fib(n - 1) + fib(n - 2); // Uses memoized version!
});

fib(40); // Computed in milliseconds vs seconds without memoization

// Memoization with WeakMap for object arguments (avoids memory leaks)
function memoizeWeak(fn) {
  const cache = new WeakMap();
  return function(obj) {
    if (cache.has(obj)) return cache.get(obj);
    const result = fn(obj);
    cache.set(obj, result);
    return result;
  };
}
```

**Memoization vs Caching:**
- Memoization: Specific to pure functions, keys are function arguments
- Caching: General term, can be for any data (HTTP responses, DB queries, etc.)

---

### Q153. What is Immutability in JavaScript? Why does it matter?

**Answer:**
Immutability means not modifying data after creation — instead, creating new copies.

```js
// ❌ Mutable approach — mutates original
function addSkill(user, skill) {
  user.skills.push(skill);     // Mutates!
  return user;
}

// ✅ Immutable approach — creates new objects
function addSkill(user, skill) {
  return {
    ...user,
    skills: [...user.skills, skill]  // New array
  };
}

// Immutable array operations
const arr = [1, 2, 3, 4, 5];

// Add
const withNew = [...arr, 6];              // [1,2,3,4,5,6]

// Remove by index
const without3 = arr.filter((_, i) => i !== 2); // [1,2,4,5]

// Update by index
const updated = arr.map((v, i) => i === 2 ? 99 : v); // [1,2,99,4,5]

// Immutable object updates
const user = { name: 'Alice', address: { city: 'Mumbai' } };

// Shallow update
const renamed = { ...user, name: 'Bob' };

// Deep update (nested)
const movedCity = {
  ...user,
  address: { ...user.address, city: 'Delhi' }
};
```

**Why it matters:**
- Predictable state (no surprise mutations)
- Easy change detection (reference equality check)
- Required for React state updates, Redux
- Enables undo/redo patterns

---

## 🔶 ERROR HANDLING

### Q154. How does Error Handling work in JavaScript? Types of Errors?

**Answer:**

```js
// Built-in Error types
new Error('generic error');
new TypeError('wrong type');          // null.property, wrong argument type
new ReferenceError('not defined');    // accessing undeclared variable
new SyntaxError('invalid syntax');    // parse time error
new RangeError('out of range');       // array length -1, toFixed(200)
new URIError('bad URI');
new EvalError('eval error');

// try / catch / finally
function riskyOperation(input) {
  try {
    if (typeof input !== 'number') {
      throw new TypeError(`Expected number, got ${typeof input}`);
    }
    return JSON.parse(input);
  } catch (error) {
    if (error instanceof TypeError) {
      console.error('Type problem:', error.message);
    } else if (error instanceof SyntaxError) {
      console.error('Parse problem:', error.message);
    } else {
      throw error; // Re-throw unknown errors
    }
  } finally {
    console.log('Always runs — cleanup here');
  }
}

// Custom Error class
class ValidationError extends Error {
  constructor(message, field) {
    super(message);
    this.name = 'ValidationError';
    this.field = field;
  }
}

throw new ValidationError('Email is invalid', 'email');

// Async error handling
async function fetchUser(id) {
  try {
    const res = await fetch(`/api/users/${id}`);
    if (!res.ok) throw new Error(`HTTP ${res.status}: ${res.statusText}`);
    return await res.json();
  } catch (err) {
    console.error('Fetch failed:', err.message);
    throw err; // Re-throw so caller can handle
  }
}
```

---

### Q155. What is error bubbling in async code? How to handle it properly?

**Answer:**
```js
// ❌ Unhandled promise rejection — crash in Node, silent in browser
fetch('/api/data').then(r => r.json()); // No .catch!

// ✅ Global handler as safety net
window.addEventListener('unhandledrejection', (event) => {
  console.error('Unhandled:', event.reason);
  event.preventDefault();
});

// ✅ Async error boundary pattern
async function withErrorHandling(fn, fallback) {
  try {
    return await fn();
  } catch (err) {
    console.error(err);
    return fallback;
  }
}

const data = await withErrorHandling(() => fetchData(), []);

// ✅ Result pattern (like Rust's Result type)
async function safeAsync(promise) {
  try {
    const data = await promise;
    return [null, data];
  } catch (err) {
    return [err, null];
  }
}

const [error, users] = await safeAsync(fetchUsers());
if (error) { /* handle */ return; }
// use users safely
```

---

## 🔶 THE DOM & BROWSER APIs

### Q156. What is the DOM? Explain common DOM manipulation methods.

**Answer:**
The DOM (Document Object Model) is a tree-like representation of the HTML document that JS can interact with.

```js
// ─── SELECTING ELEMENTS ───
document.getElementById('myId');
document.querySelector('.class');           // First match
document.querySelectorAll('div.card');      // All matches (NodeList)
document.getElementsByClassName('card');    // Live HTMLCollection
document.getElementsByTagName('p');

// ─── CREATING & INSERTING ───
const div = document.createElement('div');
div.className = 'card';
div.textContent = 'Hello';
div.setAttribute('data-id', '42');

// Modern insertion methods
parent.append(div);          // Insert as last child (accepts strings too)
parent.prepend(div);         // Insert as first child
element.before(div);         // Insert before element
element.after(div);          // Insert after element
element.replaceWith(div);    // Replace element

// ─── READING & MODIFYING ───
element.textContent = 'New text';    // Text only (XSS-safe)
element.innerHTML = '<b>Bold</b>';   // Parses HTML (⚠️ XSS risk)
element.getAttribute('href');
element.setAttribute('disabled', '');
element.removeAttribute('disabled');
element.classList.add('active');
element.classList.remove('hidden');
element.classList.toggle('open');
element.classList.contains('active'); // boolean

// ─── REMOVING ───
element.remove();
parent.removeChild(child);

// ─── TRAVERSAL ───
element.parentElement;
element.children;           // Direct children (elements only)
element.childNodes;         // All nodes including text nodes
element.firstElementChild;
element.lastElementChild;
element.nextElementSibling;
element.previousElementSibling;
```

---

### Q157. What is Event Bubbling, Capturing, and `stopPropagation`?

**Answer:**
When an event fires on an element, it propagates through the DOM in two phases:

```
Capturing phase: window → document → html → body → div → button
Target phase:    button (event fires here)
Bubbling phase:  button → div → body → html → document → window
```

```js
// Default: addEventListener listens in BUBBLE phase
element.addEventListener('click', handler);           // Bubble phase
element.addEventListener('click', handler, false);    // Bubble phase (explicit)
element.addEventListener('click', handler, true);     // Capture phase

// Stop bubbling — event won't travel up to parent handlers
button.addEventListener('click', (e) => {
  e.stopPropagation();    // Stop this event from bubbling
  handleClick(e);
});

// Stop ALL handlers on this element AND stop bubbling
button.addEventListener('click', (e) => {
  e.stopImmediatePropagation();
});

// Prevent default browser behavior (form submit, link navigation, etc.)
form.addEventListener('submit', (e) => {
  e.preventDefault();  // Stops form from refreshing page
  validateAndSubmit();
});

link.addEventListener('click', (e) => {
  e.preventDefault();  // Stop navigation
  handleRouting(e);
});

// Check where event originated
parent.addEventListener('click', (e) => {
  console.log(e.target);    // Element that was CLICKED (origin)
  console.log(e.currentTarget); // Element this handler is attached to
});
```

---

### Q158. What is `requestAnimationFrame`? When to use it over `setTimeout`?

**Answer:**
`requestAnimationFrame` (rAF) schedules a callback before the browser's next repaint (~60fps).

```js
// ❌ setTimeout for animation — inconsistent, may cause jank
function badAnimate() {
  element.style.left = (parseFloat(element.style.left) + 1) + 'px';
  setTimeout(badAnimate, 16); // Not synced to display refresh rate
}

// ✅ requestAnimationFrame — smooth, synced to display
function animate(timestamp) {
  const progress = timestamp - startTime;
  const position = Math.min(progress / duration, 1) * 300; // 0 to 300px
  
  element.style.transform = `translateX(${position}px)`;
  
  if (progress < duration) {
    requestAnimationFrame(animate); // Schedule next frame
  }
}

let startTime;
requestAnimationFrame((ts) => { startTime = ts; animate(ts); });

// Cancel animation
const frameId = requestAnimationFrame(animate);
cancelAnimationFrame(frameId);

// rAF also pauses when tab is not visible — saves battery/CPU
```

---

### Q159. What is the MutationObserver API?

**Answer:**
`MutationObserver` watches for changes to the DOM tree.

```js
const observer = new MutationObserver((mutations) => {
  mutations.forEach(mutation => {
    if (mutation.type === 'childList') {
      console.log('Child nodes changed:', mutation.addedNodes, mutation.removedNodes);
    }
    if (mutation.type === 'attributes') {
      console.log(`Attribute "${mutation.attributeName}" changed`);
    }
    if (mutation.type === 'characterData') {
      console.log('Text content changed');
    }
  });
});

// Start observing
observer.observe(targetElement, {
  childList: true,      // Watch for added/removed children
  attributes: true,     // Watch for attribute changes
  characterData: true,  // Watch for text changes
  subtree: true,        // Watch all descendants (not just direct children)
  attributeOldValue: true, // Record old attribute value
});

// Stop observing
observer.disconnect();

// Use cases: 
// - Detect when a third-party widget inserts elements
// - Watch for class changes on body (theme switches)
// - Auto-resize textareas
// - Implementing custom virtual scroll
```

---

### Q160. What is the IntersectionObserver API? What are its use cases?

**Answer:**
`IntersectionObserver` watches when elements enter or leave the viewport (or a parent element).

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      // Element is visible in viewport
      entry.target.classList.add('visible');
      observer.unobserve(entry.target); // Stop watching once visible
    }
  });
}, {
  root: null,           // null = viewport
  rootMargin: '0px',    // Expand/shrink the intersection area
  threshold: 0.5        // Fire when 50% of element is visible
});

// Observe all elements with .animate class
document.querySelectorAll('.animate').forEach(el => observer.observe(el));

// ─── USE CASES ───

// 1. Lazy load images
const imgObserver = new IntersectionObserver(entries => {
  entries.forEach(({ isIntersecting, target }) => {
    if (isIntersecting) {
      target.src = target.dataset.src;
      imgObserver.unobserve(target);
    }
  });
});

// 2. Infinite scroll (trigger load when sentinel is visible)
const sentinel = document.querySelector('#sentinel');
observer.observe(sentinel);

// 3. Analytics — track what content was actually seen
// 4. Sticky header shadow — add shadow when scrolled
// 5. Progress indicators for reading
```

---

## 🔶 ADVANCED JS PATTERNS

### Q161. What are Design Patterns? Explain the most common ones.

**Answer:**

**Singleton Pattern** — Ensure only one instance of a class exists.
```js
class Database {
  static #instance = null;
  
  constructor(url) {
    if (Database.#instance) return Database.#instance;
    this.connection = connect(url);
    Database.#instance = this;
  }
  
  static getInstance(url) {
    if (!Database.#instance) new Database(url);
    return Database.#instance;
  }
}

const db1 = new Database('mongodb://...');
const db2 = new Database('other://...');
db1 === db2; // true — same instance
```

**Observer Pattern** — Pub/Sub, notify subscribers of changes.
```js
class EventBus {
  #listeners = {};
  
  on(event, cb) {
    (this.#listeners[event] ??= []).push(cb);
    return () => this.off(event, cb);
  }
  off(event, cb) {
    this.#listeners[event] = this.#listeners[event]?.filter(l => l !== cb);
  }
  emit(event, data) {
    this.#listeners[event]?.forEach(cb => cb(data));
  }
}
```

**Factory Pattern** — Create objects without specifying exact class.
```js
function createUser(type) {
  const base = { createdAt: Date.now() };
  const roles = {
    admin:  { ...base, canDelete: true,  canEdit: true  },
    editor: { ...base, canDelete: false, canEdit: true  },
    viewer: { ...base, canDelete: false, canEdit: false }
  };
  return roles[type] ?? roles.viewer;
}
```

**Decorator Pattern** — Add behavior to objects dynamically.
```js
function readonly(target, key, descriptor) {
  descriptor.writable = false;
  return descriptor;
}

function log(fn) {
  return function(...args) {
    console.log(`Calling ${fn.name} with`, args);
    const result = fn(...args);
    console.log(`Result:`, result);
    return result;
  };
}

const loggedAdd = log(add);
loggedAdd(2, 3); // Logs args and result
```

---

### Q162. What is the Module Pattern in JavaScript?

**Answer:**
The Module Pattern uses closures to create private state — important before ES modules.

```js
// IIFE Module pattern
const Counter = (function() {
  let _count = 0;    // Private

  return {
    increment() { _count++; },
    decrement() { _count--; },
    getCount()  { return _count; },
    reset()     { _count = 0; }
  };
})();

Counter.increment();
Counter.increment();
Counter.getCount(); // 2
Counter._count;     // undefined — private!

// Revealing Module pattern
const UserStore = (function() {
  let users = [];
  
  function addUser(user)     { users.push(user); }
  function removeUser(id)    { users = users.filter(u => u.id !== id); }
  function getAll()          { return [...users]; } // Return copy!
  function findById(id)      { return users.find(u => u.id === id); }
  
  // Reveal only what should be public
  return { add: addUser, remove: removeUser, getAll, findById };
})();
```

---

### Q163. What is the difference between `Object.assign()` and spread operator for merging?

**Answer:**
```js
const defaults = { theme: 'light', lang: 'en', fontSize: 14 };
const userPrefs = { theme: 'dark', notifications: true };

// Object.assign — mutates the TARGET object
const merged1 = Object.assign({}, defaults, userPrefs);
// { theme: 'dark', lang: 'en', fontSize: 14, notifications: true }

// Object.assign MODIFIES first argument!
Object.assign(defaults, userPrefs);  // ⚠️ defaults is now mutated

// Spread — always creates new object (no mutation)
const merged2 = { ...defaults, ...userPrefs };
// Same result, but defaults is untouched

// Key difference: Object.assign triggers setters on target
const obj = {
  set value(v) { this._v = v * 2; }
};
Object.assign(obj, { value: 5 }); // Triggers setter → _v = 10
const spread = { ...obj, value: 5 }; // Copies directly → value: 5, no setter

// Both are SHALLOW — nested objects are still references
const deep = { a: { b: 1 } };
const copy = { ...deep };
copy.a.b = 999;
console.log(deep.a.b); // 999 — still linked!
```

---

### Q164. What is `typeof` vs `instanceof` vs `Array.isArray()`?

**Answer:**
```js
// typeof — returns string, works for primitives
typeof 42;          // "number"
typeof "hello";     // "string"
typeof true;        // "boolean"
typeof undefined;   // "undefined"
typeof Symbol();    // "symbol"
typeof 42n;         // "bigint"
typeof function(){}; // "function"
typeof {};          // "object"
typeof [];          // "object"  ← can't distinguish
typeof null;        // "object"  ← famous bug

// instanceof — checks prototype chain, works for objects
[] instanceof Array;       // true
[] instanceof Object;      // true (Array extends Object)
{} instanceof Object;      // true
new Date() instanceof Date; // true

// ⚠️ instanceof fails across iframes/realms
// The Array from another iframe is a different Array constructor

// Array.isArray() — reliable, works across realms
Array.isArray([]);          // true
Array.isArray({});          // false
Array.isArray('string');    // false
Array.isArray(new Array()); // true

// Object.prototype.toString — most reliable type check
Object.prototype.toString.call([]);         // "[object Array]"
Object.prototype.toString.call(null);       // "[object Null]"
Object.prototype.toString.call(undefined);  // "[object Undefined]"
Object.prototype.toString.call(new Date()); // "[object Date]"
Object.prototype.toString.call(/regex/);    // "[object RegExp]"
```

---

### Q165. What are the different ways to create objects in JavaScript?

**Answer:**
```js
// 1. Object literal
const obj1 = { name: 'Alice', age: 30 };

// 2. Constructor function
function Person(name) { this.name = name; }
const obj2 = new Person('Bob');

// 3. ES6 Class
class User { constructor(name) { this.name = name; } }
const obj3 = new User('Charlie');

// 4. Object.create() — set prototype explicitly
const proto = { greet() { return `Hi ${this.name}`; } };
const obj4 = Object.create(proto);
obj4.name = 'Dave';

// 5. Factory function — no 'new' needed
function createAnimal(name, sound) {
  return { name, sound, speak() { return `${this.name}: ${this.sound}`; } };
}
const obj5 = createAnimal('Cat', 'Meow');

// 6. Object.assign()
const obj6 = Object.assign({}, { a: 1 }, { b: 2 });

// 7. Computed property names (ES6)
const key = 'dynamicKey';
const obj7 = { [key]: 'value', [`prefix_${key}`]: 'prefixed' };

// 8. Shorthand property names (ES6)
const name = 'Alice';
const age = 30;
const obj8 = { name, age }; // Same as { name: name, age: age }
```

---

### Q166. What is `structuredClone()`? When was it introduced?

**Answer:**
`structuredClone()` was introduced natively in browsers and Node.js 17+ as the standard way to deep clone objects.

```js
// ✅ structuredClone — deep clone, handles most types
const original = {
  name: 'Alice',
  scores: [95, 87, 92],
  metadata: { created: new Date(), tags: ['react', 'js'] }
};

const clone = structuredClone(original);
clone.scores.push(100);
clone.metadata.tags.push('ts');

console.log(original.scores);        // [95, 87, 92] — untouched
console.log(original.metadata.tags); // ['react', 'js'] — untouched

// Supported types: Date, RegExp, Map, Set, ArrayBuffer, typed arrays, Error
const map = new Map([['a', 1]]);
const mapClone = structuredClone(map); // ✅ Works!

// ❌ Does NOT support: functions, DOM nodes, WeakMap, class instances (loses methods)
const fn = () => {};
structuredClone(fn); // ❌ DataCloneError

// vs JSON.parse(JSON.stringify())
const jsonClone = JSON.parse(JSON.stringify(original));
// ❌ Loses: undefined, functions, Date (becomes string), Map, Set, circular refs
```

---

### Q167. What are JavaScript Typed Arrays? What is ArrayBuffer?

**Answer:**
Typed Arrays provide array-like access to raw binary data.

```js
// ArrayBuffer — raw binary data (fixed-size)
const buffer = new ArrayBuffer(16); // 16 bytes

// Views — typed access to the buffer
const int32 = new Int32Array(buffer);   // 4 elements (4 bytes each)
const uint8 = new Uint8Array(buffer);   // 16 elements (1 byte each)
// Both point to the SAME underlying buffer!

int32[0] = 42;
console.log(uint8[0]); // 42 (low byte of 42)

// Common Typed Arrays
new Int8Array(length);    // 8-bit signed integer
new Uint8Array(length);   // 8-bit unsigned integer
new Int16Array(length);   // 16-bit signed
new Int32Array(length);   // 32-bit signed
new Float32Array(length); // 32-bit float
new Float64Array(length); // 64-bit float (like JS numbers)

// Use cases: WebGL, canvas pixel manipulation, Web Audio, binary protocols (WebSockets, File API)
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
const imageData = ctx.getImageData(0, 0, width, height);
const pixels = imageData.data; // Uint8ClampedArray — RGBA values
```

---

### Q168. What is the `Reflect` API?

**Answer:**
`Reflect` provides methods for interceptable JS operations, mirroring the `Proxy` traps.

```js
// Reflect has the same methods as Proxy handler traps
// Useful inside Proxy handlers to apply default behavior

const handler = {
  get(target, prop, receiver) {
    console.log(`Accessing: ${prop}`);
    return Reflect.get(target, prop, receiver); // Default get behavior
  },
  set(target, prop, value, receiver) {
    console.log(`Setting: ${prop} = ${value}`);
    return Reflect.set(target, prop, value, receiver); // Default set
  },
  deleteProperty(target, prop) {
    console.log(`Deleting: ${prop}`);
    return Reflect.deleteProperty(target, prop);
  }
};

const obj = new Proxy({ a: 1 }, handler);
obj.a;        // "Accessing: a"
obj.b = 2;    // "Setting: b = 2"

// Reflect.ownKeys — gets ALL own keys (string + Symbol)
const sym = Symbol('id');
const obj2 = { name: 'Alice', [sym]: 42 };
Reflect.ownKeys(obj2); // ['name', Symbol(id)]

// vs Object.keys — only enumerable string keys
Object.keys(obj2);     // ['name']
```

---

### Q169. What is `eval()`? Why should you avoid it?

**Answer:**
`eval()` executes a string as JavaScript code.

```js
eval('2 + 2'); // 4
eval('const x = 10; x * 2'); // 20

// ❌ Why to AVOID it:
// 1. Security — executes arbitrary code (XSS vector)
const userInput = 'alert("hacked!")';
eval(userInput); // Executes attacker code!

// 2. Performance — prevents JS engine optimizations
// V8 can't optimize code that uses eval (can't determine scope at compile time)

// 3. Debugging — hard to trace errors in eval'd code

// 4. Strict mode restrictions
'use strict';
eval('var x = 1');
console.log(typeof x); // undefined — eval has own scope in strict mode

// ✅ Alternatives
// Dynamic property access
const key = 'name';
obj[key];           // Instead of eval(`obj.${key}`)

// JSON parsing
JSON.parse('{"a":1}');   // Instead of eval('({"a":1})')

// Function constructor (slightly less dangerous than eval)
const fn = new Function('a', 'b', 'return a + b;');
fn(2, 3); // 5
```

---

### Q170. What are the different string methods in ES6+?

**Answer:**
```js
const str = '  Hello, World!  ';

// ─── ES5 classics ───
str.length;                  // 17
str.toUpperCase();           // '  HELLO, WORLD!  '
str.toLowerCase();           // '  hello, world!  '
str.trim();                  // 'Hello, World!'
str.trimStart();             // 'Hello, World!  '
str.trimEnd();               // '  Hello, World!'
str.indexOf('World');        // 9
str.includes('World');       // true
str.split(', ');             // ['  Hello', 'World!  ']
str.replace('World', 'JS'); // '  Hello, JS!  '
str.slice(2, 7);             // 'Hello'
str.substring(2, 7);         // 'Hello'
str.charAt(2);               // 'H'
str.charCodeAt(2);           // 72

// ─── ES6+ additions ───
'abc'.startsWith('ab');      // true
'abc'.endsWith('bc');        // true
'ha'.repeat(3);              // 'hahaha'
'5'.padStart(4, '0');        // '0005'
'5'.padEnd(4, '0');          // '5000'

// ES2021
'a::b::c'.replaceAll('::', '-'); // 'a-b-c'

// ─── String and Array interplay ───
'hello'.split('').reverse().join(''); // 'olleh'

// ─── Template literal methods ───
String.raw`Hello\nWorld`;  // 'Hello\\nWorld' — no escape processing

// ─── at() — ES2022 ───
'hello'.at(0);   // 'h'
'hello'.at(-1);  // 'o' — last character (negative index!)
```

---

### Q171. What are the key Array methods added in ES6+?

**Answer:**
```js
const nums = [1, 2, 3, 4, 5];

// ─── ES6 ───
Array.from({ length: 3 }, (_, i) => i + 1); // [1, 2, 3]
Array.of(1, 2, 3);                           // [1, 2, 3]

nums.find(n => n > 3);        // 4 (first match)
nums.findIndex(n => n > 3);   // 3 (index of first match)
nums.includes(3);              // true
nums.fill(0, 2, 4);            // [1, 2, 0, 0, 5] — fill from index 2 to 4
[[1, 2], [3, 4]].flat();       // [1, 2, 3, 4]
[[1, [2, 3]]].flat(Infinity);  // [1, 2, 3] — deep flatten
[1, 2, 3].flatMap(x => [x, x * 2]); // [1, 2, 2, 4, 3, 6]

// ─── ES2019 ───
[1, [2, [3]]].flat();           // [1, 2, [3]] — default depth 1
[1, [2, [3]]].flat(2);          // [1, 2, 3]

// ─── ES2022 ───
nums.at(0);     // 1
nums.at(-1);    // 5 — last element (clean!)
nums.at(-2);    // 4

// ─── ES2023 ───
nums.findLast(n => n < 4);      // 3 (searches from end)
nums.findLastIndex(n => n < 4); // 2

// toSorted, toReversed, toSpliced, with — NON-MUTATING versions
const arr = [3, 1, 2];
const sorted = arr.toSorted();  // [1, 2, 3] — arr unchanged
const reversed = arr.toReversed(); // [2, 1, 3] — arr unchanged
const updated = arr.with(1, 99);   // [3, 99, 2] — change index 1

// ─── Iteration helpers ───
nums.every(n => n > 0);  // true — all pass?
nums.some(n => n > 4);   // true — any pass?
nums.entries();          // Iterator of [index, value] pairs
nums.keys();             // Iterator of indices
nums.values();           // Iterator of values
```

---

### Q172. What are the key Object methods in ES6+?

**Answer:**
```js
const obj = { a: 1, b: 2, c: 3 };

// ─── Iteration ───
Object.keys(obj);     // ['a', 'b', 'c']
Object.values(obj);   // [1, 2, 3]
Object.entries(obj);  // [['a',1], ['b',2], ['c',3]]

// ─── Creation ───
Object.fromEntries([['a', 1], ['b', 2]]); // { a: 1, b: 2 }
Object.fromEntries(new Map([['key', 'val']]));

// Transform objects with entries
const doubled = Object.fromEntries(
  Object.entries(obj).map(([k, v]) => [k, v * 2])
); // { a: 2, b: 4, c: 6 }

// ─── Property descriptors ───
Object.defineProperty(obj, 'id', {
  value: 42,
  writable: false,
  enumerable: false,  // Won't appear in Object.keys
  configurable: false // Can't be changed/deleted
});

Object.getOwnPropertyDescriptor(obj, 'a');
// { value: 1, writable: true, enumerable: true, configurable: true }

Object.getOwnPropertyNames(obj);   // All own string props (incl. non-enumerable)
Object.getOwnPropertySymbols(obj); // Own symbol props

// ─── Prototype ───
Object.getPrototypeOf(obj);        // Object.prototype
Object.setPrototypeOf(obj, proto); // Change prototype (avoid in hot paths)

// ─── Checking ───
Object.is(NaN, NaN);     // true (unlike ===)
Object.is(0, -0);        // false (unlike ===)
obj.hasOwnProperty('a'); // true
Object.hasOwn(obj, 'a'); // true (ES2022 — preferred, avoids prototype issues)
```

---

### Q173. What is the difference between `for...in`, `Object.keys()`, and `Object.getOwnPropertyNames()`?

**Answer:**
```js
function Animal(name) { this.name = name; }
Animal.prototype.speak = function() { return 'sound'; };

const dog = new Animal('Rex');
Object.defineProperty(dog, 'secret', { value: 'hidden', enumerable: false });

// for...in — own + INHERITED enumerable properties
for (const key in dog) console.log(key);
// 'name', 'speak' ← includes inherited!

// Object.keys() — own ENUMERABLE properties only
Object.keys(dog);  // ['name'] — no secret (non-enum), no speak (inherited)

// Object.getOwnPropertyNames() — ALL own properties (incl. non-enumerable)
Object.getOwnPropertyNames(dog); // ['name', 'secret'] — no speak (inherited)

// Reflect.ownKeys() — ALL own properties including Symbols
const sym = Symbol('id');
dog[sym] = 1;
Reflect.ownKeys(dog); // ['name', 'secret', Symbol(id)]

// In summary:
// for...in:                    inherited + own + enumerable
// Object.keys():               own + enumerable
// Object.getOwnPropertyNames():own + enumerable + non-enumerable (no symbols)
// Reflect.ownKeys():           own + all strings + all symbols
```

---

### Q174. What are WeakRef and FinalizationRegistry?

**Answer:**
Introduced in ES2021, these give JS code a way to interact with the garbage collector.

```js
// WeakRef — holds a weak reference to an object (doesn't prevent GC)
let user = { name: 'Alice', data: new Array(1000000) };
const weakRef = new WeakRef(user);

// Access the object (may have been GC'd)
const obj = weakRef.deref();
if (obj) {
  console.log(obj.name); // 'Alice' (if not GC'd)
} else {
  console.log('Object was garbage collected');
}

// FinalizationRegistry — run callback when object is GC'd
const registry = new FinalizationRegistry((name) => {
  console.log(`${name} was garbage collected`);
});

let resource = { name: 'BigResource' };
registry.register(resource, resource.name);

resource = null; // Eligible for GC
// Eventually: "BigResource was garbage collected"

// ⚠️ Use with caution — GC timing is non-deterministic
// Primary use: cleanup of external resources (file handles, native objects)
```

---

### Q175. What is the difference between shallow equality and deep equality?

**Answer:**
```js
// Shallow equality — compares references for objects
const a = { x: 1 };
const b = { x: 1 };
const c = a;

a === b; // false — different references
a === c; // true — same reference

// Shallow equality check (what React uses for re-render checks)
function shallowEqual(obj1, obj2) {
  if (obj1 === obj2) return true;
  const keys1 = Object.keys(obj1);
  const keys2 = Object.keys(obj2);
  if (keys1.length !== keys2.length) return false;
  return keys1.every(key => obj1[key] === obj2[key]);
}
shallowEqual({ x: 1, y: 2 }, { x: 1, y: 2 }); // true
shallowEqual({ x: { z: 1 } }, { x: { z: 1 } }); // false! nested ref differs

// Deep equality — recursively compares all nested values
function deepEqual(a, b) {
  if (a === b) return true;
  if (typeof a !== typeof b) return false;
  if (typeof a !== 'object' || a === null) return false;
  const keysA = Object.keys(a);
  const keysB = Object.keys(b);
  if (keysA.length !== keysB.length) return false;
  return keysA.every(key => deepEqual(a[key], b[key]));
}
deepEqual({ x: { z: 1 } }, { x: { z: 1 } }); // true
```

---

### Q176. What is coercion in JavaScript? Show examples of implicit vs explicit.

**Answer:**
Type coercion is the automatic or explicit conversion of values from one type to another.

```js
// ─── IMPLICIT COERCION (automatic) ───

// String + anything = string concatenation
'5' + 3;          // '53' (3 coerced to string)
'5' + true;       // '5true'

// Math operators coerce to number
'5' - 3;          // 2 (string '5' → number 5)
'5' * '3';        // 15
true + 1;         // 2 (true → 1)
false + 1;        // 1 (false → 0)
null + 1;         // 1 (null → 0)
undefined + 1;    // NaN (undefined → NaN)

// Comparison coercion
0 == false;       // true (false → 0)
'' == false;      // true (both → 0)
null == undefined; // true (special rule)
NaN == NaN;       // false (NaN never equals anything)

// Boolean context (truthy/falsy)
// Falsy: false, 0, '', null, undefined, NaN, 0n
// Everything else is truthy
Boolean(0);    // false
Boolean('');   // false
Boolean([]);   // true ← empty array is truthy!
Boolean({});   // true ← empty object is truthy!

// ─── EXPLICIT COERCION ───
Number('42');     // 42
Number('');       // 0
Number(null);     // 0
Number(undefined); // NaN
Number(true);     // 1

String(42);       // '42'
String(null);     // 'null'
String(undefined); // 'undefined'

Boolean(1);       // true
Boolean(0);       // false

parseInt('42px', 10); // 42
parseFloat('3.14em'); // 3.14
```

---

### Q177. What is `NaN`? How do you reliably check for it?

**Answer:**
`NaN` (Not a Number) is a numeric value representing an invalid number.

```js
// NaN is produced by invalid numeric operations
parseInt('abc');      // NaN
0 / 0;                // NaN
Math.sqrt(-1);        // NaN
undefined + 1;        // NaN
Number('abc');        // NaN

// NaN is the ONLY value not equal to itself
NaN === NaN;          // false — bizarre!
NaN == NaN;           // false

// Checking for NaN
isNaN('abc');         // true — ⚠️ coerces to number first! isNaN('abc') → isNaN(NaN) → true
isNaN('123');         // false (coerces to 123)
isNaN(undefined);     // true (undefined → NaN)

Number.isNaN('abc');  // false — ✅ DOES NOT coerce! Only true for actual NaN
Number.isNaN(NaN);    // true  ← most reliable
Number.isNaN(undefined); // false

// typeof NaN is 'number'
typeof NaN;  // 'number' — yes, really

// Pattern to filter NaN from arrays
const arr = [1, NaN, 2, NaN, 3];
arr.filter(n => !Number.isNaN(n)); // [1, 2, 3]
```

---

### Q178. What are JavaScript Bitwise Operators and when are they used?

**Answer:**
```js
// Bitwise operators work on 32-bit integers
5 & 3;   // 1   (AND:  0101 & 0011 = 0001)
5 | 3;   // 7   (OR:   0101 | 0011 = 0111)
5 ^ 3;   // 6   (XOR:  0101 ^ 0011 = 0110)
~5;      // -6  (NOT:  inverts all bits, ~n = -(n+1))
5 << 1;  // 10  (Left shift: multiply by 2)
5 >> 1;  // 2   (Right shift: divide by 2, sign-preserving)
5 >>> 1; // 2   (Unsigned right shift: zero-fill)

// ─── PRACTICAL USES ───

// 1. Fast integer conversion (truncate decimal)
~~3.7;     // 3  (double NOT)
3.7 | 0;   // 3  (OR with 0)
// Faster than Math.floor for positive numbers

// 2. Check if number is odd/even
n & 1;     // 1 = odd, 0 = even
5 & 1;     // 1 → odd
4 & 1;     // 0 → even

// 3. Feature flags / permission bitmasks
const READ    = 0b001; // 1
const WRITE   = 0b010; // 2
const EXECUTE = 0b100; // 4

let permissions = READ | WRITE;  // 3 (has read and write)
permissions & READ;    // 1 (non-zero = has read ✅)
permissions & EXECUTE; // 0 (zero = no execute ❌)

// Grant permission
permissions |= EXECUTE;

// Revoke permission
permissions &= ~WRITE;
```

---

*Good luck with your interviews! 🚀 Consistency > Cramming. Review 10 questions per day.*
