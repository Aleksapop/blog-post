---
title: "Making External API Requests in Node.js"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

**Lesson Overview**  
In this lesson, we’ll learn how to make external API requests in Node.js using two popular libraries: `node-fetch` and `axios`. You'll understand how to fetch data from a public API and handle the responses.

**What You’ll Learn:**  

1. Setting up a Node.js project.
2. Installing the necessary packages (`node-fetch` and `axios`).
3. Making GET requests to fetch data from an external API.
4. Handling and displaying the API response.

---

#### 1. **Setting up a Node.js Project**

Before we start making API requests, we need to set up a basic Node.js project.

1. **Initialize a new Node.js project**  
   Open a terminal and create a new folder for your project:

   ```bash
   mkdir node-api-requests
   cd node-api-requests
   npm init -y
   ```

2. **Install dependencies**  
   Now, install `node-fetch` or `axios` (you can use either of these libraries). For this lesson, we'll demonstrate both.

   ```bash
   npm install node-fetch axios
   ```

---

#### 2. **Making API Requests with `node-fetch`**

Now, let’s make a request using the `node-fetch` package. It is a lightweight library that allows us to use the `fetch` function in Node.js.

1. **Create a new file named `fetchExample.js`**  
   In your project folder, create a file called `fetchExample.js`.

2. **Write the code to fetch data from a public API**

Here’s how you can fetch data from a public API using `node-fetch`:

```javascript
// fetchExample.js
const fetch = require('node-fetch');

const url = 'https://jsonplaceholder.typicode.com/posts/1';  // A public API endpoint

// Fetch data from the API
fetch(url)
  .then(response => response.json())  // Parse the JSON response
  .then(data => {
    console.log('Fetched Data:', data);  // Log the data
  })
  .catch(error => {
    console.error('Error fetching data:', error);  // Handle errors
  });
```

3.**Run the code**

```bash
node fetchExample.js
```

You should see a response similar to this in your terminal:

```json
Fetched Data: {
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit...exercitationem praesentium\nquasi...etc"
}
```

---

#### 3. **Making API Requests with `axios`**

Next, let’s see how you can use `axios` to make the same request.

1. **Create a new file named `axiosExample.js`**  
   In your project folder, create another file called `axiosExample.js`.

2. **Write the code to fetch data from a public API using `axios`**

```javascript
// axiosExample.js
const axios = require('axios');

const url = 'https://jsonplaceholder.typicode.com/posts/1';  // A public API endpoint

// Make a GET request using axios
axios.get(url)
  .then(response => {
    console.log('Fetched Data:', response.data);  // Log the data
  })
  .catch(error => {
    console.error('Error fetching data:', error);  // Handle errors
  });
```

3.**Run the code**

```bash
node axiosExample.js
```

You should see the same response as with `node-fetch`.

---

#### 4. **Key Differences Between `node-fetch` and `axios`**

- **`node-fetch`**: A minimal library that is great for making simple HTTP requests. It uses the native `fetch` API, which is available in the browser, but requires polyfilling in Node.js.
- **`axios`**: A more feature-rich HTTP client that provides more functionality out-of-the-box (e.g., automatic JSON parsing, request and response interceptors, etc.). It is a bit larger than `node-fetch`.

---

#### 5. **Exercise: Fetch Data from Another API**

Now, let’s practice fetching data from another public API. You can use [https://api.coindesk.com/v1/bpi/currentprice/BTC.json](https://api.coindesk.com/v1/bpi/currentprice/BTC.json) for live Bitcoin price data.

- Use either `node-fetch` or `axios` to fetch the current Bitcoin price.
- Display the price in the console.

---

#### **Summary**

- **`node-fetch`** and **`axios`** are both useful libraries for making HTTP requests in Node.js.
- **`axios`** is a bit more feature-rich, while **`node-fetch`** is simpler and closer to the browser’s native fetch functionality.
- Understanding how to handle responses and errors is crucial in API requests.

Great job! You’ve just learned how to make external API requests in Node.js.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
