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

Here we can see there is an arrow function inside the parentheses of the **_map()_**  function. If you look closely, you could see that this arrow function has _removed the brackets, the **_return_** keyword and also the parentheses_ as we have discussed above. If you are not familiar with the **_map()_** function, it is just simply take each element of an array and return a new array based on the content of the body of the arrow function inside it. 
