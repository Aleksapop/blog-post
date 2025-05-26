---
title: "Working with Environment Variables in Node.js"
date: "2025-05-03"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Managing sensitive information (like API keys and database credentials) directly in your code can be risky."
isFeatured: false
category: "Nodejs"
---

## 🚀 Introduction

Managing sensitive information (like API keys and database credentials) directly in your code can be risky. That's where **environment variables** come in! They help you keep this data secure and easily configurable for different environments (development, production, staging, etc.).

In this micro-learning guide, we’ll walk step-by-step through using environment variables in a Node.js app, using the popular `dotenv` package.

---

## 📷 **Before You Start – Image Upload Instructions**

This post includes an image named `ts-big-o-notation.png`.

👉 **To use it properly:**

1. Make sure the image file is named exactly: `ts-big-o-notation.png`.
2. Place the image inside the **same directory** where your markdown blog post file is stored (e.g., `/posts/`).
3. If you're using a static site generator like Next.js or Gatsby, make sure the image is correctly referenced and accessible.

---

## 🔐 What Are Environment Variables?

Environment variables are like secret notes that your application can read without having them written directly in the code.

For example:

```env
API_KEY=your_api_key_here
```

You can access that key in your app without hardcoding it.

---

## 🧑‍💻 Step-by-Step Guide

### ✅ 1. Install `dotenv` Package

We'll use the `dotenv` package to read `.env` files.

Open your terminal and run:

```bash
npm install dotenv
```

---

### 📝 2. Create a `.env` File

In the **root of your project**, create a file named `.env`.

Inside it, add some key-value pairs:

```env
API_KEY=your_api_key_here
DB_HOST=localhost
DB_PORT=5432
```

> ⚠️ **Important:** Add `.env` to your `.gitignore` file to avoid uploading sensitive info to version control.

---

### 📥 3. Load `.env` Variables in Your App

In your `app.js` (or entry file), add this line **at the top**:

```javascript
require('dotenv').config();
```

This will load everything from `.env` into `process.env`.

---

### 👀 4. Access the Variables in Code

Now, use `process.env` to read the values:

```javascript
console.log("API Key:", process.env.API_KEY);
console.log("Database Host:", process.env.DB_HOST);
console.log("Database Port:", process.env.DB_PORT);
```

Run it:

```bash
node app.js
```

Expected output:

```javascript
API Key: your_api_key_here  
Database Host: localhost  
Database Port: 5432
```

---

### 🧩 5. Practical Use: Database Connection Example

Let's say you're connecting to a PostgreSQL database. Store your credentials like this:

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=myuser
DB_PASS=mypassword
```

Then in your app:

```javascript
const { Client } = require('pg');
require('dotenv').config();

const client = new Client({
  host: process.env.DB_HOST,
  port: process.env.DB_PORT,
  user: process.env.DB_USER,
  password: process.env.DB_PASS,
  database: 'mydatabase'
});

client.connect()
  .then(() => console.log("Connected to the database"))
  .catch((err) => console.error("Connection error", err.stack));
```

---

## 🎯 Conclusion

You now know how to:

* Create a `.env` file
* Load it using `dotenv`
* Access variables with `process.env`

Environment variables are essential for writing **secure** and **configurable** Node.js apps.

---

## 🧠 Key Takeaways

* Use `.env` to separate sensitive config from code.
* Use `dotenv` to load `.env` into your Node.js app.
* Always **exclude** `.env` from version control.

---

## 🧪 Practice Task

Try it yourself:

1. Create a `.env` file in your project.
2. Add at least 3 variables: `API_KEY`, `DB_HOST`, `DB_PORT`.
3. Use `process.env` to log them in your app.
4. Bonus: Try building a database connection like the example above.

---

## 📚 Book Recommendations

* [React and React Native (3rd Edition)](https://amzn.to/3CStF7m)
* [React Key Concepts](https://amzn.to/43XOCJM)
* [The Pragmatic Programmer (20th Anniversary Edition)](https://amzn.to/3W1P4oL)

---

## 🤝 Join the Community

**💬 Need help or want to grow with others?**
Join our [Discord Community](https://discord.gg/A75tvDvZ) – A space to collaborate, learn, and grow.

**📩 For Mentorship & Consulting**
[Contact us at slavo.io](/contact)
