````md
# MOTADATA — TRAINEE PRODUCT ENGINEER
## 2–3 Hour Crash Revision
### Topics 1–3: JavaScript → React → REST APIs

---

## ⏱️ PLAN

| Topic | Time |
|---|---:|
| JavaScript | 50 min |
| React | 45 min |
| REST/API | 45 min |
| Quick Revision | 20 min |

> **RULE:**  
> Don't memorize definitions.  
> Understand **WHAT it does + WHY we use it + small example.**

---

# 1️⃣ JAVASCRIPT FUNDAMENTALS

## Variables

- `let` → value can change
- `const` → value cannot be reassigned
- `var` → old way; avoid in modern JS

### Example

```js
let age = 19;
age = 20;

const name = "Kavy";
// name = "Raj"; ❌
````

---

## Data Types

| Type      | Example                     |
| --------- | --------------------------- |
| String    | `"hello"`                   |
| Number    | `10`, `3.14`                |
| Boolean   | `true / false`              |
| Array     | `[1, 2, 3]`                 |
| Object    | `{ name: "Kavy", age: 19 }` |
| null      | intentionally empty         |
| undefined | value not assigned          |

---

## `==` vs `===`

* `==` → compares value (does type conversion)
* `===` → compares value AND type

```js
5 == "5"     // true
5 === "5"    // false
```

> **Prefer `===`.**

---

## Functions

### Normal

```js
function add(a, b) {
    return a + b;
}
```

### Arrow

```js
const add = (a, b) => {
    return a + b;
};
```

### Short

```js
const add = (a, b) => a + b;
```

---

## Arrays

```js
const nums = [1, 2, 3, 4, 5];
```

### `map()`

→ changes every element

```js
nums.map(n => n * 2);
// [2,4,6,8,10]
```

### `filter()`

→ keeps elements that satisfy condition

```js
nums.filter(n => n > 3);
// [4,5]
```

### `find()`

→ returns first matching element

```js
nums.find(n => n > 3);
// 4
```

### `forEach()`

→ performs something for every element

```js
nums.forEach(n => console.log(n));
```

### `reduce()`

→ combines array into one value

```js
nums.reduce((sum, n) => sum + n, 0);
// 15
```

### IMPORTANT

| Method    | Meaning        |
| --------- | -------------- |
| `map`     | transform      |
| `filter`  | select         |
| `find`    | find one       |
| `forEach` | perform action |
| `reduce`  | combine        |

---

## Objects

```js
const user = {
    name: "Kavy",
    age: 19
};

user.name
user.age
```

### Destructuring

```js
const { name, age } = user;
```

---

## Spread Operator

```js
const a = [1, 2];
const b = [...a, 3, 4];

// [1,2,3,4]
```

> Useful for copying/updating arrays and objects.

---

## Conditional

```js
if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

### Ternary

```js
const result = age >= 18 ? "Adult" : "Minor";
```

---

# ⭐ ASYNC JAVASCRIPT

JavaScript often has to wait for things like:

* API response
* Database
* File
* Timer

Instead of stopping everything, JS handles it asynchronously.

---

## Promise

A Promise represents a future result.

### States

* `pending` → waiting
* `fulfilled` → successful
* `rejected` → failed

---

## `async / await`

Instead of:

```js
fetch(url)
    .then(...)
    .catch(...)
```

We commonly write:

```js
async function getUsers() {
    try {
        const response = await fetch("/api/users");
        const data = await response.json();

        console.log(data);
    } catch (error) {
        console.log(error);
    }
}
```

### Remember

* `async` → function can use `await`
* `await` → wait for Promise result
* `try/catch` → handle errors

---

## API Flow

```text
React/JS
   ↓
fetch()
   ↓
Backend API
   ↓
Response
   ↓
JSON
   ↓
UI
```

---

# 🧪 JS INTERVIEW QUESTIONS

1. Difference between `let`, `const` and `var`?
2. Difference between `==` and `===`?
3. Difference between `map()` and `filter()`?
4. What is a Promise?
5. Why do we use `async/await`?
6. What happens if an API request fails?
7. What is the difference between `null` and `undefined`?

> **If you can answer these WITHOUT looking → move on.**

---

# 2️⃣ REACT

## What is React?

React is a JavaScript library used to build interactive user interfaces using reusable components.

Think:

```text
Website
   ↓
Components
   ↓
Navbar
Dashboard
Button
Card
Form
```

---

## Component

A component is a reusable piece of UI.

```jsx
function Welcome() {
    return <h1>Hello</h1>;
}
```

Use:

```jsx
<Welcome />
```

---

## JSX

JSX lets us write HTML-like syntax inside JavaScript.

```jsx
const element = <h1>Hello</h1>;
```

> It is NOT exactly HTML.
> It gets converted into JavaScript.

---

## Props

Props = data passed **FROM parent TO child**.

```jsx
function User({ name }) {
    return <h2>{name}</h2>;
}

<User name="Kavy" />
```

Think:

```text
Parent
  ↓ props
Child
```

> Props should generally be treated as read-only.

---

# ⭐⭐⭐ State

State = data that can change during component usage.

```jsx
import { useState } from "react";

const [count, setCount] = useState(0);
```

* `count` → current value
* `setCount()` → changes value

### Example

```jsx
function Counter() {

    const [count, setCount] = useState(0);

    return (
        <button onClick={() => setCount(count + 1)}>
            {count}
        </button>
    );
}
```

### IMPORTANT

> **Props → received from parent**
> **State → managed inside component**

---

# ⭐⭐⭐ `useEffect`

Used for side effects.

Common example:

> Fetching API data.

```jsx
useEffect(() => {
    fetchUsers();
}, []);
```

`[]` means:

> Run when component initially loads.

### Example

```jsx
useEffect(() => {
    console.log("Component loaded");
}, []);
```

If dependency changes:

```jsx
useEffect(() => {
    console.log("User changed");
}, [user]);
```

> Basic understanding is enough.

---

# React API Call

Typical structure:

```jsx
function Users() {

    const [users, setUsers] = useState([]);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {

        fetch("/api/users")
            .then(res => res.json())
            .then(data => {
                setUsers(data);
                setLoading(false);
            })
            .catch(err => {
                setError(err);
                setLoading(false);
            });

    }, []);

}
```

### Real application should handle

```text
Loading
   ↓
Success
   ↓
Display data

OR

Loading
   ↓
Error
   ↓
Display error
```

---

# Conditional Rendering

```jsx
{loading && <p>Loading...</p>}

{error && <p>Something went wrong</p>}

{users.map(user => (
    <div key={user.id}>
        {user.name}
    </div>
))}
```

---

## Why `key`?

React uses keys to identify list items efficiently.

Use a unique value:

```jsx
key={user.id}
```

> Avoid using random values.

---

# Forms

Common React form flow:

```text
Input
 ↓
onChange
 ↓
State
 ↓
Submit
 ↓
API
```

### Example

```jsx
const [email, setEmail] = useState("");

<input
    value={email}
    onChange={e => setEmail(e.target.value)}
/>
```

---

# 🧪 React Interview Questions

1. What is React?
2. What is a component?
3. What is JSX?
4. Props vs State?
5. What does `useState` do?
6. What does `useEffect` do?
7. How do you call an API in React?
8. Why do we need loading and error states?
9. Why does React need keys when rendering lists?
10. How would you submit a form to a backend?

---

# 3️⃣ REST API + BACKEND INTEGRATION

## What is an API?

API = a way for two software systems to communicate.

Example:

```text
React Frontend
      ↓
    API
      ↓
Node/Python Backend
      ↓
   Database
```

> Frontend doesn't normally directly manipulate the database.

> Backend handles the business logic.

---

# HTTP METHODS

| Method   | Purpose                        |
| -------- | ------------------------------ |
| `GET`    | get data                       |
| `POST`   | create data                    |
| `PUT`    | replace/update entire resource |
| `PATCH`  | partially update resource      |
| `DELETE` | delete data                    |

### Example

```http
GET    /users
POST   /users
GET    /users/10
PATCH  /users/10
DELETE /users/10
```

---

# ⭐⭐⭐ HTTP STATUS CODES

| Code  | Meaning               |
| ----- | --------------------- |
| `200` | Success               |
| `201` | Created               |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `403` | Forbidden             |
| `404` | Not Found             |
| `500` | Internal Server Error |

### Easy Memory

```text
2xx → Success
4xx → Client/request problem
5xx → Server problem
```

---

# Request vs Response

## REQUEST

```http
POST /users
```

```json
{
    "name": "Kavy",
    "email": "kavy@example.com"
}
```

## RESPONSE

```text
201 Created
```

```json
{
    "id": 101,
    "name": "Kavy",
    "email": "kavy@example.com"
}
```

---

# JSON

JSON is the common format used to exchange data between frontend and backend.

```json
{
    "name": "Kavy",
    "age": 19
}
```

JSON uses:

```text
"key": value
```

---

# REST

REST is an architectural style for building APIs.

### Good REST API

```http
GET    /products
POST   /products
GET    /products/10
PATCH  /products/10
DELETE /products/10
```

> Think resources, not actions.

Better:

```http
GET /users/10
```

Not:

```http
GET /getUserById/10
```

---

# Authentication vs Authorization

## Authentication

→ Who are you?

Example:

> Login with email/password.

## Authorization

→ What are you allowed to do?

Example:

```text
Admin → delete users
User  → view profile
```

### Remember

```text
AUTHENTICATION = identity

AUTHORIZATION = permission
```

---

# ⭐⭐⭐ API Debugging

If:

```text
Frontend → API → ERROR
```

Don't randomly change code.

Follow this:

1. Check browser Console
2. Open Network tab
3. Check request URL
4. Check HTTP method
5. Check request body
6. Check headers
7. Check status code
8. Test API in Postman
9. Check backend logs
10. Check database if needed

---

## Example

React says:

```text
"Failed to fetch"
```

### Possible reasons

* wrong URL
* backend not running
* CORS
* wrong port
* network issue
* server error

### If Postman works but browser doesn't:

Check:

→ URL
→ CORS
→ headers
→ frontend request

---

# Postman

Postman is used to test APIs independently of the frontend.

### Example

```http
POST
http://localhost:5000/users
```

Body → JSON

```json
{
    "name": "Kavy"
}
```

### Why useful?

If Postman works:

→ Backend probably works
→ Problem may be frontend.

If Postman fails:

→ Investigate backend/API.

---

# ⭐ FULL APPLICATION FLOW

```text
User clicks:
"Create Account"
        ↓
React form
        ↓
POST API
        ↓
Backend
        ↓
Validate data
        ↓
Business logic
        ↓
Database
        ↓
Database response
        ↓
Backend response
        ↓
React
        ↓
Show success/error
```

> **THIS FLOW IS VERY IMPORTANT FOR THE INTERVIEW.**

---

# 🔥 QUICK COMPARISONS

## Props vs State

| Props              | State                    |
| ------------------ | ------------------------ |
| passed from parent | managed inside component |
| read-only          | can change               |
| communication      | causes UI update         |

---

## GET vs POST

**GET**

* retrieve
* usually no request body

**POST**

* create/send data
* request body commonly used

---

## PUT vs PATCH

**PUT**

* full replacement/update

**PATCH**

* partial update

---

## Authentication vs Authorization

**Authentication**
→ Who are you?

**Authorization**
→ What can you access?

---

## `map` vs `filter`

**map**
→ transforms

**filter**
→ selects

---

# 🎯 20-MINUTE FINAL REVISION

Be able to explain these **WITHOUT NOTES**:

* [ ] `let` vs `const` vs `var`
* [ ] `==` vs `===`
* [ ] `map/filter/reduce`
* [ ] Promise
* [ ] async/await
* [ ] React component
* [ ] JSX
* [ ] Props
* [ ] State
* [ ] useState
* [ ] useEffect
* [ ] React API call
* [ ] Loading/error state
* [ ] REST API
* [ ] GET/POST/PUT/PATCH/DELETE
* [ ] HTTP status codes
* [ ] JSON
* [ ] Authentication vs Authorization
* [ ] Postman
* [ ] API debugging
* [ ] Frontend → Backend → Database flow

---

# 🚨 MOST LIKELY PRACTICAL QUESTIONS

## Q1. Your React page isn't showing API data.

### How will you debug it?

**Answer structure:**

```text
Console
→ Network
→ URL
→ Request
→ Status code
→ Postman
→ Backend logs
→ Database
```

---

## Q2. Design a simple user registration system.

**Answer:**

```text
React form
→ POST API
→ Backend validation
→ Database
→ Response
→ React success/error
```

---

## Q3. API returns 401. What does it mean?

`401 = authentication problem.`

Check:

→ login/token
→ Authorization header
→ token expiry

---

## Q4. API returns 404.

Usually:

→ wrong URL
→ endpoint doesn't exist
→ wrong route

---

## Q5. API returns 500.

Server-side error.

Check:

→ backend logs
→ code
→ database
→ external service

---

## Q6. Explain your project.

Use:

```text
Problem
→ Why you built it
→ Tech stack
→ Architecture
→ YOUR contribution
→ Biggest problem
→ How you solved it
→ Improvement
```

---

# ⭐ INTERVIEW GOLDEN RULE

Don't say:

> "I don't know."

If you genuinely don't know:

> "I haven't worked with that directly yet, but I would approach it by..."

Then explain your reasoning.

For a Product Engineer, **HOW YOU THINK** matters as much as what you already know.

---

# AFTER THESE 3 TOPICS

Next priority:

4. Git + Postman + Swagger
5. Product Thinking
6. Debugging / RCA
7. AI + LLM basics
8. Observability
9. Your projects
10. Assignment simulation
11. Interview simulation

> **DO NOT START ADVANCED DSA BEFORE THESE.**

```
```
