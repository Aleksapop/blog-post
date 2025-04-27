---
title: "Using Async/Await to Make Async Code Clean in JavaScript"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

### Why This Matters

When you work with APIs, databases, or files in JavaScript, you deal with **asynchronous operations** — things that **take time** to complete.  
At first, you might use **Promises** with `.then()` and `.catch()`.  
But as your code grows, **Promise chains** become **messy** and **hard to read**.

Good news:  
JavaScript gave us a **better way** → `async/await`.  
It makes async code **look** and **feel** like **normal step-by-step code**.  
Cleaner. Easier to debug. More professional.

---

### 🛠 Quick Before/After Example

🔴 **Without async/await (promise chain):**

```javascript
function getUserData() {
  fetch('https://api.example.com/user')
    .then(response => response.json())
    .then(data => {
      console.log('User data:', data);
    })
    .catch(error => {
      console.error('Error fetching user data:', error);
    });
}
```

✅ **Refactored with async/await:**

```javascript
async function getUserData() {
  try {
    const response = await fetch('https://api.example.com/user');
    const data = await response.json();
    console.log('User data:', data);
  } catch (error) {
    console.error('Error fetching user data:', error);
  }
}
```

**Notice:**  

- No more `.then()` chains!  
- `await` *pauses* the function until the Promise is done.
- `try/catch` handles errors in a clean block.

---

***How Async/Await Works (in plain English)***

- `async` keyword: Marks a function that uses `await`.
- `await`: Waits for a Promise to resolve (or reject) before moving to the next line.
- `try/catch`: Catches any errors inside async functions.

---

***Practical Lesson***

Let's **refactor** a real Promise-based function into `async/await`.

**Starter code (messy Promise version):**

```javascript
function getPost() {
  fetch('https://jsonplaceholder.typicode.com/posts/1')
    .then(response => response.json())
    .then(post => {
      console.log('Post title:', post.title);
    })
    .catch(error => {
      console.error('Error fetching post:', error);
    });
}

getPost();
```

---

## ✏️ Your Mission

**Refactor this function using `async/await`.**  
(Write it yourself first — then check the solution below.)

---

## ✅ Solution

```javascript
async function getPost() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
    const post = await response.json();
    console.log('Post title:', post.title);
  } catch (error) {
    console.error('Error fetching post:', error);
  }
}

getPost();
```

---

***Quick Mini-Exam (5-min Practice)***

**Question:**  
Here’s a function that still uses Promises.  
Rewrite it using `async/await`!

```javascript
function getUsers() {
  fetch('https://jsonplaceholder.typicode.com/users')
    .then(response => response.json())
    .then(users => {
      console.log('Number of users:', users.length);
    })
    .catch(error => {
      console.error('Error fetching users:', error);
    });
}

getUsers();
```

**Your Goal:**

- Make it clean with `async/await`.
- Handle errors properly.

✏️ Write it out now before checking your answer!

---

***Key Takeaways***

- **Async/await** makes code look like **simple synchronous code**.
- **Always** use `try/catch` to handle errors in async functions.
- Your code will be **cleaner**, **easier to read**, and **easier to debug**.

👉 **Professional tip:**  
At real tech companies, clean async code **matters a lot**.  
Learn async/await early — and you'll *level up* faster than most beginners.

---

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) ***The: Your journey to mastery, 20th Anniversary Edition***

[Mentorship & Consulting - Contact us for more info](/contact)

***Join Our Discord Community*** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

***For Consulting and Mentorship, feel free to contact*** [slavo.io](/contact)
