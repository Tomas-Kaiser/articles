# Three Ways to Create an Object in Javascript

Did you know that, there are three fundamental ways to create an object in JS? 

We can use one of the below approaches:

- Object literal syntax
- Factory function
- Constructor function

Let's dive in.

## Object Literal Syntax

We will start by looking into Object literal syntax that is the most straight-forward way to create an object in JS. See the example below:

```javascript
const car = {
    // key/value pair also known as property of the object
    brand: "Skoda",
    color: "red",
    isEngineOn: false,
    price: 5000,

    // Function known as a method when the function is inside of the object
    honk: function() {
        console.log("Honk honk...")
    }
}
```

This approach is totally fine if we work on a very simple application. Nevertheless, we usually work on more complex applications. Therefore, we need a different (maintainable) way to create objects.

## Factory Function

The object literal syntax has a tiny problem. Imagine that we want to create two or more cars. With that approach, we would have to duplicate the code  with the honk method implementation. What if we discover a bug in that implementation? In that case we would need to go over all objects again and fix the bug. Wouldn't it be better if we could fix the bug in one place only? I bet your answer is yes. Then, we can use Factory Function for creating objects. It is like a factory in a real world where the factory produces products. This Factory Function produces objects. Let's look at the code below:

```javascript
// Define a function with 4 parameters so that we can create a different objects with the same method called honk
function createCar(brand, color, isEngineOne, price) {
   // We are returning an object
   return {
    // In the mondern JS if the key & value is the same, then we can omit the value
    // eg. brand: brand to be just brand. It makes our code shorter & more readable.
    brand,
    color,
    isEngineOn,
    price,

    // Same for function, we can make it shorter omitting the "function" keyword and the colon as such:
    honk() {
        console.log("Honk honk...")
    }
   }
}

const car1 = createCar("BMW", "Blue", false, 1000);
const car2 = createCar("Tesla", "Red", true, 1000);
```

The beauty of this code is that if we discover a bug in the implementation of the honk method, we can fix the problem in one place.

## Constructor Function

The Constructor Function is another way how to create/construct an object. It is very similar to the Factory Function, just the syntax different. Which way you go is really up to your personal preferences. Both ways are equally good. 

```javascript
function Car(brand, color, isEngineOne, price) {
    this.brand = brand,
    this.color = color,
    this.isEngineOne = isEngineOne,
    this.price = price
    this.honk = function() {
        console.log("Honk honk...")
    }
}

// We use a "new" operator to create objects
const car1 = new Car("BMW", "Blue", false, 1000);
const car2 = new Car("Tesla", "Red", true, 1000);
```

We use Pascal naming convention for Constructor Function by convention of other javascript developers whereas we use camel notation for factory function. The pascal notation starts with an upper case letter, such as `CreateFunction` or `Car` (see the example above). In contrast, the camel notation starts with a lower case letter such as `createFunction`.

Whenever we use a `new` operator, three things happen:

1. This `new` operator creates an empty javascript object like `const car1 = {}`. That is happening under the hood.
2. The keyword `this` points to the new empty object. The `this` will set the properties such as brand, colour etc. to the new javascript object. 
3. The `new` operator returns the new car object from the `function Car`. We could put `return this` statement into the Car function but this is done under the hood as well. So, we do not have to explicitly mention it there.

You might have a question on what approach is better. Developers who know Java or any other OOP language are more familiar with the Constructor Function, but if you are not one of them, then you might want to use Factory Function. More or less, it comes down to your personal choice, but make sure to stick with one approach in your entire app.

Happy coding!