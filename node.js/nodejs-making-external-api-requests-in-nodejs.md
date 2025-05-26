---
title: "Making External API Requests in Node.js"
date: "2025-05-03"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

## 🧠 Lesson Overview

In this hands-on micro-lesson, you'll learn how to:

* Set up a basic Node.js project
* Install required libraries (`node-fetch` and `axios`)
* Fetch data from external APIs using both libraries
* Understand and compare the differences between them

---

## ✅ Step 1: Setting Up a Node.js Project

1. **Create a New Project Directory**
   Open your terminal and run the following commands:

   ```bash
   mkdir node-api-requests
   cd node-api-requests
   npm init -y
   ```

2. **Install Dependencies**

   ```bash
   npm install node-fetch axios
   ```

   > We're installing both libraries so you can try out both examples.

---

## 🌐 Step 2: Making API Requests Using `node-fetch`

### 1. **Create a File**

In your project directory, create a new file named:

```bash
touch fetchExample.js
```

### 2. **Write the Fetch Code**

```javascript
// fetchExample.js
const fetch = require('node-fetch');

const url = 'https://jsonplaceholder.typicode.com/posts/1';

fetch(url)
  .then(response => response.json())
  .then(data => {
    console.log('Fetched Data:', data);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

### 3. **Run the File**

```bash
node fetchExample.js
```

You should see something like this in your terminal:

```json
Fetched Data: {
  "userId": 1,
  "id": 1,
  "title": "...",
  "body": "..."
}
```

---

## ⚡ Step 3: Making API Requests Using `axios`

### 1. **Create Another File**

```bash
touch axiosExample.js
```

### 2. **Write the Axios Code**

```javascript
// axiosExample.js
const axios = require('axios');

const url = 'https://jsonplaceholder.typicode.com/posts/1';

axios.get(url)
  .then(response => {
    console.log('Fetched Data:', response.data);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

_**3. Run the File**_

```bash
node axiosExample.js
```

You’ll see the same output as the previous example.

---

## 🔍 Step 4: Key Differences Between `node-fetch` and `axios`

| Feature      | `node-fetch`                   | `axios`                              |
| ------------ | ------------------------------ | ------------------------------------ |
| Size         | Lightweight                    | Larger, feature-rich                 |
| JSON Parsing | Manual (`.json()` required)    | Automatic                            |
| Interceptors | Not included                   | Built-in support                     |
| Browser-Like | Closely mimics browser `fetch` | Works differently from browser fetch |

---

## 💡 Practice Task: Get Live Bitcoin Price

**Try this on your own!**
Use either `node-fetch` or `axios` to fetch the current Bitcoin price from the Coindesk API:

**API Endpoint:**
[https://api.coindesk.com/v1/bpi/currentprice/BTC.json](https://api.coindesk.com/v1/bpi/currentprice/BTC.json)

### Example Output to Display

```bash
Current BTC Price (USD): $62,345.78
```

---

## 📝 Summary

* You’ve learned how to use both `node-fetch` and `axios` to make external API requests in Node.js.
* Both libraries serve the same purpose but offer different developer experiences.
* Practicing with public APIs is a great way to improve your Node.js skills.

---

## 📚 Recommended Reading

* 📘 [React and React Native: 3rd Edition](https://amzn.to/3CStF7m)
* 📗 [React Key Concepts](https://amzn.to/43XOCJM)
* 📙 [The Pragmatic Programmer: 20th Anniversary Edition](https://amzn.to/3W1P4oL)

---

## 💬 Join Our Community

* 💡 **Have Questions? Need Guidance?**
  [Contact us here for mentorship and consulting](/contact)

* 🔗 **Join Our Discord Community**
  [Click here to connect, learn, and grow with fellow developers](https://discord.gg/A75tvDvZ)
  
Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
