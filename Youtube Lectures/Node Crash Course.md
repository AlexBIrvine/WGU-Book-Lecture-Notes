---
Date: 2019/12/18
Length: 1:30:07
Source: https://www.youtube.com/watch?v=fBNz5xF-Kx4
---

## Intro (00:00)

Going to build a webserver with only Node (no express)  
Touches on core node modules  
Deploys to Heroku at end

---

## What is Node.js? (1:14)

Javascript runtime using the V8 language (same as chrome browser)
NOT A LANGUAGE

---

## What you should know first (2:00)

- JS Fundamentals
- HTTP
- JSON
- Arrow Functions
- Promises
- MVC Pattern

---

## Why use Node? (3:21)

It's fast, efficient & highly scalable.  
Event driven, non-blocking I/O model
Popular, especially in startups.

---

## Non-Blocking I/O (4:20)

Works on a single thread.  
Works asyncronously, can support many opperations.  
Supports tens of thousands concurrent connections.  
Don't use with CPU intensive apps.

---

## Node's event loop (5:30)

When an event is triggered, a callback is called.  
It won't wait for it to complete, the program will move on.

---

## Best types of projects for node (6:09)

REST API & Microservices.  
Real Time Services (Chat)  
CRUD Apps (Blogs, shopping cards, social networks)  
Really anything that's not CPU intensive.

---

## NPM - Node Package Manager (7:45)

Install 3rd party packages  
Stored in the "node_modules" folder  
All dependencies are listed in a "package.json" file

Common commands:

```js
npm init                //Generates a package.json file
npm install express     //Installs a package locally
npm install -g nodemon  //Installs a package globally
```

---

## Node Modules (9:15)

Has a bunch of core modules (path, fs, http, etc.,)  
3rd party modules are installed via NPM  
Custom modules are files you made

---

## "Let's jump in" (10:10)

Speaker does the following:

1. Downloads & installs Node.js
2. Shows off the REPL (read, evaluate, print loop)

---

## Real code in VS Code (12:30)

First step in most Node.js projects is to create a package.json file.  
Do this by running the command `npm init` and answering the questions it asks.  
package.json main purpose is to list all of the dependencies & allow for easy installation later.

The speaker then runs `npm install uuid` to demonstrate adding a dependency.  
Then he runs `npm install -D nodemon`. The **-D** adds it as a development only dependency.  
Lastly for this step, he creates a file `index.js` that will act as the landing spot of this app.

---

## index.js (16:16)

```js
```

(Stopped at 30:00, starting new things I don't know)
