---
title: "Running Your First Node.js Script"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Learn how to run JavaScript code *outside* the browser for the first time, using Node.js!"
isFeatured: false
category: "Nodejs"
---

> **Goal**: Learn how to run JavaScript code *outside* the browser for the first time, using Node.js!

---

## 🚀 Quick Introduction

When you first learned about JavaScript, you probably ran it **inside** a browser — maybe using the **Console** in Chrome or Firefox DevTools.  
**But JavaScript isn't just for browsers anymore!**

Thanks to **Node.js**, you can run JavaScript **directly on your computer**, outside of any browser.  
This is super important because Node.js powers real-world servers, apps, tools, and even AI projects!

---

## 🧠 Key Concept

- **Browsers** (like Chrome) have a JavaScript engine (like **V8**) that understands and runs JS code.
- **Node.js** uses that same engine — **without the browser!**  
- This means you can write and run backend servers, automation scripts, and real applications just with JavaScript.

---

## 🛠️ Let's Get Practical: Your First Node Script

### Step 1: Install Node.js

- Download Node.js from [https://nodejs.org](https://nodejs.org) and install it.
- After installing, check it’s ready by opening your terminal or command prompt and typing:

  ```bash
  node --version
  ```

  You should see something like `v20.11.1` (or newer).

---

### Step 2: Create Your First JavaScript File

- Open any folder.
- Create a new file called:  

  ```plaintext
  hello.js
  ```

- Inside `hello.js`, write this code:

  ```javascript
  console.log('Hello Node!');
  ```

---

### Step 3: Run It with Node.js

In your terminal or command prompt:

1. Navigate to the folder where your `hello.js` file is saved:

   ```bash
   cd path/to/your/folder
   ```

2. Run the script:

   ```bash
   node hello.js
   ```

✅ If everything is correct, you should see:

```bash
Hello Node!
```

printed in your terminal!

---

## 📝 Why This Matters

- You're not limited to browser popups or HTML pages anymore.
- Node.js gives you **superpowers**: you can build web servers, APIs, apps, and powerful tools.
- Learning Node.js is a gateway to becoming a **full-stack developer**!

---

 🎯 Quick Practice Exercise (Mini Exam)

**Task**:

1. Create a file called `greeting.js`.
2. Write a script that prints:

   ```javascript
   Welcome to the world of Node.js!
   ```

   to the terminal.

3. Run the script using Node.js.

***Bonus Challenge***

After your greeting, also print today's date!

Hint:

```javascript
console.log(new Date());
```

***Remember***

Every great developer once started by typing:

```javascript
console.log('Hello World!');
```

You’re on your way! 🚀  

---

Would you also like me to create a **downloadable version (PDF or Markdown)** of this lesson for you to share with your students? 🎓  
Would you want a **second lesson** ready too, like "Reading Input from the Command Line"? 📚

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) ***The: Your journey to mastery, 20th Anniversary Edition***

[Mentorship & Consulting - Contact us for more info](/contact)

***Join Our Discord Community*** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

***For Consulting and Mentorship, feel free to contact*** [slavo.io](/contact)
