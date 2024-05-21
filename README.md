# node-express-typescript-mongoose-backend setup

## Getting Started

### 1. Initialize a New Node.js Project

<pre><code>npm init
</code></pre>
This command initializes a new Node.js project and creates a package.json file, which keeps track of your project's metadata and dependencies. You'll be prompted to enter various details like the project name, version, description, entry point, etc.

### 2. Install Express
 
<pre><code>npm install express --save</code></pre>
This command installs Express, a fast, unopinionated, minimalist web framework for Node.js. The --save flag adds Express to the dependencies section of your package.json, indicating that it's required for your project to run.

### 3. Install TypeScript as a Development Dependency

<pre><code>npm install typescript --save-dev
</code></pre>
This installs TypeScript, a strongly typed programming language that builds on JavaScript, as a development dependency. The --save-dev flag adds TypeScript to the devDependencies section of your package.json, indicating that it's only needed during development.

### 4. Install Mongoose

<pre><code>npm install mongoose --save
</code></pre>
Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js. This command installs Mongoose and adds it to your project's dependencies.

### 5. Install CORS

<pre><code>npm i cors
</code></pre>
CORS (Cross-Origin Resource Sharing) is a node.js package for providing a Connect/Express middleware that can be used to enable CORS with various options.

### 6. Install dotenv

<pre><code>npm install dotenv --save
</code></pre>
dotenv is a module that loads environment variables from a .env file into process.env. This makes it easier to manage environment variables for your project.

### 7. Create src Folder and Files

<pre><code>project-root
├── src
│   ├── app.ts
│   └── server.ts
└── package.json
</code></pre>
Create a src directory in your project's root, and inside it, create two files: app.ts and server.ts. The structure should look like this:

### 8. Initialize TypeScript Configuration

<pre><code>tsc --init
</code></pre>
This command generates a tsconfig.json file, which is used to configure TypeScript options for your project. This file includes various compiler options that you can adjust according to your needs.

### 9. Install Node Type Definitions

<pre><code>npm i --save-dev @types/node
</code></pre>
This installs type definitions for Node.js, allowing TypeScript to understand the types used in Node.js.

### 10. Install Express Type Definitions

<pre><code>npm i --save-dev @types/express
</code></pre>
This installs type definitions for Express, enabling TypeScript to provide type checking and autocompletion for Express.

### 11. Compile TypeScript to JavaScript

<pre><code>tsc
</code></pre>
Running this command compiles your TypeScript files in the src directory to JavaScript according to the configurations specified in tsconfig.json.

### 12. Install ts-node-dev for Development

<pre><code>npm i ts-node-dev --save-dev
</code></pre>
ts-node-dev is a development tool that restarts the node process when a file is modified. The --save-dev flag ensures it's installed as a development dependency.

### OR (Optional) Install ts-node-dev Globally

<pre><code>npm i -g ts-node-dev
</code></pre>
If you encounter issues running ts-node-dev locally, you can install it globally using this command.

### 13. Add Development Script to package.json

<pre><code>"scripts": {
  "start:dev": "ts-node-dev --respawn --transpile-only ./src/app.ts"
}
</code></pre>
This script allows you to start your development server using npm run start:dev, which will use ts-node-dev to watch for file changes and restart the server automatically.

### 14. Final Check
Run the development server with:

<pre><code>npm run start:dev
</code></pre>


# besic mongoose setup in server.ts and env config setup

## Getting Started

<pre><code>project-root
├── src
│   ├── app.ts
│   └── server.ts
    |--config
         |--index.ts 
└── package.json
</code></pre>

### conig index.ts file 
<pre><code>
</code>import dotenv from 'dotenv';
dotenv.config();

export default {
    port:process.env.PORT,
    db_url:process.env.DATABASE_URL,
}</code></pre>

### .env file

<pre><code>PORT=5000

DATABASE_URL=mongodb+srv://<dbName>:<password>@cluster0.8ldebrq.mongodb.net/first-project?retryWrites=true&w=majority&appName=Cluster0</code></pre>

### server.ts file besic setup 
<pre>// getting-started.js
import mongoose from "mongoose";
import app from "./app";
import config from "./config";

async function main() {
  try {
    await mongoose.connect(config.db_url as string);

    app.listen(config.port, () => {
      console.log(`Example app listening on port ${config.port}`);
    });
  } catch (err) {
    console.log(err);
  }
}

main();

</code></pre>

### app.ts besic setup 

<pre><code>import express, { Request, Response } from "express";
const app = express();

app.get("/", (req: Request, res: Response) => {
  res.send("Welcome hello world my");
});



export default app;
</code></pre>





