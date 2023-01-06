# Learning Functional Programming with JavaScript ES6+

Shaun Wassell

---

## Introduction

- Switching from Object Oriented Programming to functional programming
  - Minimize potential for bugs
  - Maximize readability and reusability
- Coding paradigm
- Championed by languages like Lisp and Haskell
- Natively supported in JS

- Check Linux-windows equivalent commands

  - [Linux-Windows Equivalent Commands](https://skimfeed.com/blog/windows-command-prompt-ls-equivalent-dir/)

- Tools necessary
  - sudo npm install -g npm@latest
  - npm -v and node -v to show version
  - node.js
  - NPM

### NPM

- create directory
  - mkdir
- set npm directory
  - npm init -y
- currently, node JS doesnt have native support for ES6 syntax, so we need a tool called babel to act as the middleman between the modern ES6 syntax and common JS syntax which node JS can run

- TWO STEPS

  - install babel packages
    - npm install --save @babel/core @babel/node @babel/preset-env
  - new file
    - .babel.rc

  ```json
  {
    "presets": ["@babel/preset-env"]
  }
  ```

- Ussually it is run as
  - node src/myfile.js
- Since we're going to be writing our code in ES6 syntax not nativelly supported by node.js

  - npx babel node src/myfile.js

  ```
  You have mistakenly installed the `babel` package, which is a no-op in Babel 6.
  Babel's CLI commands have been moved from the `babel` package to the `babel-cli` package.


      npm uninstall babel
      npm install --save-dev babel-cli
  ```

<font size="3">**npx babel-node filename.js**</font>

---

## 1. Introductory Functional Concepts

### The goal of functional programming

- Functional programming is concerned with tracking a large number of complex ideas present in any large computing program and organizing them in a coherent way, maintaining the code easy to test and modify.
- Functional programming aims to bring the precision of mathematical functions into computer programs.

![Function Box](/2022-12-14-LearningFunctionalProgrammingwithJavaScriptES6%2B/Chapter01/Capture01-01.JPG)

### Declarative vs imperative programming

- Imperative: "How?"
- Declarative: "What?"

![Imperative vs Decalarative](/2022-12-14-LearningFunctionalProgrammingwithJavaScriptES6%2B/Chapter01/Capture01-02.JPG)

- Core Concepts of Functional Programming
  - Immutability
  - Separating functions and data
  - First-class functions

### Immutability

- immutability means that mots of the values in a program are constant (Javascript means using the const keyword)
  In functional programming, we don't assign, we define

### Separation of data and functions

- in OOP functions are wrapped up inside objects along with the data that they operate on, and allow us to access or make changes to that data.
- In Functional Programming, functions are completely separate entities from the data that they operate on.
  - the data must be passed as arguments to the function instead of using the this keyword
  - they dont touch the original data, they only return a modified copy of that data.

### Object oriented to functional approach

- The main reason that in OOP the data and functiosn are togeteher, is because it allows us to intercat with the member variables of an object without touching them directly
- Because of the rule of immutability, in functional programming, it is not needed to make all our data private, since it cannot be changed

### First-class functions

- In functional programming, we would never think of, but it's not only possible, but a sou8rce of tremendous flexibility:
  - creating an array of functions
  - passing functions as arguments to other functions
  - returning functions from other functions
- In Functional programming, we design our functions specifically so that they work in isolation.
  All of the data that the functions needs is passed in through the arguments

### Ensuring immutability: ESLint

- By default, even when you use const, you can modify the elements of an array, use methods like reverse. and also modify the values for keys within an object with no complain from JavaScript

### Ensuring immutability: Install ESLint

```
npm init -y
npm install --save-dev eslint
npx eslint --init
```

```
? How would you like to use ESLint? To check syntax, find problems, and enforce code style
? What type of modules does your project use? JavaScript modules (import/export)
? Which framework does your project use? None of these
? Where does your code run? (Press <space> to select, <a> to toggle all, <i> to invert selection)Browser
? How would you like to define a style for your project? Use a popular style guide
? Which style guide do you want to follow? Airbnb (https://github.com/airbnb/javascript)
? What format do you want your config file to be in? JavaScript
```

- it creates the .eslintrc.js file

### Ensuring immutability: Finalize ESLint

```
npm install --save-dev eslint-plugin-immutable
```

- then adds the following to eslintrc.js file

  ```json
    plugins: [
      'immutable',
    ],
  ```

- and within rules:

  ```json
    rules: {
      'immutable/no-mutation': 2,
    },
  ```

- where 2 is error, 1 warning and 0 disabled

---

## 2. First-Class Functions

### Arrow functions in ES6

- Pre ES6 function definition (using function keyword)

  ```js
  function myFunction(arg1, arg2) {
    // function body
  }

  const myOtherFunction = function (arg1, arg2) {
    // function body
  };
  ```

- ES6 allows us to get rid of the function keyword completely with arrow functions syntax

  - arrow functions allow to get rid of the brackets in case of just one return argument

    ```js
    const add = (x, y) => x + y;
    ```

  - arrow functions allow to have a function with no arguments (Parenthesis needed)

    ```js
    const sayHello = () => console.log("Hello");
    ```

  - arrow functions allow to return an object (Since it needs to be within brackets, it has to be enclosed within parenthesis, so it is not confused as the function body)

  ```js
  const getPersonData = () => ({
    name: "John Doe",
    age: 34,
    job: "programmer",
  });
  ```

### Functions as data

- Functionsd as first class citicens, meaning they can be treated like other types, likes strings, numbers and objects.
- Good way to use functiosn as data to decide which function to execute

  ```js
  const DEVELOPMENT = true;

  const fetchDataReal = () => {
    // time-intensive operations here!
  };

  const fetchDataFake = () => ({
    name: "John Doe",
    age: 34,
  });

  const fetchData = DEVELOPMENT ? fetchDataFake : fetchDataReal;
  ```

- Array of functions

  - With no parenthesis within the array, since we are putting directly the function itself
  -

  ```js
  const double = (x) => x * 2;
  const subtractOne = (x) => x - 1;
  const triple = (x) => x * 3;
  const add5 = (x) => x + 5;

  const functionsArray = [double, subtractOne, triple, add5, Math.sqrt];

  var number = 42;
  functionsArray.forEach((func) => (number = func(number)));
  console.log(number);
  ```

### Passing functions as arguments

- What if instead of passing arguments into our function to specify what the data is, we could pass in arguments to specify what was done to our data
- Defining functions separately before passing them as arguments. --> For readability, it is good practice, but you can define them as well as anonymous functions defined on the spot

  ```js
  const add = (x, y) => x + y;
  const subtract = (x, y) => x - y;

  const combine2and3 = (func) => func(2, 3);

  combine2and3(add); // -> 2 + 3
  combine2and3((x, y) => x + y); // anonymous function
  combine2and3(subtract); // -> 2 - 3

  combine2and3(Math.max); // -> 3
  ```

### Returning functions

- a function that returns a function (like a function creator)
- An arrow function creating another arrow function (So, it presents the confusing syntax of two () => in line)
- These two functions are the same

  ```js
  const createPrinter = () => () => console.log("Hello");

  const createPrinter = function () {
    return function () {
      console.log("Hello");
    };
  };
  ```

- By using returning function and function creation these two blocks are doing the same

  - Original Functions block

    ```js
    const double = (x) => x * 2;
    const triple = (x) => x * 3;
    const quadruple = (x) => x * 4;
    ```

  - Creator function block

    ```js
    const createMultiplier = (y) => (x) => x * y;

    const double = createMultiplier(2);
    const triple = createMultiplier(3);
    const quadruple = createMultiplier(4);
    ```

### Closure

- Closure means that when we define a function that returns another function, the function that we returned still has access to the internal scope of the function that returned it.
- Very important conpcept, since without it, returning functions would be pretty useless in most cases.

  ```js
  const createPrinter = () => {
    const myFavoriteNumber = 42;

    return () => console.log("My favorite number is ${myFavoriteNumber");
  };

  const printer = createPrinter();
  printer();
  ```

### Implement private variable

- \_variableName is supposed to signify never directly use this variable. programmers will always ignore this when it's convenient
- This example use closure to make these variables accesible to the outside world only through getters and setters
- the getName function is the only way we can access the name variable

  ```js
  const Person = ({ name, age, job }) => {
    var _name = name;
    var _age = age;
    var _job = job;

    return {
      getName: () => _name,
      getAge: () => _age,
      getJob: () => _job,

      setJob: (newJob) => (_job = newJob),
    };
  };

  const me = Person({ name: "Shaun", age: 25, job: "developer" });
  console.log(me.getJob());
  me.setJob("senior developer");
  console.log(me.getJob());
  ```

### Higher-order functions

- functions that either take other functions as arguments or retunr functions
- The single responsability principle, in writing clean code: Each piece of code should have only one responsability

  - Use case --> Problem of checking arguments in JS

    ```js
    const divide = (x, y) => x / y;

    const secondArgumentIsntZero =
      (func) =>
      (...args) => {
        if (args[1] === 0) {
          console.log("Error: dividing by zero");
          return null;
        }

        return func(...args);
      };

    const divideSafe = secondArgumentIsntZero(divide);

    console.log(divideSafe(7, 0));
    console.log(divideSafe(5, 3));
    ```

---

## 3. JavaScript: The Functional parts

### Functional parts

- Built-in functions easy to work towards functional programming, like arrays methods
- map, filter, reduce and sort

### The spread operator

- spread operator allows us to, sort of, spread the properties of one object inside another.
- for Objects and arrays
- it can be used to update properties of an object

### Mapping

- convert each of the individual elements of an array.
- pass a function into the map built-in funciton
  map doesnt change the original array. This is not the case for many other built-in functions

  ![Mapping Method](/2022-12-14-LearningFunctionalProgrammingwithJavaScriptES6%2B/Chapter03/Capture03-01%20Mapping.JPG)

### Filtering

- find all of the elements in an array that fot some kind of criteria
- good example using higher-rder function to filter words with lenght than an specified value.

  ```js
  const createLengthTest = (minLength) => (word) => word.length > minLength;

  const longWords = words.filter(createLengthTest(5));
  ```

  ![Filtering Method](/2022-12-14-LearningFunctionalProgrammingwithJavaScriptES6%2B/Chapter03/Capture03-02%20Filtering.JPG)

### Every/some

- Every and some returns a single boolean.

![Every/Some Methods](/2022-12-14-LearningFunctionalProgrammingwithJavaScriptES6%2B/Chapter03/Capture03-03%20Every-Some.JPG)

- In this example, double exclamation mark notation to convert strings into booleans. It works because empty string is falsy

  - [Double Exclamation Mark](https://www.codingem.com/javascript-double-exclamation-operator/#:~:text=In%20JavaScript%2C%20the%20double%20exclamation,%E2%80%9Ctruthy%E2%80%9D%20objects%20become%20true.)
    In JavaScript, the double exclamation operator converts an Object to Boolean. This happens such that “falsy” objects become false and “truthy” objects become true. For example:

    - !! 0 –> false
    - !! null –> false
    - !! undefined –> false
    - !! 48 –> true
    - !! “hello” –> true
    - !! [1, 2, 3] –> true

  ```js
  const formValues = ["Shaun", "Wassell", "Maine", "developer"];
  const isNotEmpty = (string) => !!string;
  const allFieldsFilled = formValues.every(isNotEmpty);
  ```

### Slicing

- it doesnt take a function as argument
- slice obtains a subset of the array
- slice returns a copy (do not modify original array)
- default arguments for slice, take the whole array

  ![mutating Functions](/2022-12-14-LearningFunctionalProgrammingwithJavaScriptES6%2B/Chapter03/Capture03-04%20Mutating%20Functions.JPG)

- There is a simple workaround to turn mutating functions into non-mutating functions by using slice() and the calling the mutating function

```js
const numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

console.log(numbers.slice().reverse());
console.log(numbers);
```
