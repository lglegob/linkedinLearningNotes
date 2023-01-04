# Learning Functional Programming with JavaScript ES6+

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

```
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

**npx babel-node filename.js**

## Introductory Functional Concepts

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
