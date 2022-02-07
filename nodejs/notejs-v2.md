
# NodeJS V2

## Node.js is JavaScript

- Node.js is a runtime for built on top of Chrome's V8. It allows you to develop apps in JavaScript outside of the browser. It's single threaded non blocking and asynchronous. This is acheived by the use of an event loop at the core of Node.js. If you know JS then you already know how to develop with Node.js


Use cases
Because Node.js can run outside of the browser, it can be used for pretty much anything!

API's and servers
Databases (yes some DB's are built in Node)
CLI's
Build Tools
Automations
Basic Scripting
GPU shopping bots 
## Use Case

Because Node.js can run outside of the browser, it can be used for pretty much anything!

-   API's and servers
-   Databases (yes some DB's are built in Node)
-   CLI's
-   Build Tools
-   Automations
-   Basic Scripting
-   GPU shopping bots 
## Installing Node.js via package manager

there are many ways to install nodejs
- windows you can download the package at the following link

    link [download](https://nodejs.org/en/download/)

- macOs
    
    `brew install node`

- linux

    `sudo apt install nodejs`

For others, you can check the following link [tutorial](https://nodejs.org/en/download/package-manager/)
## Running nodeJS

### Node REPL

  Before we get into creating programs and apps with Node.js, let's get a feet wet with the Node.js REPL. Just type node in your terminal. This will create a Node.js environment where we can write and execute JavaScript. You'll see that all that JS knowledge you have learned carries over to Node.js! 💯. Although, some things, specifically browser based API's probably won't work. Go ahead, try an alert('hello world') and see what happens. You'll get an error. Although the Node.js runtime uses JS as it's languge, none of the Browser based globals that you are familiar with actually exist in Node.js or they are pollyfilled to prevent runtime errors.

### File Execution
The Node REPL it nice, but you can't build an application with that. We need to be able write our code to a file and tell Node.js to execute that.

    Create a file called: `index.js`

In that file, write some JS. Try out console.log('hello there'). To execute this .js file in the Node.js runtime, we can use the node command with the file name as an argument.

`> node index.js`
## Globals

Like the Browser, Node.js comes with some practical globals for us to use in our applications.

### Common

`global` Think of this as like `window` but for Node.js. DON'T ABUSE IT!

`__dirname` This global is a `String` value that points the the directory name of the file it's used in.

`__filename` Like `__dirname`, it too is relative to the file it's written in. A `String` value that points the the file name.

`process` A swiss army knife global. An `Object` that contains all the context you need about the current program being executed. Things from env vars, to what machine you're on.

`exports` `module` `require` These globals are used for creating and exposing modules throughout your app. We'll get to modules in a second 🌈

### The rest
Depending on what version on Node.js you're running, there are so many more globals. Not as many as the Browser, but enough that you'll probably never use many of them. Check them out [here](https://nodejs.org/api/globals.html).
## Modules

There is no GUI in Node.js, no HTML or CSS. This also means there aren't any scipt tags to include JS files into our application. Node.js uses modules to to share your JavaScript with other JavaScript in your apps. No window or globals needed. If you've ever done `window.App = window.App || {}` then you'll like this!

### What is a module
A module is a reusable chunk of code that has its own context. That way modules can't interfere with or polute the global scope.

You can think of them like lego blocks that you can create, import, and share.

### Two module types
By default, Node.js uses common js modules. With newer versions of Node.js we can now take advantage of ES6 modules. To opt into using this syntax, you can use the `.mjs` extension instead of `.js`. We'll be using the ES6 module syntax going forward as they are the standard now with browsers adding support now.

### Internal Modules
Node.js comes with some great internal modules. You can think of them as like the phenonminal global APIs in the browser. Here are some of the most useful ones:


`fs` - useful for interacting with the file system.

`path` - lib to assit with manipulating file paths and all their nuiances.

`child_process` - spawn subprocesses in the background.

`http` - interact with OS level networking. Useful for creating servers.

## File System

Until Node.js, there wasn't a great way to access the file system on a machine with JavaScript, this is due to secutrity restrictions in most browsers. With Node.js, one can create, edit, remote, read, stream, & more with files. If you've ever used a build tool like webpack or a parser like babel, then you realize just how powerful Node.js can be when manipulating the file system.
## Error Handling

The last thing you want is your entire server crashing because of an error, or, is that exactly what you want 🤷‍♀️? Regardless, you should have th choice. So you better handle those errors. Depending on the type of code (sync, promise, async callback, async await, etc) Node allows us to handle our errors how we see fit.

### Process exiting
When a exception is thrown in Node.js, the current process will exit with a code of `1`. This effectively errors out and stops your programing completely. You can manually do this with:

`process.exit(1)`

Although you shouldn't. This is low level and offers no chance to catch or handle an exception to decide on what to do. Imagine your entire API shutting down and restarting just because a user sent a malformed payload that resulting the DB throwing and exception. That would be terrible.

#### Async Errors
When dealing with callbacks that are used for async operations, the standard pattern is:

    fs.readFile(filePath, (error, result) => {
    if (error) {
        // do something
    } else {
        // yaaay
    }
    })
    
Callbacks accept the `(error, result)` argument signature where error could be `null` if there is no error.

For `promises`, you can continue to use the `.catch()` pattern. Nothing new to see here.

For `async / await` you should use `try / catch`.

    try {
    const result = await asyncAction()
    } catch (e) {
    // handle error
    }

#### Sync Errors
For sync errors, `try / catch` works just fine, just like with async await.

    try {
    const result = syncAction()
    } catch (e) {
    // handle error
    }

#### Catch All
Finally, if you just can't catch those pesky errors for any reason. Maybe some lib is throwing them and you can't catch them. You can use:

    process.on('uncaughtException', cb)
## Packages


The most beautiful part about Node.js is not the JavaScript, it's the thriving community. There are millions of node projects ready to be installed and consumed by your application. These projects are called packages. A package can have several modules and other packages. Node.js has built in support for these packages so you can take advantage of them at any time.

### NPM
#### Init
To consume a package, we must first turn our app into a package. We can do this with a simple file called `package.json` on the root of our app. Writing it by hand is cool, but using a CLI called `npm` is better. NPM was already installed when you installed Node.js. In a new folder, run: `npm init`

This will initialze a new package by walking you through a few prompts. Once you're finished, you'll have a `package.json` file that looks like this:

    {
    "name": "app",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "",
    "license": "ISC"
    }

Now are soon to be app is a package. We'll get into how to distribute and deploy different types of Node.js apps, but for now, this package is staying local. Let's take a look at some of these fields:

`"name"` - is the name of your package. Can be anything since we're local

`"version"` - is the [Semantic Version Number](https://semver.org/) or semver

`"main"` - the main entry point into your package

`"scripts"` - object of custom scripts to be excuted with npm cli

### Commands

NPM has [several commands](https://docs.npmjs.com/cli/v6/commands/) at its disposal that you don't need to know really. There are some important ones that you will use repeatedly.

`npm install` - installs given module(s) from remote registries or local sources

`npm test` - runs the test script in your package.json

`npm uninstall` - will uninstall a give package

No matter what company you're at or the app, you'll work with these three commands all the time. Unless you're one of the crazies that don't write tests 😘. The rest of the commands will be unique to your app.


[Finding and installing packages] (https://www.npmjs.com/)


## CLIs & Servers

A CLI, or command line interface is a program desgined to start and complete one off tasks. Like git or npm. Node.js is a perfect runtime to create a CLI that will run on any machine that has Node.js isntalled.

### Creating a CLI
Creating a CLI in Node.js just takes a extra step or two because they are really just an ordinary Node.js app wrapped behind a bin command. For this exercise, we'll create a CLI that opens a random reddit post in our browser. To start, we'll create a new folder and make it a package with npm init.

Once inside that folder, create a file reddit.mjs:

    // reddit.mjs
    #! /usr/bin/env node

console.log('hello from your CLI')
The fist line on that file is called a shabang or hashbang. It's needed to tell the machine where the interpreter is located that is needed to execute this file. For us, that will be Node.js.

Next we need to tell Node.js what the name of our CLI is so when can actually use it in our terminal. Just have to add a section to our package.json:

    "bin": {
    "reddit": "./reddit.mjs"
    }

Once installed, this package will have it's bin command installed into your machine's bin folder allowing us to use the reddit command.

Lastly, we must install our own package locally so we can test out the CLI. We could just execute the file with the node runtime, but we want to see the CLI actually work.

`npm install -g`

We can simply instll with no args which tells npm to install the current director. The `-g` flag means we want to globally install this package vs in a local node_modules.

You should now be able to run `reddit` and see your log print.

## Servers

Node.js has access to OS level functionality, like networking tools. This allows us to build very capable servers. Mixed with the fact that Node.js is single threaded and runs an even loop for async tasks, Node.js is widely used for API's that need to respond fast and don't require heavy CPU intensive work.