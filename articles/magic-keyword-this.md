# Magic Keyword This JavaScript

The keyword `this` references the object that is executing the current function. 

If we have a function inside of an object, we call it a method. In that case, the `this` references the object itself. Otherwise, if the function is a regular function which means it is not a part of an object, then `this` references the global object which is the `window` object in browser and `global` in node.

Let's look at a few examples.

Firstly, we will explore the method.
```JavaScript
const car = {
    brand: "Skoda",
    honk() {
        console.log(this);
    }
}

car.honk()
```
If we log `this`, we will get `{brand: "Skoda", honk: f}`. So we have access to the members of the object using `this` such as this.brand or this.honk.

The other scenario is using a regular function.
```JavaScript
function honk() {
    console.log(this);
}

honk()
```
This will give us the [window](https://www.w3schools.com/jsref/obj_window.asp) object in browser.

Let's look at one more example where it gets a bit tricky:

```JavaScript
const car = {
    brand: "Skoda",
    colors: ["red", "blue", "pink"],
    showColors() {
        this.colors.forEach(function(color) {
            console.log(color, this.brand)
        });
    }
}

car.showColors()
```

If we execute this code, `this.brand` will be undefined. The reason is that the forEach function uses a callback function which is a regular function. We know that `this` in a regular function references the window object hence we get undefined. To simply avoid this issue, we can supply a second argument in forEach function such as: 

```JavaScript
    showColors() {
        this.colors.forEach(function(color) {
            console.log(color, this.brand)
        }, this);
    }
```
The second argument in the forEach function is an optional parameter that represents the value you want to use as the function argument’s `this` value. By passing an object as the second argument, you can set the value of `this` to that object inside the callback function. This way, you can avoid the issue of getting undefined when trying to access properties of `this` inside the callback function.

Then `this.brand` will print out `Skoda` and not undefined. The better way is to use an arrow function instead. The thing is that the arrow function inherits the `this` value.

```JavaScript
    showColors() {
        this.colors.forEach(color => {
            console.log(color, this.brand)
        });
    }
```

To sum up, it is usually better to use an arrow function as a callback function so that we do not have to do any extra work for binding the `this` keyword.

Happy coding!
