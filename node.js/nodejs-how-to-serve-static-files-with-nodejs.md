---
title: " How to Serve Static Files with Node.js (Without Express!)"
date: "2025-04-28"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Learn how to serve static HTML and images with just pure Node.js and the built-in `fs` (File System) module — no frameworks needed!"
isFeatured: false
category: "Nodejs"
---

## 👋 Hey future engineer

Today, you're going to learn a **core skill** every web developer needs:  
**How to serve a static HTML page and an image using Node.js — with no extra libraries like Express!**

This is the foundation behind almost every web server: serving HTML pages, images, CSS files, and more.

And the best part:  
👉 You only need **pure Node.js** and its built-in modules — no installs, no external dependencies.

Let's build it together step-by-step! 🚀

---

## 🛠 Step 1: Create the Project Files

In a new folder, create these three files **in the same directory**:

| File Name  | Purpose |
|------------|---------|
| `server.js` | Your Node.js server |
| `index.html` | The web page you’ll serve |
| `image.jpg` | An image you’ll display on the page |

✅ **Make sure** the image you upload is saved **in the same folder** as your `server.js` and `index.html`.  
✅ You can use any `.jpg` image — just rename it to `image.jpg`.

> 💡 *Tip:* This way, Node.js will easily find and serve the image without any complicated file paths.

---

## 🛠 Step 2: Set Up the Basic Server

Create a file called `server.js` and add this code:

```javascript
const http = require('http');  // Node.js built-in HTTP module
const fs = require('fs');      // File System module
const path = require('path');  // Path module for easy file management

const server = http.createServer((req, res) => {
  console.log('Request URL:', req.url);

  if (req.url === '/') {
    // Serve HTML page
    fs.readFile(path.join(__dirname, 'index.html'), (err, data) => {
      if (err) {
        res.writeHead(500);
        res.end('Error loading HTML page');
      } else {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(data);
      }
    });
  } else if (req.url === '/image') {
    // Serve the image
    fs.readFile(path.join(__dirname, 'image.jpg'), (err, data) => {
      if (err) {
        res.writeHead(500);
        res.end('Error loading image');
      } else {
        res.writeHead(200, { 'Content-Type': 'image/jpeg' });
        res.end(data);
      }
    });
  } else {
    // Handle unknown routes
    res.writeHead(404, { 'Content-Type': 'text/plain' });
    res.end('404 - Page Not Found');
  }
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000');
});
```

---

## 🛠 Step 3: Create the `index.html`

Create a file called `index.html` in the same folder and paste this code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Welcome to My Node Server!</title>
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This page is served by Node.js!</p>
  <img src="/image" alt="Sample Image" width="300">
</body>
</html>
```

Notice the line:

```html
<img src="/image" alt="Sample Image" width="300">
```

✅ This tells the browser to request the image from the `/image` route you set up in `server.js`.

---

## 🛠 Step 4: Add Your Sample Image

Upload or save any image as `image.jpg` **in the same folder**.  

✅ Make sure the image filename matches exactly: **`image.jpg`**  
✅ Otherwise, Node.js won't find it when you visit `/image`.

---

## 🛠 Step 5: Start Your Server

Now, in your terminal:

```bash
node server.js
```

If everything is correct, you'll see:

```bash
Server running at http://localhost:3000
```

Open your browser and visit:  
👉 [http://localhost:3000](http://localhost:3000)

You should see:

- Your HTML page
- The image you added!

Congratulations 🎉 — you've served static files with pure Node.js!

---

## 🚀 Quick Breakdown: How It Works

| Concept | What It Does |
|---------|--------------|
| `http.createServer()` | Creates a basic HTTP server |
| `fs.readFile()` | Reads a file (HTML or image) from your computer |
| `res.writeHead()` | Sets the response headers (like content type) |
| `res.end()` | Sends the file content to the browser |

---

# 🔥 Practical Challenge (Make it Even Better!)

✅ 1. Create a new folder called `public/` and move `index.html` and `image.jpg` inside it.

✅ 2. Update your `server.js` code to read files from the `public/` folder like this:

```javascript
path.join(__dirname, 'public', 'index.html')
```

✅ 3. Add another image (like `photo.png`) and create a new URL `/photo` that serves it.

✅ 4. (Bonus) Create a custom `404.html` page and serve that for unknown URLs!

---

# 💬 Why This Matters

In the real world:

- **Static files** (HTML, CSS, JS, images) are a huge part of web development.
- **Understanding how HTTP and file serving works** helps you when using bigger frameworks like Express, Next.js, or NestJS.
- **Knowing how things work under the hood** makes you a more confident and valuable developer.

---

# 📚 Final Tip

**Practice small wins daily.**  
Real skills are built step-by-step — by making small working projects like this one.

You're doing amazing. Keep going! 🚀

---

# 📚 Recommended Books

- [React and React Native (Complete Guide, 3rd Edition)](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [The Pragmatic Programmer (20th Anniversary Edition)](https://amzn.to/3W1P4oL)

---

# 🤝 Connect With Us

- [Mentorship & Consulting - Contact Us](/contact)
- [Join Our Discord Community](https://discord.gg/A75tvDvZ) — *Learn, grow, and connect with like-minded developers!*

---

# 🎯 Final Reminder

When uploading your `image.jpg`, **make sure it’s placed in the same directory as `server.js` and `index.html`** (or inside `/public` if you upgrade the project).  
Otherwise, Node.js won't find it and your image won’t load!

---

Would you also like me to create a simple **folder structure diagram** that visually shows where to place `server.js`, `index.html`, and `image.jpg`? 🚀  
It would make this even easier for users to follow! 📂✨
