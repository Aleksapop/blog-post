---
title: "Error Handling Best Practices in JavaScript & Node.js"
date: "2025-05-04"
author: "Slavo"
image: "ts-error-handling-guide.png"  # Make sure this image is in the same folder as this post file
excerpt: "Learn how to handle errors like a pro in both synchronous and asynchronous JavaScript with easy-to-follow examples."
isFeatured: false
category: "Nodejs"
---

> 📷 **Upload Guide**:  
> Please upload the image `ts-error-handling-guide.png` to the **same directory** where this post is stored (e.g., `/blog/error-handling-best-practices/`).  
> This image should visually represent a flowchart or diagram of sync vs async error handling to enhance the learning experience.

---

## Why Error Handling Matters 🛡️

When you're writing code, **things can go wrong**:

- Files might not exist.
- APIs might fail.
- Bugs might pop up unexpectedly.

That's why great developers **expect errors** — and know how to **handle them gracefully**.

> 💡 **Mastering error handling** means your code is more reliable, user-friendly, and easier to debug.

---

## 🔑 Key Concepts To Understand First

Before we dive into examples, let's define two important types of code execution:

- **Synchronous Code**: Executes step-by-step (line by line).
- **Asynchronous Code**: Waits for something (like API responses or file reading). This often uses **Promises** or `async/await`.

---

## 🔥 How to Handle Errors Like a Pro

### ✅ 1. Handling **Synchronous Errors** with `try-catch`

Use `try-catch` when the code runs immediately and could throw an error:

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
````

> ✅ Use `try {}` for code that *might* fail
> ✅ Use `catch {}` to respond safely when it *does* fail

---

### ✅ 2. Handling **Asynchronous Errors** in Two Ways

#### Method A: Using `.catch()` with Promises

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

> ✅ Always chain `.catch()` when using Promises
> ❌ Skipping `.catch()` can crash your app!

---

#### Method B: Using `async/await` with `try-catch`

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

> ✅ If you're using `await`, always use a `try-catch` block around it

---

## 🧪 Challenge: Spot and Fix the Errors

Can you fix the following code so it handles both **sync** and **async** errors?

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

> 💡 Hint: `main()` should be made `async` and include proper `try-catch` blocks.

---

### ✅ Solution

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

## 🧠 Final Takeaways

- Use `try-catch` for synchronous code.
- Use `.catch()` for Promises or `try-catch` with `async/await`.
- **Never assume things will work** — write code that’s ready when they don’t.

> 🧘 Clean error handling = fewer bugs, better user experience, and way less debugging stress.

---

## 📚 Bonus Book Recommendations

- [React and React Native (3rd Edition)](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [The Pragmatic Programmer: 20th Anniversary Edition](https://amzn.to/3W1P4oL)

---

## 👨‍🏫 Need Help?

[**Mentorship & Consulting — Contact Us Here**](/contact)

---

## 💬 Join Our Developer Community

[Click to Join Our Discord](https://discord.gg/A75tvDvZ) — Unleash your potential and connect with devs worldwide!

Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) ***The: Your journey to mastery, 20th Anniversary Edition***

[Mentorship & Consulting - Contact us for more info](/contact)

***Join Our Discord Community*** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

***For Consulting and Mentorship, feel free to contact*** [slavo.io](/contact)
