---
title: "Deploy Your First Node.js App to Render (for Free)"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Type Script"
---

**Audience**:  
New engineers | First-time coders | Node.js beginners

**Goal**:  
Deploy a simple "Hello, World" Node.js app to **Render** — without paying a cent.

---

## 🧠 Quick Learning

- **Node.js** lets you run JavaScript on servers.
- **Render.com** is a cloud platform where you can host apps easily (and they have a great free plan!).

Today, you'll **code** a simple app **and deploy it online** so anyone can see it.

---

## 🛠️ Step-by-Step Guide

### 1. Create a Simple Node.js App

**First**, on your computer, create a new folder:

```bash
mkdir my-first-node-app
cd my-first-node-app
```

**Then**, create a file named `server.js`:

```bash
touch server.js
```

Open `server.js` and add this code:

```javascript
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.send('Hello, World from Render!');
});

app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});
```

> 🧠 **Note**: We use `express` to easily create a web server.  

### 2. Initialize Your Project and Install Express

In the terminal:

```bash
npm init -y
npm install express
```

This will create a `package.json` and install Express.

---

### 3. Prepare for Deployment

Modify your `package.json` so Render knows how to start your app.  

In `package.json`, add:

```json
"scripts": {
  "start": "node server.js"
}
```

Also, **create a file named** `package-lock.json` (this happens automatically when you install express) and **.gitignore** (to ignore node_modules).

Create `.gitignore` and add:

```terminal
node_modules
```

---

### 4. Upload Your App to GitHub

You need to push your app to GitHub because Render pulls from GitHub!

If you don't have Git installed, install it first.

**Then in your terminal:**

```bash
git init
git add .
git commit -m "first commit"
gh repo create my-first-node-app --public --source=. --remote=origin
git push -u origin main
```

> ✨ This uses GitHub CLI (`gh`) — if you don't have it, you can also create a new repo manually on GitHub and push.

---

### 5. Deploy to Render

- Go to [https://render.com](https://render.com) and sign up (or log in).
- Click **"New"** → **"Web Service"**.
- Connect your GitHub account if you haven't.
- Select your **repo** (`my-first-node-app`).
- Fill in:
  - **Name**: my-first-node-app
  - **Environment**: Node
  - **Build Command**: `npm install`
  - **Start Command**: `npm start`
- Click **Create Web Service**.

Wait a few minutes... 🚀

Boom! Your app is now live! 🎉

You'll get a live URL like:

```javascript
https://my-first-node-app.onrender.com
```

Visit it and see: **"Hello, World from Render!"**  

---

## 📚 Quick Summary

✅ You wrote a simple Node.js app.  
✅ You learned about Express.js.  
✅ You pushed your code to GitHub.  
✅ You deployed to Render for free.

**You just put your first app on the internet!**

---

## 📝 Practical Exam

👉 **Task**:  
Modify your app so it has **two routes**:

- `/` → Should return "Welcome to my home page!"
- `/about` → Should return "This is the about page."

Deploy the updated app again on Render (update the same project or redeploy).

> ⚡ Tip: You can edit `server.js`, commit the changes, push to GitHub — Render auto-updates!

---

### 🧪 Test Yourself

- [ ] Can you access `/` and see the welcome message?
- [ ] Can you access `/about` and see the about page?
- [ ] Did you use GitHub correctly?
- [ ] Did you update your app live?

---

## 🎯 Final Thought

Learning by doing is the fastest way to grow.  
You just built and deployed your first real Node.js app — and that’s HUGE.  
Small steps today → Big engineer tomorrow.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
