# Node.js Notes

## 1. Node.js kya hai?

**Node.js** ka use mainly **server-side (Backend) web development** ke liye kiya jata hai.

Node.js koi programming language nahi hai. Ye ek **JavaScript Runtime Environment** hai jo JavaScript code ko browser ke bahar, yani **computer ya server** par run karne ki permission deta hai.

### Simple Definition

> **Node.js is a JavaScript Runtime Environment that allows us to run JavaScript outside the browser.**

---

## 2. Node.js ka use kyu karte hain?

### 2.1 Frontend aur Backend ke liye ek hi language

Node.js ki help se hum **Frontend aur Backend dono mein JavaScript** use kar sakte hain.

Pehle developers ko:

* Frontend → JavaScript
* Backend → PHP / Python / Java

jaise different languages use karni padti thi.

Node.js ke saath:

```text
Frontend  → JavaScript
Backend   → JavaScript
```

Is approach ko **Full Stack JavaScript Development** kaha ja sakta hai.

---

### 2.2 Fast Performance

Node.js **Google Chrome ke V8 JavaScript Engine** par based hai.

V8 JavaScript code ko efficiently execute karta hai, jiski wajah se Node.js applications fast perform kar sakti hain.

```text
JavaScript Code
       ↓
    V8 Engine
       ↓
   Execution
```

---

### 2.3 Non-Blocking I/O aur Asynchronous Model

Node.js **event-driven** aur **non-blocking I/O model** use karta hai.

Agar koi operation time leta hai, jaise:

* File read karna
* Database se data lana
* Network request
* API call

to Node.js us operation ke complete hone ka wait karke pura server block nahi karta.

Example:

```text
Request 1 → Database operation → Background
Request 2 → Process
Request 3 → Process
Request 4 → Process
```

Is wajah se Node.js I/O-heavy applications ke liye useful hai.

> **Note:** "Node.js single-threaded hai" ka matlab ye nahi hai ki Node.js mein sirf ek hi thread hota hai. JavaScript execution mainly main thread par hota hai, jabki kuch asynchronous operations libuv ke thread pool ya OS facilities ka use kar sakte hain.

---

## 3. Node.js ka use kaha hota hai?

Node.js ka use kai types ke applications banane mein hota hai:

* REST APIs
* Backend Servers
* Real-time Applications
* Chat Applications
* Streaming Applications
* Online Games
* Collaborative Applications
* Microservices

### Example

```text
Client
  ↓
Node.js Server
  ↓
Database
  ↓
Response
```

---

# npm — Node Package Manager

## 4. npm kya hai?

**npm** ka commonly used full form **Node Package Manager** hai.

npm Node.js ecosystem ka **package manager aur package registry** hai.

Node.js install karne par normally npm bhi install ho jata hai.

Simple words mein:

> **npm ki help se hum apne project mein external packages install, manage aur use kar sakte hain.**

---

## 5. npm ke do important parts

### 5.1 npm Registry

npm Registry ek online repository hai jahan developers packages publish karte hain.

Example packages:

* Express
* Mongoose
* Nodemon
* Axios

---

### 5.2 npm CLI

npm CLI ki help se hum terminal ya CMD se packages ko manage karte hain.

Example:

```bash
npm install express
```

---

# 6. npm ka use kyu karte hain?

Suppose hume apne application mein authentication system banana hai.

Agar hum sab kuch scratch se banayenge, to kaafi time lag sakta hai.

npm ki help se hum existing packages install kar sakte hain.

Example:

```bash
npm install express
```

Isse Express package project mein add ho jayega.

---

# 7. Important npm Files & Commands

| Command / File          | Purpose                                            |
| ----------------------- | -------------------------------------------------- |
| `npm init`              | New Node.js project initialize karta hai           |
| `npm install <package>` | Package install karta hai                          |
| `package.json`          | Project aur dependencies ki information rakhta hai |
| `package-lock.json`     | Installed dependency versions ko lock karta hai    |
| `node_modules`          | Installed packages ka code store karta hai         |

---

## 7.1 `npm init`

Project initialize karne ke liye:

```bash
npm init
```

Ye `package.json` file create karta hai.

Quick setup ke liye:

```bash
npm init -y
```

---

## 7.2 `package.json`

`package.json` ko aap project ki **configuration / manifest file** samajh sakte ho.

Example:

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "dependencies": {
    "express": "^5.0.0"
  }
}
```

Isme project ke baare mein information aur dependencies hoti hain.

---

## 7.3 `npm install`

Package install karne ke liye:

```bash
npm install express
```

Iske baad package project ki dependencies mein add ho jata hai.

---

## 7.4 `node_modules`

Installed packages ka code `node_modules` folder mein hota hai.

Example:

```text
project/
│
├── node_modules/
├── package.json
├── package-lock.json
└── index.js
```

> Generally `node_modules` ko GitHub repository mein commit nahi kiya jata. Iske badle `package.json` aur `package-lock.json` commit kiye jate hain.

---

## 7.5 `package-lock.json`

`package-lock.json` dependencies ke exact installed versions aur dependency tree ki information maintain karta hai.

Isse project ko different systems par more consistent dependency versions ke saath install karne mein help milti hai.

---

# 8. Popular npm Packages

### Express

Backend server aur APIs banane ke liye.

```bash
npm install express
```

### Nodemon

Development ke time server ko automatically restart karne mein help karta hai.

```bash
npm install --save-dev nodemon
```

### Mongoose

MongoDB ke saath kaam karne ke liye.

```bash
npm install mongoose
```

---

# Node.js Modules

## 9. Module kya hota hai?

Node.js mein **Module** code ka ek reusable unit hota hai.

Beginner level par simple way mein:

> **Ek JavaScript file ko module ki tarah use karke hum code ko different files mein divide aur reuse kar sakte hain.**

Agar hum pura project ek hi file mein likhenge:

```text
index.js
   ↓
Login
Database
Users
Products
Orders
```

to project difficult to maintain ho sakta hai.

Isliye hum code ko different modules/files mein divide karte hain.

Example:

```text
project/
│
├── app.js
├── user.js
├── product.js
└── database.js
```

---

# 10. Node.js Modules ke Types

Node.js mein commonly 3 types ke modules samjhe jate hain:

### 10.1 Core Modules

Ye Node.js ke built-in modules hote hain.

Inhe alag se install karne ki zarurat nahi hoti.

Examples:

```text
fs
http
path
os
events
```

Example:

```javascript
const fs = require('fs');
```

---

### 10.2 Local Modules

Ye modules hum khud apne project ke liye create karte hain.

Example:

```text
project/
│
├── app.js
└── calculator.js
```

`calculator.js`:

```javascript
const add = (a, b) => {
  return a + b;
};

module.exports = add;
```

`app.js`:

```javascript
const add = require('./calculator');

console.log(add(10, 20));
```

Output:

```text
30
```

---

### 10.3 Third-Party Modules

Ye modules other developers/organizations ke packages hote hain.

Inhe generally npm se install kiya jata hai.

Examples:

```text
express
mongoose
axios
nodemon
```

Example:

```bash
npm install express
```

---

# Express.js Params

## 11. Params kya hote hain?

Express.js mein **params** ka use URL ke **dynamic values** ko receive karne ke liye hota hai.

For example, agar hume different products ki ID ke basis par data chahiye:

```text
/product/101
/product/102
/product/103
```

Hum har ID ke liye alag route nahi banayenge.

Instead, hum ek dynamic route bana sakte hain:

```text
/product/:id
```

Yahan `:id` ek **Route Parameter** hai.

---

# 12. `req.params`

Express.js mein URL ke route parameters ko:

```javascript
req.params
```

se access kiya jata hai.

Example:

```javascript
const express = require('express');

const app = express();

app.get('/product/:id', (req, res) => {
  const productId = req.params.id;

  res.send(`Aap product number ${productId} dekh rahe hain.`);
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

Agar browser mein request karein:

```text
http://localhost:3000/product/456
```

To:

```javascript
req.params.id
```

ki value hogi:

```text
456
```

Response:

```text
Aap product number 456 dekh rahe hain.
```

---

# 13. Params ka Syntax

Route mein dynamic parameter define karne ke liye `:` use karte hain.

Example:

```javascript
app.get('/user/:username', (req, res) => {
  console.log(req.params.username);
});
```

Agar URL hai:

```text
/user/viraj
```

to:

```javascript
req.params.username
```

ki value hogi:

```text
viraj
```

---

# 14. Multiple Route Parameters

Ek route mein multiple parameters bhi use kar sakte hain.

Example:

```javascript
app.get('/flights/:from/:to', (req, res) => {
  const from = req.params.from;
  const to = req.params.to;

  res.send(`Flight from ${from} to ${to}`);
});
```

Agar URL hai:

```text
/flights/delhi/mumbai
```

to:

```javascript
req.params.from
```

ki value:

```text
delhi
```

Aur:

```javascript
req.params.to
```

ki value:

```text
mumbai
```

Response:

```text
Flight from delhi to mumbai
```

---

# 15. Quick Revision

## Node.js

```text
Node.js = JavaScript Runtime Environment
```

JavaScript ko browser ke bahar run karne ke liye use hota hai.

---

## npm

```text
npm = Node Package Manager
```

Packages ko install aur manage karne ke liye.

---

## Module

```text
Module = Reusable code unit
```

Code ko different files/modules mein organize aur reuse karne ke liye.

---

## Params

```text
Params = URL ke dynamic values
```

Example:

```text
/product/:id
```

URL:

```text
/product/101
```

Access:

```javascript
req.params.id
```

Value:

```text
101
```

---

# Important Interview Points

### What is Node.js?

> Node.js is a JavaScript runtime environment built on the V8 JavaScript engine that allows us to run JavaScript outside the browser, mainly for server-side applications.

### What is npm?

> npm is the package manager and registry ecosystem commonly used with Node.js to install and manage packages and dependencies.

### What is a Module?

> A module is a reusable unit of code that helps us organize an application into smaller and maintainable parts.

### What are `req.params`?

> `req.params` is an object in Express.js that contains route parameters extracted from the URL.

Example:

```javascript
app.get('/user/:id', (req, res) => {
  console.log(req.params.id);
});
```

For:

```text
/user/101
```

Output:

```text
101
```
