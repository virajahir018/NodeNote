# 🚀 Node.js, Express & Backend Development Cheat Sheet

Welcome to the ultimate backend development cheat sheet. This guide covers core concepts of Node.js, Express.js, Mongoose, Databases, and JavaScript Runtime Architecture with both Hinglish and English explanations.

---

## 📌 Table of Contents
1. [Express.js Basics](#1-expressjs-basics)
2. [File System (fs)](#2-file-system-fs)
3. [Request & Middleware](#3-request--middleware)
4. [Mongoose & MongoDB](#4-mongoose--mongodb)
5. [Authentication & Security (bcrypt & JWT)](#5-authentication--security-bcrypt--jwt)
6. [Process & Configuration](#6-process--configuration)
7. [Advanced Database & File Uploads](#7-advanced-database--file-uploads)
8. [JavaScript Runtime & Architecture (Event Loop, Call Stack)](#8-javascript-runtime--architecture)
9. [Module Systems (CJS vs ESM)](#9-module-systems-cjs-vs-esm)
10. [Web Concepts (API & CORS)](#10-web-concepts-api--cors)

---

## 1. Express.js Basics

### # Express Install
* **Hinglish:** Node.js सिर्फ JavaScript चलाता है। Express हमें आसानी से API बनाने में मदद करता है।
* **English:** Node.js only executes JavaScript. Express is a minimalist framework built on top of Node.js that helps us build APIs and web applications efficiently.

### # Express Import
```javascript
const express = require("express");
```
* **Hinglish:** `require()` किसी package को अपने project में लाता है। यानी `const express = require("express")` का मतलब है: Express library को import करके `express` नाम के variable में रख दो।
* **English:** The `require()` function imports an external package into your project. Here, we import the Express library and store it inside the `express` variable for future use.

### # App Creation
```javascript
const app = express();
```
* **Hinglish:** `express()` एक application बनाता है। अब आपकी सारी APIs, routes और middlewares इसी `app` object पर बनेंगी।
* **English:** Executing `express()` initializes a new Express application instance. This `app` object is used to define routes, register middlewares, and start the HTTP server.

### # app.listen()
```javascript
app.listen(3000, () => console.log("Server running on port 3000"));
```
* **Hinglish:** यह आपके backend server को चालू (start) करता है ताकि वह किसी specific port पर आने वाली requests को सुन सके।
* **English:** This method binds and listens for connections on the specified host and port, successfully starting your backend server.

---

## 2. File System (fs)

### # fs Module
* **Hinglish:** `fs` का मतलब है File System। इससे हम files को read, write, update, और delete कर सकते हैं।
* **English:** `fs` stands for File System. It is a built-in Node.js module that allows developers to interact with the physical file system to read, write, update, and delete files.

### # fs.readFileSync()
```javascript
const data = fs.readFileSync("users.json", "utf-8");
```
* **Hinglish:** यह `users.json` फ़ाइल को synchronous (लाइन-बाय-लाइन) तरीके से पढ़ता है। जब तक फ़ाइल पूरी लोड नहीं होगी, कोड आगे नहीं बढ़ेगा।
* **English:** This method reads the contents of a file (`users.json`) synchronously, meaning it blocks the execution of the remaining code until the file reading is completely finished.

---

## 3. Request & Middleware

### # express.json()
```javascript
app.use(express.json());
```
* **Hinglish:** यह incoming JSON data को JavaScript object में convert करता है, ताकि हम `req.body` से डेटा को आसानी से इस्तेमाल कर सकें।
* **English:** This is a built-in middleware in Express that parses incoming requests with JSON payloads and populates `req.body` with the parsed JavaScript object.

### # req.body
* **Hinglish:** Client (जैसे React/Postman) जो भी JSON डेटा backend को भेजता है, वह हमें `req.body` के अंदर मिलता है।
* **English:** `req.body` contains key-value pairs of data submitted in the request body. By default, it is undefined and populated when you use body-parsing middleware like `express.json()`.

### # express.Router()
* **Hinglish:** यह routes का एक group बनाने में मदद करता है। उस group में आप GET, POST, PUT, DELETE सब इस्तेमाल कर सकते हो। यह कोड को साफ़ रखने के लिए ज़रूरी है।
* **English:** `express.Router()` is used to create modular, mountable route handlers. A router instance is a complete routing and middleware system, often referred to as a "mini-app".

**Routing Example:**
* **GET** `/products` -> Fetch all products
* **POST** `/products` -> Create a new product
* **PUT** `/products/:id` -> Update a product by ID
* **DELETE** `/products/:id` -> Delete a product by ID

### # app.use()
* **Hinglish:** Express.js में middleware को global या specific route पर register करने के लिए इस्तेमाल होता है। सरल भाषा में: जो भी request आए, उसे पहले यह function handle करे, फिर आगे भेजे।
* **English:** This function is used to register middleware in your Express application. Every incoming request passes through the middleware registered via `app.use()` before reaching the final route handler.

### # Middleware & next()
* **Hinglish:** Middleware एक ऐसा function है जो Request और Response के बीच में चलता है। सबसे महत्वपूर्ण चीज़ `next()` है: "अब अगला middleware या route चलाओ।" अगर `next()` नहीं लिखोगे तो request वहीं अटक जाएगी।
* **English:** Middleware functions have access to the request (`req`) and response (`res`) objects. The `next()` function is a crucial callback that tells Express to pass control to the subsequent middleware or route handler. Without it, the request hangs indefinitely.

---

## 4. Mongoose & MongoDB

### # Mongoose
* **Hinglish:** Mongoose, Node.js के अंदर MongoDB के साथ आसानी से काम करने के लिए एक library (ODM - Object Data Modeling) है।
  * MongoDB = Database
  * Mongoose = Node.js और MongoDB के बीच का पुल (Bridge/Helper)
* **English:** Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js. It acts as a structural bridge between your application logic and the MongoDB database.

### # Why do we need Mongoose?
* **Hinglish:** अगर आप directly MongoDB driver यूज़ करोगे, तो डेटा स्ट्रक्चर और validation खुद मैन्युअली संभालना पड़ेगा। Mongoose हमें Schema, Model, Validation, और Query methods जैसे रेडीमेड फीचर्स देता है।
* **English:** Direct interaction with MongoDB requires manual management of validation and data mapping. Mongoose provides a straight-forward, schema-based solution to model your application data, complete with built-in type casting, validation, and query building.

### # Schema
```javascript
const userSchema = new mongoose.Schema({ name: String, age: Number });
```
* **Hinglish:** Schema बताता है कि हमारे database में data किस structure और किस data type (String, Number, etc.) का स्टोर होगा। यह डेटा के नियम तय करता है।
* **English:** A Schema defines the blueprint, structure, and data types of the documents that will be stored within a specific MongoDB collection.

### # Model
```javascript
const User = mongoose.model("User", userSchema);
```
* **Hinglish:** Schema सिर्फ नियम तय करता है, लेकिन MongoDB के साथ actual काम (Create, Find, Update, Delete) करने के लिए हम Model बनाते हैं।
* **English:** A Mongoose Model is a wrapper on the Mongoose Schema. It provides the interface to the database for creating, querying, updating, and deleting documents (CRUD operations).

### # populate()
```javascript
const order = await Order.find().populate("user");
```
* **Hinglish:** Mongoose का एक कमाल का method है जो `ObjectId` के ज़रिए दूसरे collection से जुड़े हुए document का actual डेटा निकाल कर जोड़ देता है (जैसे SQL में Join काम करता है)।
* **English:** `populate()` is a Mongoose method used to automatically replace specified paths in a document with actual documents from other collections based on references (`ObjectId`).

---

## 5. Authentication & Security

### # bcrypt
* **Hinglish:** `bcrypt` पासवर्ड को सुरक्षित बनाने के लिए इस्तेमाल होता है। यह original पासवर्ड को 'hash' (एक गुप्त कोड) में बदल देता है, ताकि डेटाबेस हैक होने पर भी किसी को असली पासवर्ड न मिले।
* **English:** `bcrypt` is a secure password-hashing library. It hashes passwords using salt rounds to ensure that plain-text user passwords are never stored exposed inside the database.

### # JWT (JSON Web Token)
* **Hinglish:** इसका उपयोग यूज़र के Login करने के बाद उसे authenticate और पहचान करने के लिए होता है। जब यूज़र लॉगिन करता है, तो बैकएंड उसे एक Token देता है। अगली बार कोई भी सुरक्षित पेज (जैसे Profile) खोलने के लिए फ्रंटएंड यह टोकन वापस भेजता है।
* **English:** JWT is an open standard used to securely transmit information between parties as a JSON object. In authentication, when a user logs in, a token is issued. For subsequent requests, the client sends this token to verify identity.

---

## 6. Process & Configuration

### # Process Object
* **Hinglish:** `process` एक built-in global object है जिससे हम चल रहे Node.js प्रोग्राम और उसके Environment की जानकारी लेते हैं।
* **English:** The `process` object is a global instance in Node.js that provides information about, and control over, the current Node.js runtime process.

1. **`process.env`**: Environment variables (जैसे Ports, API keys) को एक्सेस करने के लिए।
2. **`process.exit()`**: चल रहे प्रोग्राम को जबरन बंद (stop) करने के लिए।
3. **`process.cwd()`**: Current Working Directory (आप अभी किस फोल्डर में हैं) देखने के लिए।
4. **`process.argv`**: Command-line से पास किए गए arguments को एरे के रूप में देखने के लिए।

### # Configuration & .env (Environment)
* **Hinglish:** **Configuration** का मतलब है प्रोजेक्ट की महत्वपूर्ण सेटिंग्स को एक जगह संभालना। **.env** एक गुप्त फ़ाइल होती है जिसमें हम Secret Keys, DB URLs आदि रखते हैं। इसे `dotenv` पैकेज और `process.env` की मदद से रीड किया जाता है।
