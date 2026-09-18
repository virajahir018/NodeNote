# Node.js Interview Questions & Answers

### Hindi + English | Beginner to Intermediate

---

## 1. What is Node.js?

### English

Node.js is a **JavaScript runtime environment** that allows us to execute JavaScript outside the browser. It is built on Google's V8 JavaScript engine.

### Hindi

Node.js ek **JavaScript runtime environment** hai jiske through hum browser ke bahar JavaScript run kar sakte hain. Ye Google ke V8 engine par built hai.

### Interview Answer

> Node.js is a JavaScript runtime environment that allows us to run JavaScript outside the browser.

---

## 2. Why do we use Node.js?

### English

Node.js is commonly used for:

* Backend development
* REST APIs
* Real-time applications
* Web servers
* Microservices
* CLI applications

It uses non-blocking I/O, which makes it suitable for handling many I/O operations efficiently.

### Hindi

Node.js ka use mainly:

* Backend
* APIs
* Web servers
* Real-time applications
* Microservices

banane ke liye hota hai.

### Interview Answer

> Node.js is useful for building scalable I/O-heavy applications because it uses an event-driven, non-blocking I/O model.

---

## 3. Is Node.js a programming language?

### English

No. Node.js is not a programming language. It is a **runtime environment** for executing JavaScript.

### Hindi

Nahi. Node.js programming language nahi hai. Ye JavaScript ko browser ke bahar run karne ka runtime environment hai.

---

## 4. Is Node.js a framework?

### English

No. Node.js is a runtime environment. Frameworks such as Express.js run on top of Node.js.

### Hindi

Node.js framework nahi hai. Ye runtime environment hai. Express.js Node.js ke upar run karne wala framework hai.

---

## 5. What is V8?

### English

V8 is Google's JavaScript engine. It is used by Chrome and Node.js to execute JavaScript.

### Hindi

V8 Google ka JavaScript engine hai jo JavaScript code ko execute karta hai. Chrome aur Node.js dono V8 use karte hain.

---

## 6. What is npm?

### English

npm stands for **Node Package Manager**. It is used to install, manage, and publish JavaScript packages.

```bash
npm install express
```

### Hindi

npm ka use packages install aur manage karne ke liye hota hai.

---

## 7. What is package.json?

### English

`package.json` contains important information about a Node.js project, such as:

* Project name
* Version
* Dependencies
* Scripts
* Project configuration

Example:

```json
{
  "name": "my-project",
  "version": "1.0.0"
}
```

### Hindi

`package.json` project ki important information aur dependencies ko store karta hai.

---

## 8. What is package-lock.json?

### English

`package-lock.json` records the exact dependency versions installed for a project and their dependency tree.

### Hindi

`package-lock.json` installed packages ke exact versions aur dependency tree ko lock karta hai.

---

## 9. What is a module in Node.js?

### English

A module is a reusable unit of code that can be imported and used in another file.

Example:

```js
const fs = require("fs");
```

### Hindi

Module reusable code ka ek part hota hai jise doosri file me import/use kar sakte hain.

---

## 10. What is CommonJS?

### English

CommonJS is a module system commonly used in Node.js.

```js
const express = require("express");

module.exports = router;
```

### Hindi

CommonJS Node.js me commonly used module system hai jisme `require()` aur `module.exports` use hote hain.

---

## 11. What is ESM?

### English

ESM stands for **ECMAScript Modules**. It uses `import` and `export`.

```js
import express from "express";

export default router;
```

### Hindi

ESM JavaScript ka standard module system hai jisme `import` aur `export` use hote hain.

---

## 12. CommonJS vs ESM

| CommonJS                            | ESM                               |
| ----------------------------------- | --------------------------------- |
| `require()`                         | `import`                          |
| `module.exports`                    | `export`                          |
| Commonly used in older Node.js code | Standard JavaScript module system |
| Node.js ecosystem me widely seen    | Modern JS projects me widely used |

---

## 13. What is Express.js?

### English

Express.js is a web framework for Node.js used to build web servers and APIs.

```js
const express = require("express");

const app = express();
```

### Hindi

Express.js Node.js ka web framework hai jo APIs aur web servers banane me help karta hai.

---

## 14. What is `express.json()`?

### English

`express.json()` is middleware that parses incoming JSON request bodies.

```js
app.use(express.json());
```

### Hindi

`express.json()` incoming JSON data ko parse karke `req.body` me available karne me help karta hai.

---

## 15. What is `express.Router()`?

### English

`express.Router()` creates a modular router that can contain related routes.

```js
const router = express.Router();

router.get("/users", getUsers);
```

### Hindi

`express.Router()` routes ko separate aur organized files me manage karne ke liye use hota hai.

---

## 16. What is middleware?

### English

Middleware is a function that runs during the request-response cycle.

It can:

* Modify `req` or `res`
* Validate data
* Authenticate users
* Log requests
* End the request
* Call `next()`

Example:

```js
function auth(req, res, next) {
  console.log("Auth middleware");
  next();
}
```

### Hindi

Middleware request aur response ke beech execute hone wala function hai.

---

## 17. What is `next()`?

### English

`next()` passes control to the next middleware or route handler.

```js
function middleware(req, res, next) {
  console.log("Middleware");
  next();
}
```

### Hindi

`next()` request ko next middleware ya handler tak bhejta hai.

---

## 18. What is `req.body`?

### English

`req.body` contains data sent by the client in the request body.

Example:

```js
const { name, email } = req.body;
```

### Hindi

Client se body me jo data aata hai usko `req.body` se access karte hain.

---

## 19. What is `req.params`?

### English

`req.params` contains route parameters.

```js
app.get("/users/:id", (req, res) => {
  console.log(req.params.id);
});
```

URL:

```text
/users/123
```

Output:

```text
123
```

### Hindi

URL ke dynamic parameters ko `req.params` se access karte hain.

---

## 20. What is `req.query`?

### English

`req.query` contains query string parameters.

```text
/products?search=shoes
```

```js
req.query.search;
```

### Hindi

URL ke query parameters ko `req.query` se access karte hain.

---

## 21. Difference between `req.params`, `req.query`, and `req.body`

| Type   | Example             | Access           |
| ------ | ------------------- | ---------------- |
| Params | `/users/123`        | `req.params.id`  |
| Query  | `/users?name=Viraj` | `req.query.name` |
| Body   | JSON request data   | `req.body`       |

---

## 22. What is REST API?

### English

A REST API is an HTTP-based API that follows REST principles to allow clients and servers to communicate using resources and HTTP methods.

Common methods:

```text
GET
POST
PUT
PATCH
DELETE
```

### Hindi

REST API client aur server ke beech data communicate karne ke liye HTTP methods aur resource-based URLs use karti hai.

---

## 23. What is GET?

### English

GET is generally used to retrieve data.

```js
app.get("/users", (req, res) => {
  res.json([]);
});
```

### Hindi

GET ka use data fetch/retrieve karne ke liye hota hai.

---

## 24. What is POST?

### English

POST is generally used to submit data or create a resource.

```js
app.post("/users", (req, res) => {
  console.log(req.body);
});
```

### Hindi

POST ka use data send karne ya new resource create karne ke liye hota hai.

---

## 25. PUT vs PATCH

### PUT

Generally used to replace the representation of a resource.

### PATCH

Generally used for partial updates.

### Hindi

* `PUT` → resource ko generally replace/update karne ke liye
* `PATCH` → resource ke specific fields update karne ke liye

---

## 26. What is DELETE?

### English

DELETE is used to request deletion of a resource.

```js
app.delete("/users/:id", handler);
```

### Hindi

DELETE ka use resource delete karne ke liye hota hai.

---

## 27. What is asynchronous programming?

### English

Asynchronous programming allows an operation to complete later without blocking the execution of other JavaScript work.

Example:

```js
setTimeout(() => {
  console.log("Done");
}, 1000);

console.log("Next");
```

### Hindi

Asynchronous programming me long-running operation ke wait ke time other work continue ho sakta hai.

---

## 28. What is non-blocking I/O?

### English

Non-blocking I/O allows Node.js to start an I/O operation and continue processing other work instead of waiting synchronously for the operation to finish.

### Hindi

Node.js I/O operation ke complete hone ka synchronously wait nahi karta; meanwhile other work process kar sakta hai.

---

## 29. What is the Event Loop?

### English

The Event Loop coordinates asynchronous callbacks and helps Node.js handle many I/O operations while JavaScript execution runs on a main thread.

### Hindi

Event Loop asynchronous operations ke callbacks ko appropriate time par execute karne me help karta hai.

Simple flow:

```text
Call Stack
   ↓
Async Operation
   ↓
Node.js / libuv
   ↓
Queue
   ↓
Event Loop
   ↓
Call Stack
```

---

## 30. What is libuv?

### English

libuv is a library used by Node.js that provides the event loop and asynchronous I/O capabilities, including a thread pool for certain operations.

### Hindi

libuv Node.js ke asynchronous I/O aur event loop infrastructure ka important part hai. Kuch operations ke liye ye thread pool bhi provide karta hai.

---

## 31. Is Node.js single-threaded?

### English

JavaScript execution in Node.js uses a main thread, but Node.js is not limited to a single OS thread. It can use libuv's thread pool and other system resources for certain operations.

### Hindi

Node.js me JavaScript code ka main execution single thread par hota hai, lekin Node.js kuch operations ke liye background threads/thread pool aur OS capabilities use kar sakta hai.

### Interview Answer

> Node.js uses a single main JavaScript thread, while some operations can be handled using background resources such as libuv's thread pool.

---

## 32. What is callback?

### English

A callback is a function passed to another function to be executed later.

```js
function greet(name, callback) {
  console.log(name);
  callback();
}
```

### Hindi

Ek function ko doosre function me argument ke roop me pass karke baad me execute karna callback kehlata hai.

---

## 33. What is Promise?

### English

A Promise represents the eventual completion or failure of an asynchronous operation.

States:

```text
Pending
Fulfilled
Rejected
```

### Hindi

Promise asynchronous operation ke future result ko represent karta hai.

---

## 34. What is async/await?

### English

`async/await` is syntax built on Promises that makes asynchronous code easier to read.

```js
async function getUsers() {
  const users = await User.find();
  return users;
}
```

### Hindi

`async/await` Promise-based asynchronous code ko readable banata hai.

---

## 35. What is `try...catch`?

### English

`try...catch` is used to handle runtime errors.

```js
try {
  // code
} catch (error) {
  console.log(error.message);
}
```

### Hindi

Runtime errors ko handle karne ke liye `try...catch` use hota hai.

---

## 36. What is Mongoose?

### English

Mongoose is an ODM library for MongoDB and Node.js. It provides schemas, models, validation, middleware, and other features for working with MongoDB.

### Hindi

Mongoose MongoDB ke saath Node.js me kaam karne ke liye ODM library hai.

---

## 37. What is Schema?

### English

A Mongoose Schema defines the structure and rules for documents in a MongoDB collection.

```js
const userSchema = new mongoose.Schema({
  name: String,
  email: String,
  password: String
});
```

### Hindi

Schema MongoDB document ka structure aur rules define karta hai.

---

## 38. What is Model?

### English

A Mongoose Model is created from a schema and provides an interface for interacting with a MongoDB collection.

```js
const User = mongoose.model("User", userSchema);
```

### Hindi

Model schema ke basis par banta hai aur database collection ke saath interact karne ke liye use hota hai.

---

## 39. What is `populate()`?

### English

`populate()` replaces referenced ObjectIds with the corresponding documents.

```js
Order.find()
  .populate("user");
```

### Hindi

`populate()` referenced ID ki jagah related document ka data lane ke liye use hota hai.

---

## 40. What is bcrypt?

### English

bcrypt is a password hashing library commonly used to securely hash passwords before storing them.

```js
const hash = await bcrypt.hash(password, 10);
```

### Hindi

bcrypt password ko hash karne ke liye use hota hai. Password ko plain text me database me store nahi karna chahiye.

---

## 41. Hashing vs Encryption

### Hashing

* Generally one-way
* Password storage ke liye commonly used

### Encryption

* Data ko encrypt/decrypt kiya ja sakta hai using a key
* Confidential data transmission/storage ke use cases me common

### Interview Answer

> Hashing is generally one-way, while encryption is designed to be reversible with the appropriate key.

---

## 42. What is JWT?

### English

JWT stands for **JSON Web Token**. It is a compact token format commonly used for authentication and authorization.

Example:

```js
const token = jwt.sign(
  { id: user._id },
  process.env.JWT,
  { expiresIn: "1d" }
);
```

### Hindi

JWT ka use authentication aur authorization ke liye commonly hota hai.

---

## 43. What is `jwt.verify()`?

### English

`jwt.verify()` verifies a JWT's signature and validates claims such as expiration when applicable.

```js
const decoded = jwt.verify(token, process.env.JWT);
```

### Hindi

`jwt.verify()` token ko verify karta hai aur valid hone par decoded payload return karta hai.

---

## 44. What is `.env`?

### English

`.env` is commonly used to store environment-specific configuration values.

Example:

```text
PORT=5000
MONGO_URI=...
JWT=...
```

### Hindi

`.env` me configuration values aur secrets ko environment variables ke form me rakh sakte hain.

---

## 45. What is `process.env`?

### English

`process.env` provides access to environment variables available to the Node.js process.

```js
const port = process.env.PORT;
```

### Hindi

Node.js application me environment variables access karne ke liye `process.env` use hota hai.

---

## 46. What is CORS?

### English

CORS stands for **Cross-Origin Resource Sharing**. It controls which origins are allowed to make certain cross-origin browser requests to a server.

```js
const cors = require("cors");

app.use(cors());
```

### Hindi

CORS browser ke cross-origin requests ko control karne ke liye use hota hai.

---

## 47. What is HTTP status code?

### English

HTTP status codes tell the client the result of an HTTP request.

Common codes:

```text
200 → OK
201 → Created
400 → Bad Request
401 → Unauthorized
403 → Forbidden
404 → Not Found
500 → Internal Server Error
```

### Hindi

Status code client ko batata hai ki request ka result kya raha.

---

## 48. Authentication vs Authorization

### Authentication

### English

Authentication verifies **who the user is**.

### Hindi

Authentication check karta hai ki user kaun hai.

### Authorization

### English

Authorization determines **what the authenticated user is allowed to do**.

### Hindi

Authorization check karta hai ki authenticated user kya kar sakta hai.

Example:

```text
Login → Authentication
Admin access → Authorization
```

---

## 49. What is CRUD?

CRUD stands for:

```text
C → Create
R → Read
U → Update
D → Delete
```

### Hindi

Database ke basic operations ko CRUD kehte hain.

Example:

```text
POST   → Create
GET    → Read
PUT/PATCH → Update
DELETE → Delete
```

---

## 50. What is Multer?

### English

Multer is middleware for handling `multipart/form-data`, commonly used for file uploads in Node.js/Express applications.

```js
const multer = require("multer");

const upload = multer({
  dest: "uploads/"
});
```

### Hindi

Multer Node.js/Express me file upload handle karne ke liye commonly use hota hai.

---

# Intermediate Interview Questions

---

## 51. What is middleware order?

### English

Express middleware executes in the order in which it is registered.

```js
app.use(first);
app.use(second);
app.get("/", handler);
```

Flow:

```text
first
 ↓
second
 ↓
handler
```

### Hindi

Express me middleware jis order me register hota hai, generally usi order me execute hota hai.

---

## 52. What happens if we don't call `next()`?

### English

If middleware neither sends a response nor calls `next()`, the request can remain pending.

### Hindi

Agar middleware response bhi nahi bhejta aur `next()` bhi call nahi karta, to request hang ho sakti hai.

---

## 53. What is error-handling middleware?

### English

Express error-handling middleware has four parameters:

```js
function errorHandler(err, req, res, next) {
  res.status(500).json({
    message: err.message
  });
}
```

### Hindi

Error handle karne ke liye Express me special middleware hota hai jisme 4 parameters hote hain:

```text
err
req
res
next
```

---

## 54. What is `fs` module?

### English

`fs` stands for File System. It provides APIs for working with files and directories.

```js
const fs = require("fs");
```

### Hindi

`fs` Node.js ka built-in module hai jo files aur folders ke saath work karne ke liye use hota hai.

---

## 55. `readFileSync()` vs `readFile()`

### `readFileSync()`

Synchronous operation hai aur current JavaScript execution ko block kar sakta hai.

```js
const data = fs.readFileSync("file.txt", "utf8");
```

### `readFile()`

Asynchronous API hai.

```js
fs.readFile("file.txt", "utf8", (err, data) => {
  console.log(data);
});
```

### Interview Answer

> `readFileSync()` is synchronous and can block execution, while `readFile()` provides an asynchronous API.

---

## 56. What is `app.listen()`?

### English

`app.listen()` starts an HTTP server that listens for incoming connections on a specified port.

```js
app.listen(5000, () => {
  console.log("Server running");
});
```

### Hindi

`app.listen()` server ko specified port par start karta hai.

---

## 57. What is API?

### English

API stands for **Application Programming Interface**. It defines a way for different software components to communicate.

### Hindi

API ek interface hai jiske through different software systems/components ek doosre ke saath communicate karte hain.

---

## 58. What is RESTful API?

### English

A RESTful API follows REST architectural principles such as resource-oriented URLs, standard HTTP methods, and stateless requests.

### Hindi

RESTful API REST principles follow karti hai aur resources ko HTTP methods ke through access/update karti hai.

---

## 59. What is JSON?

### English

JSON stands for **JavaScript Object Notation**. It is a text format commonly used to exchange structured data between client and server.

```json
{
  "name": "Viraj",
  "age": 22
}
```

### Hindi

JSON client aur server ke beech structured data exchange karne ke liye commonly use hota hai.

---

## 60. What is environment configuration?

### English

Environment configuration means keeping values such as ports, database URLs, and secrets configurable outside the application code.

### Hindi

Port, database URL aur secrets jaise configuration ko code se bahar environment variables me rakhna environment configuration hai.

---

# Most Important Interview Questions — Quick Revision

| Question     | Short Answer                                  |
| ------------ | --------------------------------------------- |
| Node.js      | JavaScript runtime environment                |
| V8           | JavaScript engine used by Node.js             |
| npm          | Node Package Manager                          |
| Express      | Node.js web framework                         |
| Middleware   | Function in request-response cycle            |
| `next()`     | Passes control to next middleware             |
| `req.body`   | Request body data                             |
| `req.params` | Route parameters                              |
| `req.query`  | Query parameters                              |
| REST API     | HTTP-based resource-oriented API              |
| Promise      | Represents future async result                |
| async/await  | Promise-based async syntax                    |
| Event Loop   | Coordinates async callbacks                   |
| libuv        | Provides async I/O infrastructure             |
| Mongoose     | MongoDB ODM                                   |
| Schema       | Defines document structure/rules              |
| Model        | Interface for MongoDB collection              |
| populate     | Loads referenced documents                    |
| bcrypt       | Password hashing                              |
| JWT          | Token format for authentication/authorization |
| `.env`       | Environment configuration                     |
| CORS         | Controls browser cross-origin requests        |
| CRUD         | Create, Read, Update, Delete                  |
| Multer       | Handles multipart/form-data/file uploads      |
| API          | Interface for software communication          |

---

# 10 Questions You Should Definitely Prepare

### 1. What is Node.js?

> Node.js is a JavaScript runtime environment that allows us to execute JavaScript outside the browser.

### 2. Why Node.js?

> Node.js uses an event-driven, non-blocking I/O model, making it suitable for I/O-heavy and scalable applications.

### 3. Is Node.js single-threaded?

> Node.js uses a single main JavaScript thread, while certain operations can use background resources such as libuv's thread pool.

### 4. What is middleware?

> Middleware is a function that runs during the request-response cycle and can modify the request or response, end the request, or pass control using `next()`.

### 5. What is Express.js?

> Express.js is a web framework for Node.js used to build servers and APIs.

### 6. What is Mongoose?

> Mongoose is an ODM library that provides a structured way to work with MongoDB from Node.js.

### 7. What is JWT?

> JWT is a compact token format commonly used for authentication and authorization.

### 8. What is bcrypt?

> bcrypt is a password hashing library used to securely hash passwords before storing them.

### 9. What is Event Loop?

> The Event Loop helps Node.js coordinate asynchronous operations and callbacks while JavaScript runs on the main thread.

### 10. Authentication vs Authorization?

> Authentication verifies who the user is, while authorization determines what the authenticated user is allowed to do.
