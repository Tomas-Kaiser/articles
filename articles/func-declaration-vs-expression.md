# Function Declaration X Expression in JavaScript

It is fairly common to be asked to explain a difference between a function declaration and a function expression during a job interview. 

If you are not entirely sure how would you tackle this question, let's dive in.

## Function Declaration

The function declaration is the simpliest way how to delcare a function.

```javascript
function sayHello() {
    console.log("Hello...")
}

sayHello();
```

## Function Expression
The other way to declare a function is called function expression. The only difference is that the function expression is stored in a variable.

```javascript
const greet = function sayHello() {
    console.log("Hello...")
};

greet();
```

Is it the only difference? Nope, a JavaScript hoisting comes into play. The key difference between those two functions is that we can call the function declaration before it is defined such as:

```javascript
// we call it before we define the function declartion
sayHello();

function sayHello() {
    console.log("Hello...")
}
```

We cannot do the same with function expression. If we try to do that, we will get a following error `Uncaught ReferenceError: greet is not defined at index.js:2` 

```javascript
// we call it before we define the function expression
greet(); // This will throw the Error

const greet = function sayHello() {
    console.log("Hello...")
};
```

It is like using a variable or a constant before it is defined.
```javascript
// We try to display\log variable "x" before it is initialized, therefore it will throw the Error
console.log(x)
const x = 1;
```

As you can see, we can call a function that is defined using the function declaration syntax but not the function expression. The reason is, when a JavaScript engine executes this code, it moves all function declarations to the top of the file. It means that the code will look like this at runtime:

```javascript
// As we define
sayHello(); 

function sayHello() {
    console.log("Hello...")
};

// What JavaScript engine will execute at runtime
function sayHello() {
    console.log("Hello...")
};

sayHello(); 
```

This is called a `hoisting`. The `hoisting` is a process of moving all function declarations to the top of the file. This is done autmatically by the JavaScript engine that is executing this code. That is the reason, why we can call the functions that are defined using the function declaration syntax before their definition.  

Happy coding!