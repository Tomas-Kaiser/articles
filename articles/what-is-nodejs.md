# What Is Node JS

Node JS or just Node is an open-source and cross-platform runtime environment for executing JavaScript code outside of a browser. We usually use Node to build backend services also known as API's **A**pplication **P**rogramming **I**nterfaces. 

Node is ideal for building highly scalable, data-intensive and real-time backend services that power client applications.

## Node Architecture

We have touched that the node is a runtime environment for executing JavaScript code but what is it really about?

We used JavaScript to build applications that run inside of a browser before Node. It means that every browser out there has a JavaScript Engine. JS Engine takes the JavaScript code and converts it into machine code that the computer can understand.

JS engine for browsers:
- Microsoft Edge - Used to use Chakra but they have migrated into v8 JavaScript engine
- Firefox - SpiderMonkey 
- Chrome - v8

A browser provides a runtime environment for JavaScript code such as `Window` or `document` objects. As you probably know we can use a document object and call a getElementById method `document.getElementById("");`. These objects allow us to work with an environment in which a code is running.

Until 2009, we were able to execute JavaScript code only inside of browsers. In 2009, Ryan Dahl came up with a brilliant idea. He thought it would be great to execute JavaScript outside of a browser. Basically, he took the fastest JS engine v8 from Chrome and embedded it into a C++ programe and called that program Node.exe. That means, similar to a browser the Node is a runtime environment to execute a JavaScript code. It contains a JS engine that executes JavaScript code but it also has certain objects that provide an environment for JavaScript code. These objects are different from the environment objects we have in browsers. For example, we do not have `document` object. Instead, we have other objects such as

- `fs.readFiles()` for working with the files system
- `http.createServer()` for listening to requests in a given port

To sum up, the Node is a program that includes a JS engine plus some additional modules that give us capabilities, not available inside browsers. Both Chrome browser and Node share the same JS engine but they provide different runtime environments for JavaScript. Saying that Node is neither not a programming language nor a framework. It is a purely runtime environment where we can run a JavasCript code.

Happy Coding!