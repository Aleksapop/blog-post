---
title: "Introduction to Promises in Node.js"
date: "2025-05-03"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "In Node.js, a **Promise** is a special object that represents the result of an asynchronous operation."
isFeatured: false
category: "Type Script"
---

## Topic: Convert a Callback into a Promise (Manually)

---

## 🧠 What You’ll Learn

* What is a **Promise** in Node.js?
* Why do we sometimes **convert callbacks** into Promises?
* How to **manually wrap** a callback inside a Promise.

---

## 🚀 Quick Introduction: What is a Promise?

In Node.js, a **Promise** is a special object that represents the result of an asynchronous operation.

✅ A Promise can be in one of **three states**:

* **Pending** → The operation is still in progress.
* **Resolved** → The operation has completed successfully.
* **Rejected** → Something went wrong.

Instead of using **callbacks**—which can become messy, also known as "callback hell"—we use Promises to write **cleaner**, **more readable** code.

---

## 📜 Classic Callback Example

Many Node.js functions still use **callbacks**, like this:

```javascript
function getData(callback) {
  setTimeout(() => {
    callback(null, "Here is your data!");
  }, 1000);
}

getData((err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

> ⚡ **Problem:** Callback code can get **messy** and **nested** quickly.

---

## 🔥 Let's Convert This Callback into a Promise

We can **manually** wrap the callback inside a **Promise** like this:

```javascript
function getDataPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true; // Change this to false to test rejection
      if (success) {
        resolve("Here is your data!");
      } else {
        reject("Something went wrong!");
      }
    }, 1000);
  });
}

// Now, we can use .then() and .catch()
getDataPromise()
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.error(error);
  });
```

✅ Now the function returns a **Promise** instead of using a callback!

---

## 🎯 Step-by-Step Breakdown

1. **Create a new Promise object:**
   `new Promise((resolve, reject) => { ... })`

2. **Inside the Promise:**

   * Call `resolve(result)` if the operation succeeds.
   * Call `reject(error)` if an error occurs.

3. Use `.then()` to handle **successful resolution**.

4. Use `.catch()` to handle **rejections/errors**.

---

## 🛠️ Practical Exercise

> **Task:**
> Convert this callback-based function into a Promise version!

### Original (Callback Version)

```javascript
function readFileFake(callback) {
  setTimeout(() => {
    const error = null;
    const content = "File content: Hello World!";
    callback(error, content);
  }, 1500);
}

readFileFake((err, content) => {
  if (err) {
    console.error("Error reading file:", err);
  } else {
    console.log(content);
  }
});
```

### ✨ Your Challenge

* Create a function called `readFileFakePromise`.
* It should return a **Promise**.
* Use `.then()` and `.catch()` to log the result.

🔵 **Hint:** Wrap `setTimeout` inside a new Promise, just like the example we studied.

---

## 📚 Summary

* Promises help us write **cleaner**, **more manageable** async code compared to callbacks.
* You can **manually wrap** any callback-based function into a Promise.
* Use `.then()` for success handling, and `.catch()` for error handling.

Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
