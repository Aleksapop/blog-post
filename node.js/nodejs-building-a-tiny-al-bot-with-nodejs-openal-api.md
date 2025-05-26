---
title: "Building a Tiny AI Bot with Node.js + OpenAI API"
date: "2025-05-05"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Today, we’ll build something magical together — a Tiny AI Bot 🤖 using Node.js and the OpenAI API."
isFeatured: false
category: "Type Script"
---

### 👋 Welcome, New Coders

Today, we’ll build something **magical** together — a **Tiny AI Bot** 🤖 using **Node.js** and the **OpenAI API**.
Even if you're just starting, don’t worry — this guide is **step-by-step and beginner-friendly**.

> 💡 **By the end**, you’ll have your own AI bot that talks back!

---

## 🖼️ Image Upload (For Readers Using This Lesson as a Guide)

> ✅ Please make sure the image file `ts-big-o-notation.png` is uploaded into the **same directory** as your project files (`tiny-ai-bot/`).
> You can drag and drop it into the folder, or use this terminal command:

```bash
mv /path/to/ts-big-o-notation.png ./tiny-ai-bot/
```

This image is used in the blog metadata and helps with SEO/social previews. It won't be used in your code — just make sure it's in the folder.

---

## ✨ Step 1: Set Up Your Project

1. Install [Node.js](https://nodejs.org/) if you haven’t already.
2. Open your terminal and run:

```bash
mkdir tiny-ai-bot
cd tiny-ai-bot
npm init -y
```

🛠️ You’ve just created a fresh Node.js project!

---

## 📦 Step 2: Install the OpenAI Package

Install the official OpenAI Node.js client:

```bash
npm install openai
```

This gives your project access to powerful AI capabilities.

---

## 🔑 Step 3: Get Your OpenAI API Key

1. Go to [OpenAI’s platform](https://platform.openai.com/)
2. Sign in or sign up.
3. Navigate to **API Keys** and copy your key (starts with `sk-...`)

> ⚠️ Keep your API key **private**. Do not share it publicly!

---

## 🧠 Step 4: Write Your AI Bot

1. Create a new file:

```bash
touch index.js
```

2.Open it in your favorite editor (like VS Code), and add this code:

```javascript
// 1. Import OpenAI
const { OpenAI } = require('openai');

// 2. Initialize OpenAI
const openai = new OpenAI({
  apiKey: 'YOUR_API_KEY_HERE', // Replace this with your actual API key
});

// 3. Send a prompt to the AI
async function askAI() {
  const response = await openai.chat.completions.create({
    messages: [{ role: 'user', content: 'Tell me a fun fact about space!' }],
    model: 'gpt-3.5-turbo',
  });

  console.log('🤖 AI says:', response.choices[0].message.content);
}

// 4. Run the function
askAI();
```

---

## 🚀 Step 5: Run Your Bot

In your terminal, run:

```bash
node index.js
```

🎉 You should see a fun AI-generated answer in your terminal!

---

## 🧪 Mini Practical Exercise

Try customizing your bot!

1. Change the question to:

```javascript
{ role: 'user', content: 'Give me a motivational quote!' }
```

2.Add a second call to `askAI()` or modify the function to ask:

```javascript
{ role: 'user', content: 'What is Node.js in one sentence?' }
```

> ✨ Experiment freely! You can even loop through multiple prompts if you want to get fancy.

---

## 💥 Bonus Challenge

Try these upgrades:

* Ask **any question** you want!
* Change the model from `gpt-3.5-turbo` to `gpt-4` (if your API key allows).
* Format the output with emojis, bold text, or markdown:

```javascript
console.log('🌟 Answer:', response.choices[0].message.content);
```

---

## 🔁 Recap

Today you learned how to:

* Create a Node.js project 🛠️
* Install and use the `openai` package 📦
* Use the API to get real-time answers from AI 🤖
* Build, run, and experiment with your own chatbot!

---

## 📘 Keep Going! Microlearning Ideas

* Make your bot **talk back** in real-time like a conversation loop
* Build a **web server with Express** that sends back AI answers
* Add a **user interface** with HTML/CSS or React!

Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
