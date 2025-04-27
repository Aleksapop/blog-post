---
title: "Connecting Node.js to MongoDB (First Read/Write Example)"
date: "2025-04-27"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "JavaScript is the backbone of modern web development, powering everything from dynamic websites to complex web applications."
isFeatured: false
category: "Nodejs"
---

**_Welcome, New Engineers_**

Today, you're going to learn something _real_ — how to connect your **Node.js app** to a **MongoDB database** using a popular tool called **Mongoose**.

We'll keep it super simple — your first ever **read/write** with a real database!  
**By the end**, you'll be able to **save** and **fetch** data from MongoDB 🚀.

---

## 🛠️ Step 1: Setup

First, create a new project folder:

```bash
mkdir my-first-mongo-app
cd my-first-mongo-app
npm init -y
npm install mongoose
```

✅ You've installed Mongoose — a library that makes MongoDB easier to use.

---

## 🌐 Step 2: Start MongoDB

You'll need access to a MongoDB database.

**Two options**:

- **Local MongoDB**: If installed on your computer, run `mongod`.
- **MongoDB Atlas** (Free cloud database): [Create an account](https://www.mongodb.com/atlas/database) and get a connection string.

**Connection string example** (from MongoDB Atlas):

```javascript
mongodb+srv://<username>:<password>@cluster0.mongodb.net/myFirstDatabase?retryWrites=true&w=majority
```

_(You'll replace `<username>`, `<password>`, and `myFirstDatabase`.)_

---

## ✍️ Step 3: Write the Code

Create a file: `index.js`

```javascript
// 1. Import mongoose
const mongoose = require('mongoose');

// 2. Connect to MongoDB
mongoose.connect('YOUR_MONGODB_CONNECTION_STRING_HERE', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
})
.then(() => console.log('✅ Connected to MongoDB!'))
.catch((error) => console.error('❌ Connection error:', error));

// 3. Define a simple Schema (blueprint for our data)
const UserSchema = new mongoose.Schema({
  name: String,
  age: Number,
});

// 4. Create a Model based on the Schema
const User = mongoose.model('User', UserSchema);

// 5. Create and Save a new User
const createUser = async () => {
  const user = new User({ name: 'Alice', age: 25 });
  await user.save();
  console.log('📝 User saved:', user);
};

// 6. Read all Users
const readUsers = async () => {
  const users = await User.find();
  console.log('📚 All users:', users);
};

// 7. Run the functions
const run = async () => {
  await createUser();
  await readUsers();
  mongoose.disconnect(); // Close connection when done
};

run();
```

---

## 🚀 Step 4: Run It

In your terminal:

```bash
node index.js
```

✅ You should see:

- **Connected to MongoDB!**
- **User saved:** with Alice's info.
- **All users:** listing Alice and any previous users.

Congrats — **you just did your first real database operation!** 🎉

---

## 🧪 Practical Mini-Exam

**Challenge yourself!**

👉 Modify the `createUser` function to **add your own name** and **age** instead of "Alice".

👉 Then **add another new user** (yes, two users!).

👉 Finally, **read all users** again and **confirm** you see both.

**Example Idea**:

```javascript
const user1 = new User({ name: 'Bob', age: 30 });
await user1.save();
const user2 = new User({ name: 'Sarah', age: 22 });
await user2.save();
```

---

## 🎯 Key Points to Remember

- **Mongoose** helps you connect and work with MongoDB.
- You create a **Schema** (blueprint) and then a **Model** (actual thing you use).
- You **save** and **find** documents easily with Mongoose methods.

---

 _**You’re one step closer to building real-world apps**_

Keep practicing — next you’ll learn **updating** and **deleting** data! 🚀

Happy coding!

\*\* Book Recommendation:

- [React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
- [React Key Concepts](https://amzn.to/43XOCJM)
- [Pragmatic Programmer](https://amzn.to/3W1P4oL) _**The: Your journey to mastery, 20th Anniversary Edition**_

[Mentorship & Consulting - Contact us for more info](/contact)

_**Join Our Discord Community**_ [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

_**For Consulting and Mentorship, feel free to contact**_ [slavo.io](/contact)
