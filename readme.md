# Functions and Scope

## Framing 

We've learned a lot of things that are fundamental to programming, such as
primitive and complex data types, conditionals, and loops. However, we still
need a way to encapsulate logic and make it reusable (make our code more DRY).
Functions are a fundamental part of JavaScript that allow us to contain all of
the logic of a particular operation within a named entity that can be activated,
or "called", repeatedly from other parts of our code.

One feature of functions in JavaScript is that each function creates a new
"scope" when it is defined. Scope defines what variables and functions are
accessible at any given point in the execution of your code. Understanding scope
in JavaScript is key to writing well structured code and being a better
developer.

There's a good chance you'll be asked about scope during technical interviews
too.

## Learning Objectives

### Functions

- Describe what a JavaScript function is
- Recognize the parts of a function
- Write a function in JavaScript using a declaration and an expression
- State the difference between a function's output and side effects
- Differentiate between referencing and invoking a function
- Define hoisting

### Scope

- Describe scope and how it governs how data is able to be accessed in code

## Functions

**What is a Function?**

- Fundamental component of JavaScript
- A reusable block of JavaScript code used to perform a task
- Simply put, a function is a block of code that takes an input, processes that
  input and then produces some form of output

---

**Why do we use functions?**

Benefits of functions:

- Reusability
- DRYness
- Naming convention (describes intent)

---

### Recognize the Parts

**What are the components of a function?**

#### Function Container

```js
function multiply() {}
```

#### Input Parameters (or Arguments)

```js
function multiply(num1, num2) {
  // now you have two variables you can access
  // num1 and num2
}
```

> When we declare a function that takes input values, we call these values
> parameters.

> Conversely, when we _call_ a function and pass values into it, those values
> are called arguments.

> These terms are often used interchangeably, which is okay. But knowing the
> difference can come in handy.

1. num1 and num2 are our parameters. Note that they are in a comma separated list. This tells our function that we are going to give it the function 2 values, num1 and num2.

2. There is nothing special about the words `num1` and `num2` here. These are just descriptive names to remember what information that is being given to our function. We could use other names as well i.e. `number1` and `number2`, `value1` and `value2`, etc. It's best practice to be semantic as possible when declaring parameters.

```js
function multiply(num1, num2) {
  console.log(num1 * num2) // Note: This is a side effect which is covered later.
}

multiply(3, 4) // 12
multipley(6, 3) // 18 
```

3. When the name of the function is followed by `()` the function is being called. By passing comma separated values in between the parentheses (i.e. arguments) correlate to the name of the parameters when the function was declared. Ex: `3` relates to `num1` and `4` relates to `num2`. **Note that the order does matter.**

#### Default/Optional Parameters

Default parameters were introduced in ES6. They allow us to define parameters
that will default to some pre-determined value if the function is called without
passing them in. We can set optional parameters in a function definition by
assigning a value to the parameter definition.

```js
function exponentiate(base, exponent = 2) {
  return base ** exponent
}

exponentiate(4, 3)
=> 64

exponentiate(4)
=> 16
```

### Calling vs Referencing a Function

Let's say we've defined a function. Now we need to call it...

```js
// call a function, passing no arguments
multiply();

// Call a function, passing 2 arguments in
multiply(2, 5);

// Reference the function. What happens if we reference the function without parentheses?
multiply;
```

> When you pass a function into another function as a parameter, do you call it
> or reference it?

#### Output and Side Effects

```js
function multiply(num1, num2) {
  return num1 * num2; // Output
}
```

- Output: What the function evaluates to - noted by keyword `return`

> If a function returns a value, you can store that value in a variable.

```js
let num2 = 5;

function multiply(num1) {
  num2 = num1 * num2; // side effect
}
```

- Side Effects: Effects the function has on data outside of itself (external to
  its scope)

> Note: If you don't specify a return value, it will return `undefined`.

#### More on returns

Understanding what `return` means in a function can be a little tricky.

Here are two similar code snippets - can you explain what the difference is?

```js
const splitMe = "I am the eggman I am the walrus";

function splitString(str) {
  return str.split(" ");
}

const newString = splitString(splitMe);

console.log(newString);
```

```js
const splitMe = "I am the eggman I am the walrus";

function splitString() {
  splitMe.split(" ");
}

splitString();

console.log(splitMe);
```

What does the first one do? What does the second one do?

Are there advantages to doing it the first way? What about the second way? Which
one seems easier to understand?

### You do: Write some functions

Open your code editor and write out the following functions. Try and work through all of these, and we will review afterwards. For the time being, don't worry about creating `side effects`.

1.  Write a function that console.logs 'Hello World'
2.  Write a function that console.logs whatever you want it to say
3.  Write a function that prints every number between 1 and 100.
4.  Write a function that takes an array of numbers, as a parameter and adds each element of that array to a counter and prints the final value of the counter (i.e. the sum of all of the numbers in the array).
e.g. Passing the function the array `[2, 4, 6, 8]` should give you back the answer to `20`
5.  Write a function that loops over the following array of SEI students and prints out their name and what class they are currently in.
  e.g `Alice is in SEI <your_cohort_name>`
  
```js
const students = [
  'Alice',
  'Andrew',
  'Casey',
  'Damian',
  'Grant',
  'Howie',
  'Wade',
  'Kat',
  'Kimbrad',
  'Kiu',
  'Natasha',
  'Obi',
  'Pedro',
  'Sarah',
  'Scott',
  'Tiffany',
  'Zhe',
];
```

6.  Write a function that takes an array of strings as a parameter and returns an array of numbers corresponding to the lengths of each word.
    e.g. passing this function an array `['i', 'am', 'the', 'best']` should give you back `[1, 2, 3, 4]`
    Hint: you can call .length on a string!
7.  Write a function that takes 3 parameters and returns one number, which is the product of the first two numbers raised to the power of the third.
    e.g. passing this function `1, 2, 3` should give you back the answer to `(1 * 2)^3`

Bonus Functions!

1.  Rewrite your previous function to print every EVEN number between 1 and 100
2.  Recreate the Fibonacci sequence between 1 and 20. If you don't know what that is, Google is your best friend!



### Function Declarations and Expressions

There are two ways to define a function...

#### Declaration

```js
function multiply(num1, num2) {
  return num1 * num2;
}
```

#### Expression

```js
var multiply = function(num1, num2) {
  return num1 * num2;
};

// var, let, and const are all valid here
```

#### Declarations vs. Expressions

Calling them is the same regardless of how they're declared.

```js
multiply(2, 5);
```

Both do the same thing and run the same chunk of code but they are different.

**What differences do you notice?**

- **Function declarations** define functions without assigning them to
  variables.
- **Function expressions** assign _anonymous functions_ to variables.

While we call/reference functions defined through declarations and expressions
the same way, they do have a subtle but important difference...

### Hoisting

Hoisting is a general way of thinking about how execution contexts (specifically the creation and execution phases) work in JavaScript. 

Conceptually, for example, a strict definition of hoisting suggests that variable and function declarations are physically moved to the top of your code, but this is not in fact what happens. Instead, the variable and function declarations are put into memory during the compile phase, but stay exactly where you typed them in your code.

Function declarations are processed before any code is executed, meaning you can
call functions before they are declared in the flow of your code. This behavior
is known as **hoisting**.

Conversely, function expressions **are not** hoisted, meaning you cannot call
them before they are defined in the flow of your code.

What do you think will happen when we run the below code...

```js
multiply(3, 5);

var multiply = function(num1, num2) {
  return num1 * num2;
};
// function expression
```

Surely the same thing will happen when we run the below code...

```js
multiply(3, 5);

function multiply(num1, num2) {
  return num1 * num2;
}
// function declaration
```

> We can successfully call the multiply function before declaring it. When our
> script file loads, the browser processes all function declarations first, and
> then runs the rest of our JavaScript from top to bottom.

Knowing this, what will happen each time we call `express` and `declare` in the
below example?

```js
// What happens when we run this function at this point in the code?
express();

var express = function() {
  console.log("Function expression called.");
};
```

What about when we run this example?

```js
var express = function() {
  console.log("Function expression called.");
};

declare(); // ???
express(); // ???

function declare() {
  console.log("Function declaration called.");
}
```

You can read more about hoisting
[here](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)

### ES6 Features

#### Arrow Functions

Following the release of ECMAScript 6 (ES6) in 2015, anonymous functions can be
written as "arrow functions", a syntax adapted from CoffeeScript.

```js
var multiply = function(num1, num2) {
  // function expression
  return num1 * num2;
};
```

What does this look like in ES6?

```js
const multiply = (num1, num2) => {
  return num1 * num2;
};
```

Or, to simplify it further..

```js
const multiply = (num1, num2) => num1 * num2;
```

Arrow functions with a "concise" function body (no brackets and on one line)
have "implicit return". This means you can leave out the `return` keyword and it
still returns.

However, this single line return can be faked with parentheses (NOT CURLY
BRACKETS!)

```js
const multiply = (num1, num2) => (
  num1 * num2
)
```

## Break (10 minutes)

## Scope

### What Is Scope?

**In real life:** Your "scope" is what your eyes can see from wherever you're
standing.

**In Javascript:** scope is...

- Where a variable can be referenced/used.
- A list of all variables that can be accessed from a given line of code.

> Two ways of saying the same thing.

#### Quick Example

Here's a code snippet that demonstrates some of Javascript's fundamental rules
of scope...

```js
function getColor() {
  color = "red";
}

getColor();
console.log(color); // What should we see in the console?
```

Let's see what happens if we add the `let` keyword...

```js
function getAnotherColor() {
  let anotherColor = "green";
}

getAnotherColor();
console.log(anotherColor); // What should we see in the console?
```

#### Rules of Scope in JS

In Javascript, there are two types of scope: **global scope** and **local
scope**.

There are four simple rules to remember about scope in JS...

1. Variables created **without** the `var`, `let`, or `const` keywords, no
   matter where in a program, are placed in the global scope.
2. Variables created **with** the `var`, `let`, or `const` keywords are created
   in the current local scope.
3. All functions create a new local scope.
4. The current scope includes all outer (enclosing) scopes.

> One consequence of rule 3 is that variables defined outside of any function
> are inherently global, even if the `var` keyword is used.

![scope diagram](js-es5-scope-2.png)

Another way to say this...

- **Local variables** defined inside a function cannot be accessed from anywhere
  outside of the function, because the variable is defined only within the scope
  of the function.
- However, a function can access all variables and functions defined inside the
  scope in which it is defined (which includes all outer scopes).

### We Do: A More Complex Example

Let's walk through this example in two steps...

1. Identify and diagram the scope of each variable.
2. Determine whether each `console.log` will error out or not.

```js
teamName = "Giraffes"; // What scope is this?
var teamCity = "Sioux Falls"; // What scope is this?

function playBaseball() {
  console.log("From " + teamCity + "..."); // Does this work?
  console.log("Welcome the " + teamName + "!"); // Does this work?

  pitcherName = "Meg"; // What scope is this?
  var batterName = "Perry"; // What scope is this?

  console.log(batterName); // Does this work?
  console.log(pitcherName); // Does this work?
}

playBaseball();

console.log(teamCity); // Does this work?
console.log(teamName); // Does this work?

console.log(pitcherName); // Does this work?
console.log(batterName); // Does this work?
```

<details>
  <summary><strong>List of scopes for this example...</strong></summary>

> `teamName` - global (no var)  
> `teamCity` - global (not in a function)  
> `pitcherName` - global (no var)  
> `batterName` - local to `playBaseball`

</details>

### More on Hoisting 

#### Functions

A Javascript feature that may impact scope is **hoisting**. This applies to
Javascript functions.

Recall that there are two ways to declare functions in Javascript, **function
declarations** and **function expressions**.

```js
var sayHello = function() {
  console.log("Hello!");
};

function sayHello() {
  console.log("Hello!");
}
```

#### Hoisting Review

<details>
  <summary>
    Which is a function declaration? Which is a function expression?
  </summary>

- `var sayHello = function () {}` is a function expression.
- `function sayHello () {}` is a function declaration.

</details>

<details>
  <summary>
    How does a function declaration differ from a function expression?
  </summary>

- A function expression follows the same rules as variable assignment. Since the
  value of the reference is a function, that function is only available after
  the assignment.
- With a function declaration, no matter where you put it in your code, it
  behaves as if you wrote it as the very first line in your code.
- Aside from that, they are functionally equivalent.

</details>


## Review Questions

1. What is a functions in javascript and how can they be useful?
2. How is a side effect different from an output?
3. What is the difference between calling and referencing a function?
4. How is a function declaration different than a function expression?
5. Explain the difference between local and global scope.
6. Explain how hoisting can affect functions.
7. Explain how hoisting can affect variables.
8. What does DRY mean?

## Bonus: Test Your Scope Knowledge

> 10 minutes exercise. 5 minutes review.

Answer the questions below the following code snippet. The letters in the
questions and answer choices reference lines in the snippet.

```js
/* A */
var username = "XxXskaterBoi2004XxX";
/* B */
function logIn() {
  /* C */
  var sessionID = "8675309";
  /* D */
  return decrypt(sessionID);
  /* E */
  function decrypt(string) {
    /* F */
    var token = profileID;
    /* G */
  }
  /* H */
}
/* I */
logIn();
/* J */
var profileID = 4011989;
/* K */
```

1. The variable `username` **has a value** on which lines? (That is: on which
   lines will `console.log`ing it not return `undefined`?)
   - A, B, I, J, K
   - A and B
   - All lines
   - All lines except A
2. The variable `profileID` **has a value** on which lines?
   - A, B, I, J, K
   - K
   - All lines
   - All lines except A
3. The variable `profileID` **is accessible** on which lines? (That is: on which
   lines can it be `console.log`ged without throwing an error?)
   - A, B, I, J, K
   - K
   - All lines
   - All lines except A
4. The variable `sessionID` **is accessible** on which lines?
   - C, D, E, F, G, H
   - C, D, E, H
   - All lines
   - All lines except F and G
5. The function `decrypt` **is accessible** on which lines?
   - C, D, E, F, G, H
   - C, D, E, H
   - All lines
   - All lines except F and G

<details>

  <summary><strong>When you've finished...</strong></summary>

1. All lines except A. The variable is available on all lines due to hoisting,
   but it only has a value after `username =`
2. K. The variable is available on all lines due to hoisting, but it only has a
   value after `profileID =`
3. All lines.
4. C, D, E, F, G, H
5. C, D, E, F, G, H

</details>

## References

- [Understanding Scope and Context in JavaScript](http://ryanmorr.com/understanding-scope-and-context-in-javascript/)
- [Everything you wanted to know about JavaScript scope](http://toddmotto.com/everything-you-wanted-to-know-about-javascript-scope/)
- [Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
