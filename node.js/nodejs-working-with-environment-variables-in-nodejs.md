---
title: "Working with Environment Variables in Node.js"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

### **Introduction:**

As a new software engineer, understanding how to manage sensitive information in your code is essential. One of the best ways to handle this is by using environment variables. They allow you to store configuration values securely, like database credentials, API keys, and application settings. In this micro-learning lesson, we'll teach you how to create a `.env` file and read its values using `process.env` in Node.js.

### **What are Environment Variables?**

Environment variables are key-value pairs used to configure your application for different environments (development, production, etc.). They can help keep sensitive data out of your codebase and can be easily accessed by your application.

For example, you might have an API key for a third-party service, and instead of hardcoding it in your application, you can store it as an environment variable. This way, you can keep your credentials safe, and your code will be easier to manage across different environments.

---

### **Step-by-Step Lesson:**

#### **1. Install dotenv Package**

First, we'll use the `dotenv` package to load environment variables from a `.env` file into our Node.js application. To install it, run the following command in your project directory:

```bash
npm install dotenv
```

#### **2. Create the .env File**

Now, let's create a `.env` file in the root of your project. This file will hold your environment variables.

Create a `.env` file and add a few key-value pairs like this:

```env
# .env file
API_KEY=your_api_key_here
DB_HOST=localhost
DB_PORT=5432
```

Make sure to add the `.env` file to your `.gitignore` file to prevent it from being committed to version control. This keeps your sensitive data secure.

#### **3. Loading Environment Variables**

In your `app.js` (or any entry point file of your application), you’ll need to load the variables from the `.env` file. At the very top of your file, add the following line:

```javascript
require('dotenv').config();
```

This line tells your Node.js application to load all the variables from the `.env` file into `process.env`.

#### **4. Accessing Environment Variables**

Now, you can access your environment variables using `process.env`. Here's an example:

```javascript
console.log("API Key:", process.env.API_KEY);
console.log("Database Host:", process.env.DB_HOST);
console.log("Database Port:", process.env.DB_PORT);
```

If you run the app, you should see the values from your `.env` file printed to the console.

```bash
$ node app.js
API Key: your_api_key_here
Database Host: localhost
Database Port: 5432
```

#### **5. Practical Example: Database Connection**

Imagine you're building an app that connects to a PostgreSQL database. Instead of hardcoding the connection details in your code, you can store them in the `.env` file. Here's how you might do it:

```env
# .env file
DB_HOST=localhost
DB_PORT=5432
DB_USER=myuser
DB_PASS=mypassword
```

Then, in your Node.js app:

```javascript
const { Client } = require('pg');

// Load environment variables
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

Now, you can connect to your database securely without exposing sensitive information in your code.

---

### **Conclusion:**

In this lesson, you learned how to manage sensitive data using environment variables in Node.js. We covered how to create a `.env` file, load it with `dotenv`, and access the variables using `process.env`. This is a powerful tool for building secure and maintainable applications.

### **Key Takeaways:**

- Environment variables store configuration data securely.
- The `.env` file holds the key-value pairs.
- Use the `dotenv` package to load the `.env` file.
- Access environment variables using `process.env`.

---

### **Your Practice Task:**

- Create a `.env` file in your Node.js project with at least 3 variables (e.g., API key, database host, port).
- Modify your app to use those environment variables for configuration.
- Test your app by printing out the environment variables to the console.

---

By practicing with environment variables, you'll be on your way to writing more secure, flexible, and maintainable code!

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
