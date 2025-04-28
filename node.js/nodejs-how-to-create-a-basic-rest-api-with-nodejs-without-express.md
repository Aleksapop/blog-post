---
title: "How to Create a Basic REST API with Node.js (Without Express)"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---



#### Goal: 
By the end of this lesson, you will understand how to create a basic REST API using only Node.js, utilizing the built-in `http` module to serve a simple JSON response.


### Prerequisites

- Basic knowledge of JavaScript.
- A text editor (like VS Code) and Node.js installed on your computer.

---

### Introduction

In this lesson, we’re going to create a simple REST API using Node.js **without** the need for any external libraries like Express. You’ll use Node.js's built-in `http` module to handle HTTP requests and send JSON responses.

#### What is REST API?

A REST (Representational State Transfer) API allows communication between different systems over HTTP. It's a way to expose some functionality (like fetching data) via URLs. We will be implementing a simple API with the following routes:

- `GET /api/greeting`: Returns a "Hello, World!" message in JSON format.

---

### Step-by-Step Guide

#### 1. **Setup your project:**

First, let's initialize a basic Node.js project.

1. Create a folder for your project, e.g., `node-api`.
2. Inside the folder, create a new file named `index.js`.
3. Open `index.js` in your text editor.

#### 2. **Write the code:**

Now, let’s set up a basic server using the `http` module.

```javascript
// Import the http module to create the server
const http = require('http');

// Define the server
const server = http.createServer((req, res) => {
  // Set the response header for JSON
  res.setHeader('Content-Type', 'application/json');

  // Check for the requested route
  if (req.method === 'GET' && req.url === '/api/greeting') {
    // Return a JSON response for the greeting route
    res.statusCode = 200;  // Status code for successful request
    res.end(JSON.stringify({ message: 'Hello, World!' }));
  } else {
    // For all other routes, return a 404 Not Found
    res.statusCode = 404;
    res.end(JSON.stringify({ message: 'Route not found' }));
  }
});

// Define the port where the server will listen
const PORT = 3000;

// Start the server
server.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```

#### 3. **Explanation of the Code:**

- **`http.createServer`**: This method creates a server that listens for requests. It takes a callback function with two parameters: `req` (request) and `res` (response).
- **`res.setHeader`**: Sets the content type of the response to `application/json`.
- **`req.method` and `req.url`**: These properties allow us to check the HTTP request method (GET, POST, etc.) and the URL being requested.
- **`res.statusCode`**: Sets the HTTP status code of the response (200 for success, 404 for not found).
- **`res.end()`**: Ends the response and sends data back to the client.

#### 4. **Run the Server:**

In your terminal, navigate to the folder where you saved `index.js`, and run the server:

```bash
node index.js
```

Your server should now be running on `http://localhost:3000`.

#### 5. **Test the API:**

1. Open your browser and go to `http://localhost:3000/api/greeting`. You should see:

   ```json
   { "message": "Hello, World!" }
   ```

2. If you try accessing a route that doesn't exist (e.g., `http://localhost:3000/api/unknown`), you will get a response like:

   ```json
   { "message": "Route not found" }
   ```

---

### Recap

- We created a simple REST API using the built-in `http` module in Node.js.
- We learned how to handle different HTTP methods (`GET` in this case).
- We returned JSON data as a response to the client.
- We also checked the status code to communicate success or failure.

### Next Steps

- Now that you’ve built a basic REST API, you can try adding more routes, like `POST`, `PUT`, or `DELETE`.
- You can also try integrating a database like MongoDB to serve dynamic data.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
