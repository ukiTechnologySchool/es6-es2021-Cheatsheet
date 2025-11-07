# JavaScript ES6+ & Modern (up to ES2021) Features — Teacher Cheatsheet (Examples & Use Cases)

This cheatsheet lists **modern JavaScript features** from ES6 up through **ES2021** that are most relevant to your six groups.  
For each feature: **short explanation → concise example → practical use case**.

---

## Group 1 — Numbers & Strings (ES6 → ES2021)

### 1. Template Literals (ES6)
**What:** Interpolate values and create multi-line strings.
```js
const name = "Niroobana";
const price = 99.99;
console.log(`Hello ${name}, your total is Rs.${price.toFixed(2)}`);
```
**Use case:** Cleanly build receipt lines, emails, or UI strings.

### 2. String Methods: startsWith, endsWith, includes (ES6)
**What:** Test substrings more readably.
```js
"hello".startsWith("he"); // true
"version-1.2.3".includes("1.2"); // true
```
**Use case:** Form validation, search filters.

### 3. String padding: padStart, padEnd (ES2017)
**What:** Pad strings for alignment.
```js
console.log("5".padStart(3, "0")); // "005"
```
**Use case:** Formatting invoice numbers, aligning table columns.

### 4. trimStart / trimEnd (ES2019)
**What:** Trim whitespace from one side.
```js
"  user ".trimStart(); // "user "
```
**Use case:** Clean user input while preserving intentional trailing spaces in some contexts.

### 5. Intl.NumberFormat (ECMAScript Internationalization API — widely available)
**What:** Localized number/currency formatting.
```js
const fmt = new Intl.NumberFormat('en-LK', { style: 'currency', currency: 'LKR' });
console.log(fmt.format(12345.67)); // "LKR 12,345.67" (locale dependent)
```
**Use case:** Display currency amounts correctly for users in different locales.

---

## Group 2 — Math, Loops & Iteration (ES6 → ES2021)

### 1. Arrow Functions (ES6)
**What:** Concise function expressions; lexical `this`.
```js
const sq = n => n * n;
[1,2,3].map(n => n * 2);
```
**Use case:** Short callbacks in loops, array transformations.

### 2. for...of (ES6)
**What:** Iterate iterable values (arrays, strings) directly.
```js
for (const item of ["a","b"]) console.log(item);
```
**Use case:** Cleaner iteration over arrays than index-based `for`.

### 3. Array.from + Array.of (ES6)
**What:** Create arrays from iterable/array-like structures.
```js
const chars = Array.from("hello"); // ['h','e','l','l','o']
```
**Use case:** Convert NodeList, arguments, or strings into arrays for processing.

### 4. Math.trunc, Math.sign (ES6 additions / later)
**What:** Helpful numeric utilities.
```js
Math.trunc(4.9); // 4
Math.sign(-5); // -1
```
**Use case:** Numeric normalization in analytics or sensor data.

### 5. BigInt (ES2020) — also relevant in Group 4
**What:** Integers beyond `Number.MAX_SAFE_INTEGER`.
```js
const big = 123456789012345678901n;
```
**Use case:** Transaction IDs, crypto counters.

---

## Group 3 — Operators & Conditions (ES6 → ES2021)

### 1. Destructuring (ES6)
**What:** Extract values from arrays/objects succinctly.
```js
const user = {name: 'A', age: 20};
const { name, age } = user;
const [first, second] = [10, 20];
```
**Use case:** Cleaner access to request payloads or DB rows.

### 2. Default Parameters & Rest (ES6)
**What:** Provide defaults and capture remaining args.
```js
function greet(name = "Guest", ...flags) { console.log(name, flags); }
```
**Use case:** Flexible function APIs for utilities or services.

### 3. Spread Operator (ES6)
**What:** Expand arrays/objects; shallow copy/merge.
```js
const a = [1,2];
const b = [...a, 3];
const newObj = { ...user, active: true };
```
**Use case:** Immutable updates to state (React), merging payloads.

### 4. Optional Chaining (ES2020)
**What:** Safely access nested properties.
```js
console.log(user.profile?.address?.city);
```
**Use case:** Handling unpredictable API responses.

### 5. Nullish Coalescing (ES2020)
**What:** Use `??` to provide default only for `null`/`undefined`.
```js
const val = 0 ?? 10; // 0 (unlike ||)
const name = user.name ?? "Anonymous";
```
**Use case:** Provide meaningful defaults without overriding valid falsy values like `0` or `""`.

---

## Group 4 — Date, Null, Undefined, BigInt, Symbol (ES6 → ES2021)

### 1. Intl.DateTimeFormat (Widely available)
**What:** Localized date/time formatting.
```js
const fmt = new Intl.DateTimeFormat('en-GB', { dateStyle: 'medium', timeStyle: 'short'});
console.log(fmt.format(new Date()));
```
**Use case:** Display readable timestamps in user locale.

### 2. Temporal (Note: proposal; not in ES2021) — OMITTED (per request)

### 3. BigInt (ES2020)
**What:** Safe integer arithmetic for very large integers.
```js
const id = 987654321012345678901n;
console.log(id + 1n);
```
**Use case:** Blockchain counters, large transaction IDs.

### 4. Symbol (ES6)
**What:** Create unique keys; hidden object properties.
```js
const S = Symbol('session');
const obj = { [S]: 'secret' };
```
**Use case:** Private-ish properties in libraries, avoiding key collisions.

### 5. Nullish handling patterns (ES2020)
**What:** Combine `??` and optional chaining to handle missing data safely.
```js
const city = user?.profile?.city ?? "No Data";
```
**Use case:** Safely display fallback values in UIs and logs.

---

## Group 5 — Objects (ES6 → ES2021)

### 1. Object Destructuring (ES6)
**What:** Extract properties easily.
```js
const { name, salary } = employee;
```
**Use case:** Pull relevant fields from API responses.

### 2. Computed Property Names (ES6)
**What:** Dynamic keys in object literals.
```js
const k = 'id';
const obj = { [k]: 101 };
```
**Use case:** Build objects using form field names.

### 3. Object Spread (ES2018)
**What:** Clone/merge objects.
```js
const merged = { ...obj1, ...obj2 };
```
**Use case:** Immutable updates to state/config.

### 4. Object.fromEntries (ES2019)
**What:** Convert key-value pairs to objects.
```js
const entries = [['a',1],['b',2]];
const obj = Object.fromEntries(entries); // {a:1, b:2}
```
**Use case:** Convert query params or form data into objects.

### 5. Optional Chaining & Nullish Coalescing (ES2020)
**What:** Safe property access with defaults.
```js
const phone = user.contact?.phone ?? "No phone";
```
**Use case:** Robust UI rendering for partial data.

---

## Group 6 — Arrays (ES6 → ES2021)

### 1. Spread & Rest (ES6)
**What:** Combine/copy arrays, gather function args.
```js
const arr = [1,2,3];
const copy = [...arr];
function sum(...nums) { return nums.reduce((a,b) => a+b, 0); }
```
**Use case:** Immutable list updates, flexible utilities.

### 2. Array.find, findIndex (ES6)
**What:** Locate items by predicate.
```js
const users = [{id:1},{id:2}];
users.find(u => u.id === 2);
```
**Use case:** Retrieve model by id in lists.

### 3. map, filter, reduce (ES5/ES6 usage patterns)
**What:** Functional transformations over arrays.
```js
const doubled = [1,2,3].map(n => n*2);
const evens = [1,2,3,4].filter(n => n%2===0);
const sum = [1,2,3].reduce((s,n) => s+n, 0);
```
**Use case:** Data pipelines for analytics and UI data prep.

### 4. flat & flatMap (ES2019)
**What:** Flatten nested arrays.
```js
[1,[2,3],[4]].flat(); // [1,2,3,4]
[1,2,3].flatMap(n => [n, n*2]); // [1,2,2,4,3,6]
```
**Use case:** Normalize API responses with nested lists.

### 5. at() (ES2022 — include as recent but after ES2021 note)
**Note:** `at()` is ES2022; mention briefly as upcoming/modern convenience.
```js
const a = [10,20,30];
a.at(-1); // 30
```
**Use case:** Cleaner negative indexing for last item.

---

## Quick Examples — Combined Patterns

### Safe access + default
```js
const city = user?.address?.city ?? "Unknown";
```

### Merge arrays & remove duplicates
```js
const a = [1,2,3], b = [3,4];
const mergedUnique = [...new Set([...a, ...b])]; // [1,2,3,4]
```

### Convert form entries to object
```js
const entries = [['username','niroo'], ['age','22']];
const obj = Object.fromEntries(entries);
```

---

## Recommended Talking Points for Class
- Emphasize **immutability**: prefer spread over mutation in most UI apps.  
- Show **readability** improvements with destructuring and optional chaining.  
- Use `Intl` APIs for localization (numbers, dates).  
- BigInt is for special cases — most web apps still use Numbers; show when BigInt is necessary.

---

## Endnotes
This cheatsheet restricts features up to **ES2021**, with a few brief mentions of later conveniences (noted). Use these snippets during presentations to **deepen**, **correct**, and **extend** student points.

