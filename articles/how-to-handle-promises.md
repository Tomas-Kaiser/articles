Before we dive in, let's briefly explore what the promise actually is.

It is like in the real world where I promise you to teach you how to handle it. There are two outputs of my promise. Either I fulfil aka `resolved` or I fail aka `rejected` my promise. In the asynchronous code it promises you that it will return some data at some point of the future.

So now that we know the promise object returns one of the two possible outputs, let's look at the code.

First we need to create a promise object as below:
```javascript
// The new Promise() constructor returns a promise object.
const promiseObj = new Promise()
``` 

The `new Promise()` accepts a callback function as an argument such as: `new Promise(function (resolve, reject) { // ... })`

```javascript
// The callback function must have two arguments: resolve and reject that represent other built-in functions
const promiseObj = new Promise(function (resolve, reject) {
    // 50 % chance that this promise will return resolve
    if (getRandomNum() < 0.5)
        resolve("I taught you promise!")
    else
        reject("I did not teach you promise properly!")
})

// This func returns a random number between 0 - 1
function getRandomNum() {
    return Math.random()
}
```

Note: the else statement block is not necessary since the promise returns resolve or reject. We can simplify as such:

```javascript
    if (getRandomNum() < 0.5)
        resolve("I taught you promise!")
    reject("I did not teach you promise properly!")
```

We created the promiseObj, now we need to properly handle it. The old way (not necessarily a wrong one) is to use .then() and .catch() method. With new ES6 syntax, we can use async/await key words to work with promises.

**Older version**:
```javascript
// Handle promise with .then() if resolved or .catch() if rejected
promiseObj
    .then((msg) => console.log(msg))
    .catch((err) => console.error(err))
`````
It will either print out "I taught you promise!" in case the promise was resolved or "I did not teach you promise properly!" in case the promise was rejected.

**Using ES6 syntax**:
Whenever we use `await` keyword in the function, we need to annotate the function with `async` keyword.

```javascript
// Annotate function with async keyword
async function init() {
    // if promise returns reject then the catch block will catch it
    try {
       // The await keyword means that it will be waiting for the response from the promise and then it will store the response in the msg variable in case the promise is resolved.
        const msg = await promiseObj
        console.log(msg)
    } catch (error) {
        console.log(error)
    }
}

// Trigger the async function
init()
```

In summary, promises are used in asynchronous code and I tried to show you two ways how to handle them.
---
You can find complete code below. Feel free to copy/paste it to your index.js and play around with it. To run the code in your terminal, you can use a following command: `node index.js`

```javascript
// Promise accepts a callback with two arguments - resolve, reject
const promiseObj = new Promise(function (resolve, reject) {
    if (getRandomNum() < 0.5)
        resolve("I taught you promise!")
    reject("I did not teach you promise properly!")

})

// Handle promise with .then() if resolved or .catch() if rejected
promiseObj
    .then((msg) => console.log(msg))
    .catch((err) => console.error(err))


// New version using async/await    
async function init() {
    try {
        const msg = await promiseObj
        console.log(msg)

    } catch (error) {
        console.log(error)
    }
}

init()

// This func returns a random number between 0 - 1
function getRandomNum() {
    return Math.random()
}
```

Happy coding!