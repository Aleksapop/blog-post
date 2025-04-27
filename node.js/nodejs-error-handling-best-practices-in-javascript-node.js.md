---
title: "Error Handling Best Practices in JavaScript & Node.js"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---



## Why Error Handling Matters 🛡️

When you're writing code, *things can go wrong*. Files might not exist. APIs might fail. Bugs might happen.

Good engineers expect mistakes — and **handle errors** carefully so the app doesn't crash or behave badly.  

Learning **error handling** early will make you a **much stronger developer**.

---

## Key Concepts You Need To Know 🔑

- **Synchronous Code**: Code that runs line by line, instantly.
- **Asynchronous Code**: Code that waits (e.g., API calls, reading files) — usually with Promises or async/await.

Each type needs a slightly different way to handle errors.

---

## 🔥 How to Handle Errors

### 1. Handling **Synchronous Errors** with `try-catch`

Use `try-catch` blocks when your code runs immediately and could throw errors.

```javascript
function riskySyncFunction() {
  throw new Error("Something went wrong!");
}

try {
  riskySyncFunction();
  console.log("This won't run if there's an error.");
} catch (error) {
  console.error("Caught a sync error:", error.message);
}
```

✅ Inside `try {}`, you put the code that *might* break.  
✅ Inside `catch (error) {}`, you react safely when it *does* break.

---

### 2. Handling **Asynchronous Errors** (Promises)

Async functions and Promises need `.catch()` or `try-catch` with `async/await`.

#### Using `.catch()` on Promises

```javascript
function riskyAsyncFunction() {
  return Promise.reject(new Error("Async failure!"));
}

riskyAsyncFunction()
  .then(() => {
    console.log("Success!");
  })
  .catch((error) => {
    console.error("Caught an async error with .catch:", error.message);
  });
```

✅ Always add `.catch()` to your Promises, so you don't miss errors!

---

#### Using `try-catch` with `async/await`

```javascript
async function handleAsync() {
  try {
    await riskyAsyncFunction();
    console.log("Success!");
  } catch (error) {
    console.error("Caught an async error with try-catch:", error.message);
  }
}

handleAsync();
```

✅ If you use `await`, wrap it in a `try-catch` to catch errors.

---

## 🚀 Practical Example Challenge

**Fix the code below so it properly catches both sync and async errors:**

```javascript
function mayThrowSync() {
  throw new Error("Sync boom!");
}

async function mayThrowAsync() {
  throw new Error("Async boom!");
}

function main() {
  mayThrowSync();
  mayThrowAsync();
}

main();
```

> 🧠 Hint: You need both `try-catch` and `async/await`.

---

### 🛠 Solution

```javascript
function mayThrowSync() {
  throw new Error("Sync boom!");
}

async function mayThrowAsync() {
  throw new Error("Async boom!");
}

async function main() {
  try {
    mayThrowSync();
  } catch (error) {
    console.error("Caught sync error:", error.message);
  }

  try {
    await mayThrowAsync();
  } catch (error) {
    console.error("Caught async error:", error.message);
  }
}

main();
```

---

## 🧠 Key Takeaways

- Use `try-catch` for synchronous code.
- Use `.catch()` for Promises or `try-catch` with `async/await`.
- Always expect things to go wrong — and handle it cleanly!

> **Good error handling = Reliable software + Happy users + Less stress!**

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) ***The: Your journey to mastery, 20th Anniversary Edition***

[Mentorship & Consulting - Contact us for more info](/contact)

***Join Our Discord Community*** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

***For Consulting and Mentorship, feel free to contact*** [slavo.io](/contact)
