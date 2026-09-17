# 1. What is Node.js ?

English :
- Node.js is a JavaScript runtime environment that allows us to run JavaScript outside the browser, mainly on the server side.

Hindi :
- Node.js ek JavaScript runtime environment hai, jiske through hum JavaScript ko browser ke bahar, server par run kar sakte hain.

# 2. Why use Node.js ?

English :
- Node.js is used to build fast and scalable backend applications and APIs.

JavaScript on the server
- Node.js allows us to use JavaScript for backend development.
Asynchronous and non-blocking
- Node.js can handle I/O operations without making the main JavaScript execution wait for each operation.
Good for APIs
- Node.js + Express makes it easy to create REST APIs.
Scalable
- Its event-driven architecture is suitable for applications that handle many concurrent I/O requests.
Same language for frontend and backend
- You can use JavaScript/TypeScript on both React frontend and Node.js backend.
Large npm ecosystem
- npm provides a huge number of packages for authentication, databases, validation, file uploads, etc.

Hindi :
- Node.js ka use mainly fast aur scalable backend applications aur APIs banane ke liye hota hai.

# 3. Node.js vs Browser JavaScript ?

- Browser JavaScript is mainly used to create interactive frontend applications, 
- while Node.js allows JavaScript to run outside the browser and is mainly used for backend development, 
- APIs, and server-side applications.

# 4. Node.js Installation & npm

- Node.js is installed from the official Node.js website, and npm (Node Package Manager) is installed automatically with Node.js. 
- npm is used to install and manage packages or dependencies in a Node.js project.

# 5. package.json ?

English :

- package.json is a configuration file of a Node.js project. 
- It contains important information about the project, 
- such as the project name, version, scripts, and installed dependencies.

Example:

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

Hindi :

- package.json Node.js project ki ek configuration file hoti hai. 
- Isme project ki important information store hoti hai, jaise project ka name, version, scripts aur dependencies.

6. Modules
English

A module is a separate file or piece of code that contains specific functionality. Modules help us organize, reuse, and maintain code easily.

For example, instead of writing everything in server.js, we can create separate files like:

project/
├── server.js
├── user.js
└── product.js

Then we can export functionality from one file and import/require it into another.

Hindi:

Module code ka ek reusable part hota hai jo usually separate file me rakha jata hai, jisse code ko organize, reuse aur maintain karna easy hota hai.


======================================

# Node.js Basics

A beginner-friendly documentation covering the basic concepts of Node.js, npm, package.json, and modules.

---

## 1. What is Node.js?

### English

Node.js is a **JavaScript runtime environment** that allows us to run JavaScript outside the browser, mainly on the server side.

### Hindi

Node.js ek **JavaScript runtime environment** hai, jiske through hum JavaScript ko browser ke bahar, mainly server par run kar sakte hain.

---

## 2. Why Use Node.js?

### English

Node.js is used to build **fast, scalable backend applications and APIs**.

### 1. JavaScript on the Server

Node.js allows us to use JavaScript for **backend development**.

### 2. Asynchronous and Non-Blocking

Node.js can handle I/O operations without making the main JavaScript execution wait for each operation.

### 3. Good for APIs

Node.js with Express makes it easy to create **REST APIs**.

### 4. Scalable

Node.js uses an **event-driven architecture**, which is suitable for applications that handle many concurrent I/O requests.

### 5. Same Language for Frontend and Backend

We can use **JavaScript or TypeScript** for both the frontend and backend.

For example:

* React → Frontend
* Node.js + Express → Backend

### 6. Large npm Ecosystem

npm provides a huge number of packages for:

* Authentication
* Database integration
* Validation
* File uploads
* API development
* Security
* And many more features

### Hindi

Node.js ka use mainly **fast aur scalable backend applications aur APIs** banane ke liye hota hai.

Iske main benefits:

* JavaScript ko backend par use kar sakte hain.
* Asynchronous aur non-blocking operations support karta hai.
* REST APIs banana easy hota hai.
* Scalable applications ke liye useful hai.
* Frontend aur backend dono me JavaScript/TypeScript use kar sakte hain.
* npm ke through bahut saare packages available hain.

---

## 3. Node.js vs Browser JavaScript

| Browser JavaScript                                 | Node.js                                         |
| -------------------------------------------------- | ----------------------------------------------- |
| Mainly frontend development ke liye use hota hai   | Mainly backend development ke liye use hota hai |
| Browser ke andar run hota hai                      | Browser ke bahar run hota hai                   |
| DOM ke saath kaam kar sakta hai                    | Server-side operations ke liye use hota hai     |
| User interface aur interactions ke liye useful hai | APIs aur server applications ke liye useful hai |
| Browser APIs available hoti hain                   | Node.js APIs aur modules available hote hain    |

### English

Browser JavaScript is mainly used to create **interactive frontend applications**, while Node.js allows JavaScript to run **outside the browser** and is mainly used for backend development, APIs, and server-side applications.

### Hindi

Browser JavaScript ka use mainly **frontend aur user interactions** ke liye hota hai, jabki Node.js JavaScript ko **browser ke bahar**, mainly backend aur server-side applications ke liye run karta hai.

---

## 4. Node.js Installation & npm

### English

Node.js can be installed from the **official Node.js website**.

When Node.js is installed, **npm (Node Package Manager)** is also installed automatically.

npm is used to:

* Install packages
* Manage dependencies
* Update packages
* Remove packages
* Run project scripts

### Example

```bash
npm install express
```

This command installs the Express package in the Node.js project.

### Hindi

Node.js ko official Node.js website se install kiya ja sakta hai.

Node.js ke saath **npm (Node Package Manager)** automatically install ho jata hai.

npm ka use:

* Packages install karne ke liye
* Dependencies manage karne ke liye
* Packages update karne ke liye
* Packages remove karne ke liye
* Project scripts run karne ke liye

Example:

```bash
npm install express
```

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

### Important Commands

Create `package.json`:

```bash
npm init
```

Default values ke saath `package.json` create karne ke liye:

```bash
npm init -y
```

Package install karne ke liye:

```bash
npm install express
```

---

## 6. Modules

### English

A **module** is a separate file or reusable piece of code that contains specific functionality.

Modules help us:

* Organize code
* Reuse code
* Maintain code easily
* Keep files clean
* Separate different functionalities

Instead of writing everything inside `server.js`, we can create separate files.

### Example Project Structure

```text
project/
│
├── server.js
├── user.js
└── product.js
```

For example:

* `server.js` → Server-related code
* `user.js` → User-related functionality
* `product.js` → Product-related functionality

We can **export** functionality from one file and **import/require** it into another file.

### Example

#### user.js

```js
const user = {
    name: "Viraj Ahir",
    email: "viraj@example.com"
};

module.exports = user;
```

#### server.js

```js
const user = require("./user");

console.log(user);
```

### Hindi

Module code ka ek **reusable part** hota hai jo usually separate file me rakha jata hai.

Modules ki help se hum:

* Code ko organize kar sakte hain.
* Code ko reuse kar sakte hain.
* Code ko easily maintain kar sakte hain.
* Different functionalities ko separate files me rakh sakte hain.

Example:

```text
project/
│
├── server.js
├── user.js
└── product.js
```

Ek file se functionality ko `export` karke doosri file me `require` ya `import` kiya ja sakta hai.

---

# Quick Interview Revision

### What is Node.js?

**English:**
Node.js is a JavaScript runtime environment that allows us to run JavaScript outside the browser, mainly on the server side.

**Hindi:**
Node.js ek JavaScript runtime environment hai jo JavaScript ko browser ke bahar, mainly server par run karne deta hai.

### Why use Node.js?

**English:**
Node.js is used to build fast, scalable backend applications and APIs.

**Hindi:**
Node.js ka use fast aur scalable backend applications aur APIs banane ke liye hota hai.

### What is npm?

**English:**
npm stands for Node Package Manager. It is used to install and manage packages and dependencies in Node.js projects.

**Hindi:**
npm ka full form Node Package Manager hai. Iska use Node.js project me packages aur dependencies ko install aur manage karne ke liye hota hai.

### What is package.json?

**English:**
`package.json` is a configuration file that contains information about a Node.js project, including scripts and dependencies.

**Hindi:**
`package.json` Node.js project ki configuration file hoti hai jisme project ki information, scripts aur dependencies hoti hain.

### What is a Module?

**English:**
A module is a reusable piece of code that is usually kept in a separate file.

**Hindi:**
Module code ka reusable part hota hai jo usually separate file me rakha jata hai.

---

# Conclusion

Node.js provides a powerful environment for building **backend applications, REST APIs, and server-side applications** using JavaScript.

The basic concepts covered in this documentation are:

1. What is Node.js?
2. Why use Node.js?
3. Node.js vs Browser JavaScript
4. Node.js Installation & npm
5. package.json
6. Modules
