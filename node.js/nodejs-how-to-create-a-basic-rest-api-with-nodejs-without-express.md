---
title: "How to Create a Basic REST API with Node.js (Without Express)"
date: "2025-05-04"
author: "Slavo"
image: "node-api-guide.png"
excerpt: "Learn to build a lightweight REST API in Node.js from scratch using just the built-in HTTP module. Perfect for beginners!"
isFeatured: false
category: "Nodejs"
---

## 🚀 Goal

By the end of this tutorial, you'll know how to:

* Create a basic REST API using only Node.js (no Express).
* Serve a JSON response using the built-in `http` module.
* Understand and navigate routes with basic condition handling.

---

## 🧠 Prerequisites

Before starting, make sure you have:

* Basic JavaScript knowledge (variables, functions, conditionals).
* [Node.js installed](https://nodejs.org) on your system.
* A code editor like [Visual Studio Code](https://code.visualstudio.com/).

---

## 📸 Important – Upload the Demo Image

Make sure to **upload the image named `node-api-guide.png`** to the **same folder or directory** where your blog post file is stored. This ensures the blog platform can locate and render the image correctly in the post.

The image should visually represent a basic Node.js architecture or server setup. You can create your own or use a royalty-free illustration. Save it with the filename exactly as specified above (`node-api-guide.png`) to match the frontmatter reference.

---

## 📚 What is a REST API?

A **REST API** (Representational State Transfer) is a system that allows different applications to communicate via HTTP requests. APIs expose endpoints (URLs) that clients (like browsers or apps) can call to:

* Get data (`GET`)
* Add data (`POST`)
* Update data (`PUT`)
* Delete data (`DELETE`)

In this guide, we’ll build a single endpoint:

* `GET /api/greeting` → Returns a simple JSON message.

---

## 🛠️ Step-by-Step Guide

### 1. Setup Your Project

Let’s get started by setting up a minimal Node.js environment.

```bash
# Create a new folder and navigate into it
mkdir node-api && cd node-api

# Create your main server file
touch index.js
```

Open the `index.js` file in your code editor.

---

### 2. Add Your Server Code

Copy and paste the following code into `index.js`:

```javascript
// Import the built-in HTTP module
const http = require('http');

// Create an HTTP server
const server = http.createServer((req, res) => {
  res.setHeader('Content-Type', 'application/json');

  // Handle the specific route
  if (req.method === 'GET' && req.url === '/api/greeting') {
    res.statusCode = 200;
    res.end(JSON.stringify({ message: 'Hello, World!' }));
  } else {
    res.statusCode = 404;
    res.end(JSON.stringify({ message: 'Route not found' }));
  }
});

// Define the port
const PORT = 3000;

// Start listening
server.listen(PORT, () => {
  console.log(`Server is running at http://localhost:${PORT}`);
});
```

---

### 3. Code Breakdown

| Line                  | Explanation                                       |
| --------------------- | ------------------------------------------------- |
| `require('http')`     | Loads the Node.js module to create a server.      |
| `http.createServer()` | Instantiates a new server.                        |
| `req.method`          | Detects the HTTP method (GET, POST, etc).         |
| `req.url`             | Reads the requested path (e.g., `/api/greeting`). |
| `res.setHeader()`     | Sets response headers (we're returning JSON).     |
| `res.statusCode`      | Sends the HTTP status code (e.g., 200, 404).      |
| `res.end()`           | Sends the final response.                         |

---

### 4. Run Your Server

Use your terminal:

```bash
node index.js
```

You should see:

```javascript
Server is running at http://localhost:3000
```

---

### 5. Test Your Endpoint

#### ✅ Valid Route

Open your browser or Postman and go to:

```javascript
http://localhost:3000/api/greeting
```

You should get:

```json
{ "message": "Hello, World!" }
```

#### ❌ Invalid Route

Try:

```javascript
http://localhost:3000/api/unknown
```

You'll see:

```json
{ "message": "Route not found" }
```

---

## 🔁 Recap

Here’s what you’ve achieved:

* Built a functioning API without Express.
* Used the `http` module directly.
* Served JSON responses.
* Handled routing with `if` conditions.

---

## 🚧 Next Steps

* Add more routes: `/api/time`, `/api/users`, etc.
* Explore other HTTP methods like `POST`, `PUT`, and `DELETE`.
* Connect to a database (like MongoDB or SQLite).
* Later, try switching to Express to simplify routing and middleware.

Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
