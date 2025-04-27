---
title: "How to Serve Static Files with Node.js"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

### Hey future engineer! 👋  

Today, we’re learning something **foundational**:  
**How to serve a static HTML file or an image using Node.js**.

This is the kind of thing every web server in the world does — whether it's serving a homepage, a product image, or a video.

Good news:  
👉 **You don’t need any frameworks** like Express for this basic skill — just **pure Node.js** + a built-in module called `fs` (File System).

Let’s dive in.

---

## 🛠 Step-by-Step: Serve Static Files with Node.js

### 1. Set up a basic server

First, create a file called `server.js`:

```javascript
const http = require('http');  // built-in Node.js HTTP module
const fs = require('fs');      // built-in File System module
const path = require('path');  // helps handle file paths

const server = http.createServer((req, res) => {
  console.log('Request URL:', req.url);

  // Handle root URL
  if (req.url === '/') {
    // Read and serve the HTML file
    fs.readFile(path.join(__dirname, 'index.html'), (err, data) => {
      if (err) {
        res.writeHead(500);
        res.end('Error loading the file');
      } else {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(data);
      }
    });
  }
  // Handle an image
  else if (req.url === '/image') {
    fs.readFile(path.join(__dirname, 'image.jpg'), (err, data) => {
      if (err) {
        res.writeHead(500);
        res.end('Error loading the image');
      } else {
        res.writeHead(200, { 'Content-Type': 'image/jpeg' });
        res.end(data);
      }
    });
  }
  else {
    res.writeHead(404);
    res.end('Page not found');
  }
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000');
});
```

---

### 2. Create a basic `index.html`

In the same folder, make a file called `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Welcome to My Server!</title>
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This HTML page is served by Node.js!</p>
  <img src="/image" alt="Sample Image" width="300">
</body>
</html>
```

---

### 3. Add a sample image

Save any image as `image.jpg` in the same folder as your `server.js` and `index.html`.

---

### 4. Run the server

In your terminal:

```bash
node server.js
```

Now open your browser and go to:  
👉 [http://localhost:3000](http://localhost:3000)

You’ll see your HTML page, and the image too! 🖼️

---

## 🚀 Quick Breakdown: How It Works

- `http.createServer()` — creates a server that listens for requests.
- `fs.readFile()` — reads a file from your computer’s disk.
- `res.writeHead()` — sets the HTTP status and headers (like telling the browser “hey, this is HTML” or “this is an image”).
- `res.end()` — sends the file content back to the browser.

You just built a *very basic static file server*!

---

***Practical Exercise***

Now it’s your turn:

✅ 1. Create a new folder called `public/` and move `index.html` and `image.jpg` inside it.

✅ 2. Update the server code to read from the `public/` folder.

*Hint:* You’ll need to change the `path.join` line like:

```javascript
path.join(__dirname, 'public', 'index.html')
```

✅ 3. Add a second image (like `photo.png`) and make a new URL `/photo` to serve it!

✅ 4. (Bonus) Handle 404 errors nicely — create a `404.html` page and serve it when the page isn’t found.

---

***Why This Matters***

In real-world coding:

- You'll often need to serve files (HTML, CSS, JS, images).
- Understanding **how Node.js handles files and HTTP** helps you massively when you use frameworks like Express later.
- And it gives you the confidence that you know **what's going on under the hood**.

---

***Final Tip***

Keep practicing these *small wins* every day.  
Building with your own hands is the fastest way to learn real coding skills.

***Proud of you for taking the time to learn this!***

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) ***The: Your journey to mastery, 20th Anniversary Edition***

[Mentorship & Consulting - Contact us for more info](/contact)

***Join Our Discord Community*** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

***For Consulting and Mentorship, feel free to contact*** [slavo.io](/contact)
