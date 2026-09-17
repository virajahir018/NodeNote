# Node.js Notes

## 1. What is Node.js?

### English

Node.js is a **JavaScript runtime environment** that allows us to run JavaScript outside the browser, mainly on the server side.

### Hindi

Node.js ek **JavaScript runtime environment** hai, jiske through hum JavaScript ko browser ke bahar, server par run kar sakte hain.

---

## 2. Why use Node.js?

### English

Node.js is used to build **fast and scalable backend applications and APIs**.

### Key Reasons to Use Node.js

#### 1. JavaScript on the Server

Node.js allows us to use JavaScript for **backend development**.

#### 2. Asynchronous and Non-blocking

Node.js can handle **I/O operations** without making the main JavaScript execution wait for each operation.

#### 3. Good for APIs

Node.js with **Express.js** makes it easy to create **REST APIs**.

#### 4. Scalable

Its **event-driven architecture** is suitable for applications that handle many concurrent I/O requests.

#### 5. Same Language for Frontend and Backend

We can use **JavaScript/TypeScript** for both the frontend and backend.

For example:

* React → Frontend
* Node.js → Backend

#### 6. Large npm Ecosystem

npm provides a huge number of packages for:

* Authentication
* Databases
* Validation
* File uploads
* API development
* And many other features

### Hindi

Node.js ka use mainly **fast aur scalable backend applications aur APIs** banane ke liye hota hai.

---

## 3. Node.js vs Browser JavaScript

### English

**Browser JavaScript** is mainly used to create interactive **frontend applications**.

**Node.js** allows JavaScript to run **outside the browser** and is mainly used for:

* Backend development
* APIs
* Server-side applications

### Simple Difference

| Browser JavaScript       | Node.js                   |
| ------------------------ | ------------------------- |
| Runs in the browser      | Runs outside the browser  |
| Mainly used for frontend | Mainly used for backend   |
| Works with DOM           | Does not have browser DOM |
| Used for UI interactions | Used for servers and APIs |
| Uses browser APIs        | Uses Node.js APIs         |

---

## 4. Node.js Installation & npm

### English

Node.js is installed from the **official Node.js website**.

When Node.js is installed, **npm (Node Package Manager)** is also installed automatically.

npm is used to:

* Install packages
* Manage dependencies
* Update packages
* Remove packages
* Run project scripts

### Check Node.js Version

```bash
node -v
```

### Check npm Version

```bash
npm -v
```

### Hindi

Node.js ko install karne ke liye official Node.js website se Node.js download aur install karte hain.

Node.js ke saath **npm automatically install** ho jata hai.

npm ka use packages aur dependencies ko install aur manage karne ke liye hota hai.

---

## 5. package.json

### English

`package.json` is a **configuration file** of a Node.js project.

It contains important information about the project, such as:

* Project name
* Version
* Scripts
* Dependencies
* Project configuration

### Example

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^5.0.0",
    "mongoose": "^8.0.0"
  }
}
```

### Hindi

`package.json` Node.js project ki ek **configuration file** hoti hai.

Isme project ki important information store hoti hai, jaise:

* Project ka name
* Version
* Scripts
* Dependencies
* Project configuration

---

## 6. Modules

### English

A **module** is a separate file or piece of code that contains specific functionality.

Modules help us to:

* Organize code
* Reuse code
* Maintain code easily
* Keep the project structured

For example, instead of writing everything in `server.js`, we can create separate files:

```text
project/
│
├── server.js
├── user.js
└── product.js
```

Then, we can export functionality from one file and import or require it into another file.

### Hindi

Module code ka ek **reusable part** hota hai jo usually separate file me rakha jata hai.

Isse:

* Code organize hota hai
* Code reuse kar sakte hain
* Code maintain karna easy hota hai
* Project ka structure clean rehta hai

---

## 7. CommonJS (CJS)

### English

**CommonJS (CJS)** is a module system used in Node.js to import and export code between files.

CommonJS mainly uses:

* `require()` → to import a module
* `module.exports` → to export a module

### Example

**user.js**

```js
const name = "Viraj Ahir";

module.exports = name;
```

**server.js**

```js
const name = require("./user");

console.log(name);
```

### Hindi

**CommonJS (CJS)** Node.js ka ek module system hai, jiska use ek file ke code ko doosri file me **export aur import** karne ke liye kiya jata hai.

CommonJS me mainly:

* `require()` → module ko import karne ke liye
* `module.exports` → module ko export karne ke liye

---

## 8. ESM (ECMAScript Modules)

### English

**ESM (ECMAScript Modules)** is the modern JavaScript module system used to import and export code between files.

ESM mainly uses:

* `export` → to export code
* `import` → to import code

### Example

**user.js**

```js
export const name = "Viraj Ahir";
```

**server.js**

```js
import { name } from "./user.js";

console.log(name);
```

### Hindi

**ESM (ECMAScript Modules)** JavaScript ka modern module system hai, jiska use ek file ke code ko doosri file me **export aur import** karne ke liye kiya jata hai.

ESM me mainly:

* `export` → code export karne ke liye
* `import` → code import karne ke liye

---

## 9. Built-in Modules

### English

**Built-in modules** are modules that are already provided by Node.js.

We do not need to install them using npm.

Some commonly used built-in modules are:

| Module   | Use                                |
| -------- | ---------------------------------- |
| `fs`     | File System                        |
| `http`   | Create HTTP servers                |
| `path`   | Work with file and directory paths |
| `os`     | Get operating system information   |
| `url`    | Work with URLs                     |
| `events` | Create and handle events           |

### Example

Using the `fs` module:

```js
const fs = require("fs");

fs.writeFileSync("hello.txt", "Hello Node.js");
```

### Hindi

**Built-in modules** wo modules hain jo Node.js ke saath already available hote hain.

Inhe use karne ke liye normally `npm install` karne ki zarurat nahi hoti.

Common built-in modules:

* `fs` → File System ke liye
* `http` → HTTP server banane ke liye
* `path` → File aur directory paths ke saath kaam karne ke liye
* `os` → Operating system ki information ke liye
* `url` → URLs ke saath kaam karne ke liye
* `events` → Events create aur handle karne ke liye

---

# Quick Revision

| Topic            | Short Answer                                   |
| ---------------- | ---------------------------------------------- |
| Node.js          | JavaScript runtime environment                 |
| Why Node.js?     | Fast and scalable backend applications ke liye |
| Browser JS       | Mainly frontend development                    |
| npm              | Packages aur dependencies manage karne ke liye |
| package.json     | Project ki configuration file                  |
| Module           | Reusable piece of code                         |
| CommonJS         | `require()` and `module.exports`               |
| ESM              | `import` and `export`                          |
| Built-in Modules | Node.js ke saath already available modules     |

---

# Interview Quick Answers

### What is Node.js?

> Node.js is a JavaScript runtime environment that allows us to run JavaScript outside the browser, mainly on the server side.

### Why do we use Node.js?

> Node.js is used to build fast, scalable backend applications and APIs.

### What is npm?

> npm is the Node Package Manager used to install and manage packages and dependencies in a Node.js project.

### What is package.json?

> package.json is a configuration file that contains information about a Node.js project, including scripts, dependencies, name, and version.

### What is a module?

> A module is a reusable piece of code that helps us organize and maintain our application.

### What is CommonJS?

> CommonJS is a Node.js module system that uses `require()` for importing and `module.exports` for exporting.

### What is ESM?

> ESM is the modern JavaScript module system that uses `import` and `export`.

### What are built-in modules?

> Built-in modules are modules provided by Node.js that can be used without installing them through npm.
