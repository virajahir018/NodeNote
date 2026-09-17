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