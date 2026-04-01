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
- [ ] JS Advanced: Promises, async/await, event loop, generators, proxy
- [ ] React: Hooks, lifecycle, context, patterns, optimization
- [ ] Performance: Core Web Vitals, code splitting, lazy loading
- [ ] Debugging: DevTools, common React bugs, CSS issues
- [ ] Coding: Implement common utilities from scratch
- [ ] System Design: Folder structure, component architecture

---

*Good luck with your interviews! 🚀 Consistency > Cramming. Review 10 questions per day.*
