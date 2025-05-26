---
title: "Connecting Node.js to MongoDB"
date: "2025-05-04"
author: "Slavo"
image: "ts-big-o-notation.png"
excerpt: "Today, you're going to build a real-world skill—how to **connect your Node.js project to MongoDB** using **Mongoose**, a powerful ODM (Object Data Modeling) library."
isFeatured: false
category: "Nodejs"
---

## 👋 Welcome, Future Full-Stack Engineer

Today, you're going to build a real-world skill—how to **connect your Node.js project to MongoDB** using **Mongoose**, a powerful ODM (Object Data Modeling) library.

### 🧠 What You'll Learn

* Set up your project
* Connect to MongoDB (local or cloud)
* Create, read, and display users from your database

By the end, you’ll be storing and retrieving real data like a pro. Let’s get started!

---

## 🛠️ Step 1: Create Your Project & Install Mongoose

Open your terminal and run:

```bash
mkdir my-first-mongo-app
cd my-first-mongo-app
npm init -y
npm install mongoose
```

✅ You’ve initialized a new Node.js project and installed Mongoose.

---

## 🌍 Step 2: Get MongoDB Running

You need a running MongoDB instance. You can either:

### Option 1: Local MongoDB

If you have MongoDB installed on your system, start the server:

```bash
mongod
```

> 💡 If `mongod` doesn't work, make sure MongoDB is installed and added to your system path.

### Option 2: MongoDB Atlas (Free Cloud Database)

1. Go to [mongodb.com/atlas/database](https://www.mongodb.com/atlas/database)
2. Sign up and create a **free cluster**
3. Create a database user and get your **connection string**

Example connection string (you’ll replace values):

```bash
mongodb+srv://<username>:<password>@cluster0.mongodb.net/myFirstDatabase?retryWrites=true&w=majority
```

🔑 Replace:

* `<username>` → Your MongoDB user
* `<password>` → Your MongoDB password
* `myFirstDatabase` → Your database name

---

## ✍️ Step 3: Write the Code (CRUD Basics)

Create a file called `index.js`:

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

// 3. Define a simple Schema
const UserSchema = new mongoose.Schema({
  name: String,
  age: Number,
});

// 4. Create a Model
const User = mongoose.model('User', UserSchema);

// 5. Create and Save a New User
const createUser = async () => {
  const user = new User({ name: 'Alice', age: 25 });
  await user.save();
  console.log('📝 User saved:', user);
};

// 6. Read All Users
const readUsers = async () => {
  const users = await User.find();
  console.log('📚 All users:', users);
};

// 7. Run the Functions
const run = async () => {
  await createUser();
  await readUsers();
  mongoose.disconnect(); // Close DB connection
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

* **Connected to MongoDB!**
* A user saved with the name "Alice"
* A list of users printed (including Alice)

🎉 **Boom!** You just made your first real database operation.

---

## 🧪 Try It Yourself (Mini Challenge)

Change it up a bit! Replace "Alice" with **your name and age**, and add **another user**.

Example:

```javascript
const user1 = new User({ name: 'Bob', age: 30 });
await user1.save();

const user2 = new User({ name: 'Sarah', age: 22 });
await user2.save();
```

Then run:

```bash
node index.js
```

And confirm that both users appear in the terminal.

---

## 🔁 Recap: What You Learned

* How to **set up Node.js with Mongoose**
* Connect to a **local or cloud MongoDB**
* Define a **Schema and Model**
* Perform **create** and **read** operations

---

## 🖼️ About the Image (Reminder!)

📌 If you're using `ts-big-o-notation.png` as your cover image, **upload it to the same directory** where this blog post lives. Most blogging platforms will use that image as the featured image if properly referenced in front matter.

Happy coding!

\*\* Book Recommendation:

-[React and React Native: A complete hands-on guide to modern web and mobile development with React.js, 3rd Edition](https://amzn.to/3CStF7m)
-[React Key Concepts](https://amzn.to/43XOCJM)
-[Pragmatic Programmer](https://amzn.to/3W1P4oL) **_The: Your journey to mastery, 20th Anniversary Edition_**

[Mentorship & Consulting - Contact us for more info](/contact)

**_Join Our Discord Community_** [Unleash your potential, join a vibrant community of like-minded learners, and let's shape the future of programming together. Click here to join us on Discord.](https://discord.gg/A75tvDvZ)

**_For Consulting and Mentorship, feel free to contact_** [slavo.io](/contact)
