# Node.js Study Guide

## Introduction to Node.js

Node.js is a server-side JavaScript runtime environment based on Google Chrome’s V8 engine. Its asynchronous and event-driven design makes it highly efficient for real-time applications and scalable systems. Unlike other execution environments, Node.js allows developers to run JavaScript code on the server rather than just in the browser.

### 1. Key Features of Node.js

| Feature | Description |
|---------------|-------------|
| **Asynchronous and Non-Blocking** | All Node.js APIs are asynchronous, meaning the server does not wait for responses before proceeding. |
| **Fast Execution** | Built on the V8 engine, which executes JavaScript code quickly. |
| **Single-Threaded but Scalable** | Uses an event-driven, single-threaded model that efficiently handles multiple connections. |
| **No Buffering** | Data is processed in chunks rather than buffered. |
| **JavaScript-Based** | Uses JavaScript, allowing full-stack development with a single language. |

## Express.js Framework

Express.js is a minimal and flexible Node.js web framework that provides a robust set of features for web and mobile applications.

### 2.1. Key Features of Express.js

| Feature | Description |
|---------------|-------------|
| **Routing** | Provides a powerful routing mechanism for handling HTTP requests. |
| **Middleware Support** | Allows adding middleware functions to process requests. |
| **Template Engine Support** | Supports template engines like EJS, Pug, and Handlebars. |
| **Error Handling** | Comes with built-in error-handling middleware. |
| **Lightweight and Fast** | Minimalistic framework designed for performance. |
| **REST API Support** | Facilitates creating RESTful APIs easily. |

### 2.2. Middleware in Express.js

Middleware functions are functions that have access to the request (`req`), response (`res`), and the next function in the application's request-response cycle.

#### Example of Middleware
```js
const express = require('express');
const app = express();

// Simple middleware function
app.use((req, res, next) => {
  console.log('Middleware executed');
  next();
});

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

### 2.3. Types of Middleware

| Middleware Type | Description |
|---------------|-------------|
| **Application-Level** | Middleware functions bound to an instance of `app`. |
| **Router-Level** | Middleware bound to an instance of `express.Router()`. |
| **Error-Handling** | Used for handling errors in Express applications. |
| **Built-In Middleware** | Express has built-in middleware like `express.json()`, `express.urlencoded()`. |
| **Third-Party Middleware** | Middleware provided by third-party libraries like `cors`, `helmet`. |

### 2.4. Middleware Chaining

Middleware functions are executed in the order they are added.

#### Example:
```js
app.use((req, res, next) => {
  console.log('First Middleware');
  next();
});

app.use((req, res, next) => {
  console.log('Second Middleware');
  next();
});

app.get('/', (req, res) => {
  res.send('Hello from Express!');
});
```

### 2.5. Express Routing

Express allows handling different HTTP methods such as GET, POST, PUT, DELETE.

#### Example:
```js
app.get('/users', (req, res) => {
  res.send('GET request to fetch users');
});

app.post('/users', (req, res) => {
  res.send('POST request to create a user');
});
```

### 2.6. Enabling CORS in Express.js

Cross-Origin Resource Sharing (CORS) allows API access from different origins.

```js
const cors = require('cors');
app.use(cors());
```

## NestJS Framework

NestJS is a progressive Node.js framework for building scalable server-side applications using TypeScript and JavaScript.

### 3.1. Key Features of NestJS

| Feature | Description |
|---------------|-------------|
| **Modular Architecture** | Encourages modularity by structuring applications with modules. |
| **Dependency Injection** | Uses dependency injection for managing dependencies effectively. |
| **TypeScript Support** | Built with TypeScript but also supports JavaScript. |
| **Middleware and Guards** | Provides middleware and guards for request handling and authorization. |
| **GraphQL Support** | Supports GraphQL APIs alongside REST APIs. |
| **CLI Support** | Provides a powerful CLI tool for scaffolding applications. |

### 3.2. Creating a NestJS Application

#### Install the NestJS CLI:
```sh
npm i -g @nestjs/cli
```

#### Create a new NestJS project:
```sh
nest new my-app
```

### 3.3. Modules in NestJS

A module in NestJS is a class decorated with `@Module()` that organizes the application.

#### Example:
```ts
import { Module } from '@nestjs/common';
@Module({})
export class AppModule {}
```

### 3.4. Controllers in NestJS

Controllers handle incoming requests and return responses.

#### Example:
```ts
import { Controller, Get } from '@nestjs/common';
@Controller('users')
export class UsersController {
  @Get()
  getUsers() {
    return ['User1', 'User2'];
  }
}
```

### 3.5. Services in NestJS

Services handle business logic and are injected into controllers.

#### Example:
```ts
import { Injectable } from '@nestjs/common';
@Injectable()
export class UsersService {
  getUsers() {
    return ['User1', 'User2'];
  }
}
```

