---
title: "🚀 Deploy Your First Node.js App to Render (for Free)"
date: "2025-05-04"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Launch your first Node.js project on the web for free with this beginner-friendly Render deployment guide."
isFeatured: false
category: "TypeScript"
---

**👥 Who is this for?**  
New developers · First-time coders · Node.js beginners

**🎯 Goal:**  
Build and deploy a simple “Hello, World” Node.js app on **Render** — without paying a cent.

---

## 🧠 What You’ll Learn

- How to create a basic Node.js app with Express.
- How to push your code to GitHub.
- How to deploy your app to the web using Render's free hosting.

---

## 🛠️ Step-by-Step Instructions

### ✅ 1. Create Your App Locally

In your terminal, run:

```bash
mkdir my-first-node-app
cd my-first-node-app
touch server.js
````

Then open `server.js` and paste this code:

```js
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

> ℹ️ This uses **Express**, a popular Node.js framework for servers.

---

### ✅ 2. Initialize Project & Install Express

Still in the terminal:

```bash
npm init -y
npm install express
```

This will create a `package.json` and install your dependency.

---

### ✅ 3. Configure for Deployment

Open your `package.json` and update the `scripts` section like this:

```json
"scripts": {
  "start": "node server.js"
}
```

Then, create a `.gitignore` file to exclude unnecessary files:

```bash
touch .gitignore
```

Add the following inside:

```nodejs
node_modules
```

---

### ✅ 4. Upload Code to GitHub

Render requires a GitHub repo.

If you haven’t already, install Git and GitHub CLI:

```bash
git init
git add .
git commit -m "Initial commit"
gh repo create my-first-node-app --public --source=. --remote=origin
git push -u origin main
```

> 💡 If you prefer, you can manually create a GitHub repo and push your code the traditional way.

---

### ✅ 5. Deploy on Render

1. Go to [**Render.com**](https://render.com) and sign in or sign up.
2. Click **New → Web Service**.
3. Connect your GitHub if it asks.
4. Select the `my-first-node-app` repo.

In the form, set:

- **Name**: `my-first-node-app`
- **Environment**: Node
- **Build Command**: `npm install`
- **Start Command**: `npm start`

Click **Create Web Service**.

After a short wait... 🚀 your app will be live at:

```txt
https://my-first-node-app.onrender.com
```

Open it and you’ll see:
**“Hello, World from Render!”**

---

## 🖼️ Upload the Blog Post Image (`ts-big-o-notation.png`)

Make sure the image `ts-big-o-notation.png` is saved in the **same directory** as your Markdown blog file (usually `/public/images` or `/assets/images`, depending on your setup).

### Steps

1. Save `ts-big-o-notation.png` in your blog's image folder (same directory as other post images).
2. Double-check that the `image:` path in the frontmatter matches exactly:

   ```yaml
   image: "ts-big-o-notation.png"
   ```

3. Rebuild or restart your static site generator if needed (e.g., Next.js or Astro).

---

## 📝 Practical Task – Add More Routes

Update your `server.js`:

```js
app.get('/', (req, res) => {
  res.send('Welcome to my home page!');
});

app.get('/about', (req, res) => {
  res.send('This is the about page.');
});
```

Then:

```bash
git add .
git commit -m "Add about page"
git push
```

> 🔄 Render will **auto-deploy** from GitHub. Visit:
>
> - `/` → Should show: *Welcome to my home page!*
> - `/about` → Should show: *This is the about page.*

---

## ✅ Final Checklist

- [ ] Can you see your homepage live?
- [ ] Can you access `/about`?
- [ ] Did Render update automatically after your Git push?
- [ ] Is your image file visible in the final blog post?

---

## 📚 Learning Recap

✅ Built a Node.js server with Express
✅ Uploaded it to GitHub
✅ Deployed it online (for free!) using Render
✅ Made live updates to your deployed site

---

## 🎯 Final Thought

Learning by building is the best way forward.
You’ve now put your first Node app **online** for the world to see!

Keep going — you’re building real-world skills.

Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) ***The: Your journey to mastery, 20th Anniversary Edition***

[Mentorship & Consulting - Contact us for more info](/contact)

**Join Our Discord Community** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

***For Consulting and Mentorship, feel free to contact*** [slavo.io](/contact)
