---
title: "Building a Tiny AI Bot with Node.js + OpenAI API"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

### 👋 Welcome, New Coders

Today, we're going to build something **magical**:  
A **Tiny AI Bot** that talks to OpenAI's API and gives you smart answers! 🤖

No worries — **we’ll take it slow**, step by step.  
By the end, you'll have a real Node.js app talking to AI!  
**Let’s GO 🚀**

---

## ✨ Step 1: Set Up Your Project

First, you need Node.js installed.  
(If you don't have it yet, download it here: [https://nodejs.org/](https://nodejs.org/)).

Now, open your terminal and type:

```bash
mkdir tiny-ai-bot
cd tiny-ai-bot
npm init -y
```

This will create a new Node.js project!

---

## 📦 Step 2: Install the OpenAI NPM Package

Now install the official OpenAI client:

```bash
npm install openai
```

✅ Done! You now have the power of AI at your fingertips.

---

## 🔑 Step 3: Get Your OpenAI API Key

1. Go to [https://platform.openai.com/](https://platform.openai.com/)
2. Sign up (if you haven't yet).
3. Find your **API Key** and **copy it**.  
   (It looks like: `sk-XXXXXXXXXXXXXXXXXX`).

We'll need this soon!

---

## 🧠 Step 4: Create Your First AI Bot Code

Create a file called:

```bash
touch index.js
```

Open `index.js` in your favorite code editor (like VS Code).

Now write this:

```javascript
// 1. Import OpenAI
const { OpenAI } = require('openai');

// 2. Initialize OpenAI with your API Key
const openai = new OpenAI({
  apiKey: 'YOUR_API_KEY_HERE', // 🔥 Replace this with your real key!
});

// 3. Send a prompt to OpenAI
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

Boom! 💥  
You just built your **first AI-powered bot**!!

---

**_Mini Practical Exam_**

Let's test what you've learned!

---

### 📝 Practical Exercise

> 1. Change the prompt from  
> `"Tell me a fun fact about space!"`  
> ➔ to ask: `"Give me a motivational quote!"`
> 2 Add a second prompt to ask:  
> `"What is Node.js in one sentence?"`

(👀 Tip: You can call `askAI()` twice or modify the function to send multiple prompts.)

---

### ✅ Bonus Challenge

- Try asking **ANY question** you want!
- Try **changing the model** from `gpt-3.5-turbo` to another one like `gpt-4` if your API key allows.
- **Print the answers in a more styled way** (like adding emojis 🌟, etc.)

---

Recap

Today you learned:

- How to create a simple Node.js app 🛠️
- How to install and use the `openai` npm package 📦
- How to send prompts and get responses back from the AI 🤖
- How to experiment and modify your code! 🧪

---

> **Remember:**  
> Great coders learn by **doing small projects** like this every day!  
> You're already on the right path. 🌟

---

Next Microlearning Idea (If you want)

- How to make your bot talk in the terminal like a real conversation.
- How to build a simple Express server that answers with AI.

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
