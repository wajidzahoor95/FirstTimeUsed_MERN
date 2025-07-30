# FirstTimeUsed_MERN
Here’s a beginner-friendly, step-by-step guide to download and install VS Code, Node.js, React, Express, and MongoDB on your system. This guide will help you set up your full-stack development environment from scratch, including using the VS Code terminal.
#
Create a complete setup for building MERN stack apps (MongoDB, Express, React, Node.js) using VS Code.


---

✅ Step 1: Install Google Chrome (Optional but recommended)

Why? It helps with developer tools and works well with VS Code extensions.

Visit: https://www.google.com/chrome

Click Download Chrome

Install it like a normal app



---

✅ Step 2: Install VS Code (Visual Studio Code)

Why? It’s a free, powerful code editor for web development.

1. Go to: https://code.visualstudio.com


2. Click on Download for Windows/Linux/Mac


3. Open the downloaded file and install it


4. During installation, check:

✅ "Add to PATH"

✅ "Open with Code" (right-click menu)




➡ After installation, open VS Code


---

✅ Step 3: Install Node.js & npm

Why? Node.js runs JavaScript on the server. npm is the Node Package Manager (used to install packages).

1. Visit: https://nodejs.org


2. Click LTS (Long-Term Support) version


3. Download and install


4. After installing, open VS Code, press Ctrl + ~ to open terminal, and type:



node -v
npm -v

You should see versions like:

v20.10.0
10.2.4

✅ Means Node.js and npm are installed.


---

✅ Step 4: Install MongoDB (Database)

Option 1: Install MongoDB Community Server

1. Go to: https://www.mongodb.com/try/download/community


2. Choose your OS (Windows/macOS/Linux)


3. Download and install


4. Use the default settings, and make sure MongoDB Compass is checked (GUI tool)



Option 2 (Optional): Use MongoDB Atlas (Online)

Signup at: https://www.mongodb.com/cloud/atlas


---

✅ Step 5: Install React.js (Frontend)

1. Open VS Code terminal


2. Navigate to a folder where you want your project:



cd Desktop
mkdir my-app
cd my-app

3. Create a React app:



npx create-react-app client

It will take some time ⏳

4. After it's done:



cd client
npm start

Your React app will open in the browser at http://localhost:3000


---

✅ Step 6: Set Up Node.js + Express.js (Backend)

1. Go back to your project folder:



cd ..
mkdir server
cd server

2. Initialize a Node project:



npm init -y

3. Install Express:



npm install express

4. Create a basic server:



👉 Create a file named index.js:

const express = require('express');
const app = express();
const PORT = 5000;

app.get('/', (req, res) => {
  res.send('Hello from Express!');
});

app.listen(PORT, () => {
  console.log(Server running on http://localhost:${PORT});
});

5. Run your server:



node index.js

✅ Visit: http://localhost:5000 — you’ll see "Hello from Express!"


---

✅ Step 7: Connect Express to MongoDB

1. Install MongoDB Node driver:



npm install mongoose

2. Update index.js:



const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/mydatabase', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
})
.then(() => console.log('MongoDB connected'))
.catch(err => console.log(err));

3. Make sure MongoDB is running locally (or use Atlas)




---

✅ Final Folder Structure (Basic)

my-app/
│
├── client/       ← React frontend
└── server/       ← Node + Express + MongoDB backend


---

✅ Extra: VS Code Extensions for MERN Stack

🧩 ESLint – clean code

🎨 Prettier – auto format

🌐 Live Server – for static HTML/JS

📦 MongoDB for VS Code

🚀 Thunder Client – test API (like Postman)



---

✅ Helpful Terminal Commands Summary

Command	Use

cd foldername	go to folder
mkdir name	create folder
code .	open VS Code in current folder
npm start	run React app
node file.js	run Node.js file
npm install packagename	install package
Ctrl + C	stop server in terminal

Great question! Yes, you can run React (frontend) and Node.js + Express (backend/server) at the same time, so your full-stack app works together. Here's how to do it:


---

✅ Step-by-Step Guide to Run React and Node.js Server Together

📁 Your folder structure:

my-app/
├── client/     ← React frontend
└── server/     ← Node.js + Express backend


---

🔷 Step 1: Start the React App

1. Open VS Code


2. Open terminal in client folder:



cd client
npm start

This will open http://localhost:3000


---

🔷 Step 2: Start the Node.js + Express Server

Open a second terminal window or tab in VS Code (you can press ➕ icon in terminal tab).

1. Go to the server folder:



cd ../server

2. Run your server:



node index.js

OR if you're using nodemon (optional, auto-reloads server):

npm install -g nodemon
nodemon index.js

This runs server on http://localhost:5000


---

✅ Now both are running:

App	Port

React	localhost:3000
Express.js	localhost:5000



---

🔄 Optional: Connect React → Express (Proxy Setup)

If you want to call your backend from React easily (without CORS issues), do this:

1. Go to client/package.json


2. Add this line:



"proxy": "http://localhost:5000",

Now, in React, you can fetch like this:

fetch('/api/something')

It will automatically go to http://localhost:5000/api/something


---

💡 Bonus: Single Command to Run Both (Optional Advanced)

You can use a tool like concurrently to run both frontend and backend with one command:

1. Go to main folder (my-app/)


2. Install:



npm install concurrently --save-dev

3. In the main folder, create package.json like this:



{
  "name": "fullstack-app",
  "scripts": {
    "start": "concurrently \"npm run server\" \"npm run client\"",
    "server": "cd server && nodemon index.js",
    "client": "cd client && npm start"
  }
}

4. Run both:



npm start

✅ This will run React and Express together with one command.
