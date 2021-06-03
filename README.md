## Techniques Used 

- Using VSCode to commit files to github 
- Creating a .gitignore file
- Non-web server Node.js JavaScript code
    - Lambda expressions
    - Tenary operater
    - if...else statments
    - template literals
- Web server Node.js JavaScript code
  - Installing fastify
  - Initializing as a node.js file
  - Using http "GET" verb
  - Utilizing the html MIME type
  - Returning a status code
  - Responding to client requests and handling query parameters

## Objectives

### Initalize the folder as a node.js project and update server code to the proper MIME type. Adjust routes to respond to query parameters from the client or a lack thereof.

```
// Require the Fastify framework and instantiate it
const fastify = require("fastify")();
// Handle GET verb for / route using Fastify
// Note use of "chain" dot notation syntax
fastify.get("/", (request, reply) => {
  reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send("<h1>Hello from Lab 4!</h1>");
});

//new route
fastify.get("/name", (request, reply) => {
    // get request info
    const {first, last} = request.query;
    //process request info
    const name = first && last ? `${first} ${last}` : `Guest`
    reply
      .code(200)
      .header("Content-Type", "text/html; charset=utf-8")
      .send(`<h1>Hello, ${name}</h1>`);
  });
// Start server and listen to requests using Fastify
const listenIP = "localhost";
const listenPort = 8080;
fastify.listen(listenPort, listenIP, (err, address) => {
  if (err) {
    console.log(err);
    process.exit(1);
  }
  console.log(`Server listening on ${address}`);
});

```

Node.js configuration file:

[package.json](https://lizz02.github.io/cit281-lab03/package.json)
