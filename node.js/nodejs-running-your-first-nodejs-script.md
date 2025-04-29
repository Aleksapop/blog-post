---
title: "Learn how to run JavaScript code *outside* the browser for the first time, using Node.js!"
date: "2025-04-29"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Learn how to run JavaScript code *outside* the browser for the first time using Node.js!"
isFeatured: false
category: "Nodejs"
---


## 🚀 Quick Introduction

When you first learned JavaScript, you probably used it **inside** a browser — maybe in the Chrome DevTools Console.

But JavaScript isn’t just for browsers anymore.

Thanks to **Node.js**, you can run JavaScript code **directly on your computer**, no browser required.  
This is a game-changer — Node.js powers real-world web servers, command-line tools, and even AI scripts.

---

## 🧠 Key Concept

- Browsers (like Chrome) run JavaScript using a built-in engine called **V8**.
- **Node.js** also uses V8 — but **without the browser**.
- That means you can write scripts and backends in plain JavaScript on your own machine.

---

## 🛠️ Hands-On: Running Your First Node Script

Follow these steps to run your first script.

---

### ✅ Step 1: Install Node.js

1. Go to [https://nodejs.org](https://nodejs.org) and download the latest **LTS version** for your system.
2. Install it with the default settings.
3. Open a **terminal** or **command prompt** and run:

   ```bash
   node --version
   ```

   If installed correctly, it will print something like:

   ```javascript
   v20.11.1
   ```

---

### 📝 Step 2: Create Your JavaScript File

1. Choose or create a folder on your desktop, for example:  
   `my-node-test`

2. Inside that folder, create a new file called:

   ```javascript
   hello.js
   ```

3. Open it in any text editor (e.g., VS Code, Notepad++) and paste:

   ```javascript
   console.log('Hello Node!');
   ```

---

### 💻 Step 3: Run the Script Using Node.js

1. Open your terminal and navigate to the folder you just created:

   ```bash
   cd path/to/my-node-test
   ```

   (Use drag-and-drop if you're unsure of the path.)

2. Run your script:

   ```bash
   node hello.js
   ```

3. ✅ If everything works, you’ll see:

   ```javascript
   Hello Node!
   ```

---

### 📸 Image Upload for Redori Users

If you're using **Redori** to create or publish this lesson, and you need to add the image `"ts-big-o-notation.png"`:

1. Save the image file in the **same folder/directory** as your Markdown file.
2. Ensure this frontmatter line exists at the top of your post:

   ```yaml
   image: "ts-big-o-notation.png"
   ```

3. The image will now appear as the blog header/preview depending on your theme.  
   ✅ Keep image names lowercase and with dashes for consistency and SEO.

---

## 🌟 Why This Matters

Now that you're running JavaScript outside the browser:

- You can create powerful tools, servers, and APIs.
- You’re building real-world backend logic with **zero browser dependencies**.
- You’re officially on the **full-stack path**!

---

## 🎯 Practice Exercise

Try this on your own!

**Task**:

1. Create a file called `greeting.js`.
2. Write this:

   ```javascript
   console.log("Welcome to the world of Node.js!");
   ```

3. Then run it just like before:

   ```bash
   node greeting.js
   ```

**Bonus Challenge**:

Also print today’s date:

```javascript
console.log(new Date());
```

---

## 💡 Final Thoughts

Remember: every great developer once typed:

```javascript
console.log('Hello World!');
```

You’ve just taken your first step toward mastering JavaScript *beyond the browser*.

Keep going — backend, full-stack, APIs, tools — it's all waiting for you. 🚀

---

## 📚 Want to Go Deeper?

Would you like this lesson as a **PDF or Markdown download** for your team or classroom?

Should I prepare a **second lesson** like “Reading Input from the Command Line in Node.js”? Let me know!

---

## 📘 Book Recommendations

- [React and React Native (3rd Edition)](https://amzn.to/3CStF7m) — Web & mobile in one go!
- [React Key Concepts](https://amzn.to/43XOCJM) — Fast-track React knowledge.
- [The Pragmatic Programmer (20th Anniversary)](https://amzn.to/3W1P4oL) — Timeless advice for all coders.

---

## 🙌 Join the Community

Join our **Discord** to share progress, ask questions, and connect with other devs:  
👉 [Click to join](https://discord.gg/A75tvDvZ)

Need help or mentorship?  
🔗 [Contact us here](/contact)

Happy coding!  
– Slavo

---
