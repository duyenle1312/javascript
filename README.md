# Javascript Arrow Functions
### Today, we are going to talk about one of the most common topics in Javascript ES6, which is the arrow function.

At the end of this article, you will learn three main ideas:

1. What is the main difference between a normal function and an arrow function?
2. Why should we use arrow functions in Javascript version ES6?
3. Examples of arrow functions and different use cases

## 1. Introduction
First, let's have a look at the way we usually create a function in Javascript ES5:

```sh
function findMax(a,b) {
    return a > b ? a : b;
}
// Or
let findMax = function (a,b) {
    return a > b ? a : b;
}
```

![](/normalFunctions.png "Normal Functions")

Now, let's have a look at the arrow function syntax:

```sh
const findMax = (a,b) => {
    return a > b ? a : b; // If a > b, return a, otherwise, return b
};
let a = findMax(5,6);
console.log(a); // This will return 6 in the console
```

![](/arrowFunction.png "An arrow Function")

As you can see, the body of the function is very much similar to the normal function with the same functionality, the only difference is the header. When we get rid of the keyword "function", it is now much easier and less time-consuming to write a declaration for a function. 

[//]: # (* Const and let could be here)

If this does not convince you to use arrow functions, then have a look at how we could even shorten the function body even more in the next section.

## 2. Syntax and Declaration

Because the inner content of the function does not change, we usually use the ```const``` type with the name of an arrow function. If the **function body has only one line**, the brackets and the **_return_** keyword could be omitted like this:

```sh
const findMax = (a,b) => a > b ? a : b;
```

If there is only **one parameter**, you could also remove the parentheses:

```sh
const sayHello = name => console.log(`Hello ${name}`)
```

If there is **no parameter** at all, you still need to put the parentheses before the arrow of the function:

```sh
const welcomeToBulgaria = () => console.log("Hi there, welcome to Bulgaria!")
```

Now let's see how we can use the arrow functions to **calculate and return a value**:

```sh
const add = (a, b) => a + b;
let sum = add(13, 12);
console.log(sum); // This will print 25 (12 + 13) to the console
```

You can also **return anything else such as an array, or an object** similarly to a normal function. For example, let's return an object from all the arguments:

```sh
const createPerson = (name, age) => {
    return { name: name, age: age };
}
let student = createPerson("Duyen Le", 18);
console.log(student); // Print {name: 'Duyen Le', age: 18}
```
![](/returnObjects.png "Return an object from an arrow function")

How about double each element in an array?

```sh
const arr = [1, 2, 3];
const doubleArray = arr.map(element => element ** 2);
console.log(doubleArray); // [1, 4, 9]
```

Here we can see there is an arrow function inside the parentheses of the **_map()_**  function. If you look closely, you could see that this arrow function has _removed the brackets, the **_return_** keyword and also the parentheses_ as we have discussed above. If you are not familiar with the **_map()_** function, it just simply takes each element of an array and return a new array based on the content of the arrow function body. 

## 3. Disadvantages
### Constructors
Despite all the benefits, arrow functions could not satisfy all the use cases of a normal function in Javascript. For example, arrow functions could not be used to create constructors because they do not have their own bindings to the ```this``` or ```super``` keywords. 

When you access ```this``` inside **an inner function (inside a method)**, this refers to the global object. For example,

```sh
const person = {
    name : 'Jack',
    age: 25,

    // this inside method
    // this refers to the object itself
    greet() {
        console.log(this);        // {name: "Jack", age ...}
        console.log(this.age);  // 25

        // inner function
        function innerFunc() {
        
            // this refers to the global object
            console.log(this);       // Window { ... }
            console.log(this.age);    // undefined
            
        }

        innerFunc();

    }
}

person.greet();
```
Output:
```sh
{name: "Jack", age: 25, greet: ƒ}
25
Window { …}
undefined
```
Here, ```this``` inside ```innerFunc()``` refers to the global object because ```innerFunc()``` is inside a method, ```this.age``` outside ```innerFunc()``` refers to the person object.

**Arrow functions** do not have their own ```this```, usually, ```this``` in an arrow function refers to its parent scope object. For example,

```sh
const greet = {
    name: 'Jack',

    // method
    sayHi () {
        let hi = () => console.log(this.name);
        hi();
    }
}

greet.sayHi(); // Jack
```

Here, ```this.name``` inside the ```hi()``` function refers to **the greet object**.


### Arguments Binding
Regular functions have arguments binding. That's why when you pass arguments to a regular function, you can access them using the arguments keyword. For example,

```sh
let x = function () {
    console.log(arguments);
}
x(4,6,7); // Arguments [4, 6, 7]
```

Arrow functions, however, do not have arguments binding. When you try to access an argument using the arrow function, it will give an error. For example,

```sh
let x = () => {
    console.log(arguments);
}

x(4,6,7); // ReferenceError: Can't find variable: arguments
```
To solve this issue, you can use the spread syntax.

```sh
let x = (...n) => {
    console.log(n);
}

x(4,6,7); // [4, 6, 7]
```

So that's the end of today topic about arrow functions, I hope you find something  interesting along the way that might be useful for your next project or job interview.

Happy coding!
