# JavaScript Notes

## Table Of Contents

- [Variables](#variables)
- [Data Types](#data-types)
- [Functions](#functions)
  - [Traditional Functions](#functions)
  - [Arrow Functions](#arrow-functions)
- [Guard Clauses](#guard-clauses)
- [Destructuring](#array-destructuring)
  - [Array Destructuring](#array-destructuring)
  - [Object Destructuring](#object-destructuring)
- [Ternary Operator](#ternary-operator)
- [Rest Parameter](#rest-parameter)
- [Spread Syntax](#spread-syntax)
- [Short Circuiting](#short-circuiting)
- [Switch Statements](#switch-statements)
- [Array Methods](#array-methods)
  - [Push](#push)
  - [Pop](#pop)
  - [Unshift](#unshift)
  - [Shift](#shift)
  - [Includes](#includes)
  - [Join](#join)
  - [Filter](#filter)
  - [Map](#map)
  - [forEach](#foreach)
  - [Reduce](#reduce)
  - [Slice](#slice)
  - [Splice](#splice)
- [Class / Classes](#classes)
- [Advanced Console Methods - Useful When Debugging](#advanced-console-methods)
- [Code Snippets](#code-snippets)
  - [Generate A Random Number](#generate-a-random-number)
- [Helpful JavaScript Developer - Tools and Resources](#helpful-javascript-developer-tools-and-resources)
- [Glossary - Programming Terminology](#glossary-programming-terminology)


<br>
// Add anchor tags here to other my other notes repos - HTML, CSS, TypeScript, React ect

<br><br><br>
Notes to write next:

* DEFAULT PARAMETERS
* CONSTRUCTORS - Date(), Error()
* setTimeout() function / method

* More of the basic array methods
* Logical operators
* Math functions
* Selectors such as getElementById ect
* for loop - with the use of break and continue - refer to scrimba - JS mini Projects - for loop break and continue - lesson
* Loops, for, for of /
* forEach
* typeof()
* Add a glossary / word dictionary for words such as, callback function, return, closure, break, continue, operands, control flow, OOP, functional programming

Format and style these readme's better
Look up most popular JS array methods on youtube

<br><br>

# Variables

JavaScript provides three main ways to declare variables, each with its distinct behavior: var, let, and const.
Understanding the differences is crucial for effective and error-free coding.

## let & const
* Scope: Block scope (a block is anything between {} braces).
* Hoisting: Variables are hoisted but not initialized. Accessing them before declaration results in a ReferenceError.
* Re-declaration: Cannot be re-declared in the same scope.

Re-assignment of values:

* let allows re-assignment of values.
* const does not allow re-assignment. The variable must be initialized at the time of declaration and cannot be changed afterward. However, objects and arrays declared with const can have their contents modified (e.g., adding or changing properties).

## var
* Scope: Function scope or globally scoped if declared outside of a function.
* Hoisting: Variables are hoisted to the top of their scope, allowing them to be used before they are declared.
* Re-declaration: Allows re-declaration of the same variable within the same scope.
* Re-assignment: Allows re-assignment of values.

* Var is primarily encountered in legacy codebases, and its use is generally discouraged in favor of let and const, which were introduced in the ES6 update for more specific and safer variable declarations.


## Key Differences
* Scope: var is function or globally scoped, while both let and const are block-scoped.
* Hoisting: All are hoisted, but var is initialized with undefined, making it accessible before declaration. In contrast, let and const are in a "temporal dead zone" from the start of the block until the declaration is reached.

Mutability:
* Variables declared with let can be updated but not re-declared.
* Const declarations cannot be updated or re-declared.
* Var allows both re-declarations and updates within its scope.

<br><br>

# Data Types

JavaScript variables can hold different types of data, classified into two main categories: primitive types and reference types.

JavaScript is a dynamically typed language, meaning variables do not need to be declared with a data type, and their types can change at runtime.<br>
Primitive types are immutable and operated on by value, whereas reference types (objects) are mutable and operated on by reference.<br>
Understanding these types and their behaviors is crucial for effective JavaScript programming, as it affects variable declaration, function return values, and overall data manipulation within your applications.

## Primitive Types

String: Represents textual data.
```
let name = "John Doe";
```

Number: Represents both integer and floating-point numbers.
```
let age = 25; // Integer
let price = 99.99; // Floating-point
BigInt: Represents integers with arbitrary precision.
let bigNumber = 1234567890123456789012345678901234567890n;
```

Boolean: Represents a logical entity with two values: true and false.
```
let isAvailable = true;
```

Undefined: Represents a variable that has not been assigned a value.
```
let result;
console.log(result); // undefined
Null: Represents the intentional absence of any object value.
let empty = null;
```

Symbol: Represents a unique, immutable identifier.
```
let symbol = Symbol("description");
```


## Reference Types (Objects)

Object: Represents instances of keyed collections and more complex entities.
```
let person = { name: "John Doe", age: 30 };
```

Array: Represents a list-like object of ordered values.
```
let numbers = [1, 2, 3, 4, 5];
```

Function: Represents code that can be invoked.
```
function greet() {
  console.log("Hello, World!");
}
```

<br><br>

# Shallow Copy vs Deep Copy
A shallow copy of an object creates a new object with the same first-level properties as the original. However, it does not create copies of nested objects; instead, it copies their references. Thus, if you modify a nested object in the copy, the change will also reflect in the original object, and vice versa. Shallow copying is useful when you want to duplicate an object's structure without needing to create independent copies of its internal objects.

A deep copy goes further by duplicating every level of an object, including all nested objects. This means that the copy and the original are completely independent; changes made to deeply nested objects in the copy do not affect the original, and vice versa. Deep copying is essential when you need to work with a truly separate copy of an object without affecting the original, preserving the integrity of nested structures.

<br><br>

# Functions

Functions in JavaScript are blocks of code designed to perform a particular task, and they are a fundamental building block of the language.<br>
JavaScript functions can be defined in several ways and can be called or invoked to execute the block of code whenever needed.

Also read [Arrow functions](#arrow-functions) which became available in ES6, they provide a modern and concise syntax for writing function expressions.<br>
<br>

> **Important To Remember:** In JavaScript, when using return:<br>
Exiting a Function: If return is called with no value, the function exits immediately, and undefined is returned to the caller.<br>
Returning a Value: If return is followed by a value, that value is returned to the function caller, and the function execution stops at that point.

<br>

Function Declaration<br>
A function declaration defines a function with the specified parameters.

```
function sayHello(name) {
  console.log(`Hello, ${name}!`);
}

sayHello('Alice'); // Output: Hello, Alice!
```

Function Expression<br>
A function expression assigns an anonymous function to a variable. Function expressions can be named or anonymous.
```
const greet = function(name) {
  console.log(`Hello, ${name}!`);
};

greet('Bob'); // Output: Hello, Bob!
```


Immediately Invoked Function Expression (IIFE)<br>
An IIFE is a function that runs as soon as it is defined.
```
(function() {
  console.log('This runs right away');
})();
```

Parameters and Arguments<br>
Functions can accept parameters and be invoked with arguments.
```
function multiply(a, b) {
  return a * b;
}

console.log(multiply(2, 4)); // Output: 8
```

Default Parameters (ES6)<br>
Default parameters allow named parameters to be initialized with default values if no value or undefined is passed.
```
function greet(name = 'Guest') {
  console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, Guest!
```
Rest Parameters (ES6)<br>
Rest parameters allow us to represent an indefinite number of arguments as an array.
```
function sum(...numbers) {
  return numbers.reduce((acc, current) => acc + current, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10
```

Use Cases:

1. Code Reusability: Write code once and reuse it multiple times with different arguments.
2. Modularizing Code: Break down complex problems into smaller, manageable pieces.
3. Event Handling: Define behavior for user interactions in the browser.
4. Callbacks and Asynchronous Programming: Functions allow for asynchronous execution flows, such as in AJAX requests, timers, and event handlers.
5. Closures: Functions can create closures, which allow for private variables and methods, enabling data encapsulation.


<br><br>

# Arrow Functions

Arrow functions, introduced in ES6 (ECMAScript 2015), offer a concise syntax for writing function expressions in JavaScript.<br>
They are particularly useful for short functions and are often used in callback-based code, like event handlers or setTimeout.

Arrow functions streamline function declaration and offer lexical scoping of this, making them a powerful feature for modern JavaScript development.<br>
However, they are not suitable for all situations, such as methods defined in object literals or constructors, where traditional function expressions or declarations might be more appropriate.

Syntax:

The basic syntax of an arrow function is as follows:
```
const functionName = (parameters) => {
  // function body
};
```
If the function has only one parameter, parentheses around the parameter list are optional.<br>
If the function body contains just a single statement, you can omit the curly braces and the return statement.<br><br>

Code Examples:

Basic Arrow Function
```
const greet = () => {
  console.log("Hello, World!");
};

greet(); // Output: Hello, World!
```

With Parameters
```
const add = (a, b) => {
  return a + b;
};

console.log(add(5, 3)); // Output: 8
```

Single-Line Function<br>
For a single-line function that returns a value, you can omit the braces and the return keyword:
```
const square = x => x * x;

console.log(square(4)); // Output: 16
```

Returning Objects<br>
To return an object literal directly, enclose the object in parentheses:
```
const getObject = () => ({ name: "John", age: 30 });

console.log(getObject()); // Output: { name: 'John', age: 30 }
```

Arrow Functions as Callbacks<br>
Arrow functions are often used for callbacks due to their concise syntax:
```
const numbers = [1, 2, 3, 4, 5];

const squares = numbers.map(number => number * number);

console.log(squares); // Output: [1, 4, 9, 16, 25]
```

Use Cases:

1. Callbacks and Array Methods: Ideal for short callback functions passed to methods like map(), filter(), reduce(), etc.
2. Event Handlers: Concisely define event handlers for DOM elements.
3. Functional Programming: Supports a more functional style of coding with concise function expressions.
4. Inline Functions: Useful for defining inline functions where brevity is valued.
5. Lexical this: Arrow functions capture the this value of the enclosing context, making them suitable for use in methods that need to access the this of their containing object.

<br><br>

# Guard Clauses

Guard clauses are used to improve code readability and efficiency by handling edge cases or invalid conditions early in a function or block of code.<br>
They act as early returns that "guard" against further execution if certain conditions are not met,<br>
thus avoiding nested if-else statements and making the main logic of the function clearer and less indented.


* Early Exit: A guard clause provides an early exit from a function if a condition is not met, reducing the need for additional indentation and nested conditions.
* Simplification: Simplifies the logic by dealing with edge cases or errors upfront, making the remaining code easier to understand.
* Improves Readability: Helps in separating the handling of special conditions from the main logic, improving code readability.

<br>

> **Important To Remember:** In JavaScript, when using return:<br>
Exiting a Function: If return is called with no value, the function exits immediately, and undefined is returned to the caller.<br>
Returning a Value: If return is followed by a value, that value is returned to the function caller, and the function execution stops at that point.

<br>

Code Examples:<br>

Basic Guard Clause: Handling invalid input in a function.
```
function processOrder(order) {
  if (!order) {
    console.log('No order provided');
    return; // Early return if order is not provided
  }

  // Proceed with order processing
  console.log('Processing order', order);
}

processOrder(null); // Output: No order provided
processOrder('1234'); // Output: Processing order 1234
```

Multiple Guard Clauses: Using multiple conditions to exit early for different cases.
```
function calculateDiscount(price, customer) {
  if (price <= 0) {
    return 0; // Early return for invalid price
  }
  if (!customer.isPremium) {
    return price * 0.05; // Standard discount for non-premium customers
  }

  // Enhanced discount for premium customers
  return price * 0.1;
}

console.log(calculateDiscount(100, { isPremium: false })); // Output: 5
console.log(calculateDiscount(100, { isPremium: true })); // Output: 10
```

Guard Clauses in Async Functions: Handling missing parameters in asynchronous functions.
```
async function fetchData(userId) {
  if (!userId) {
    throw new Error('User ID is required');
  }

  // Fetch data for the given user ID
  const data = await getUserData(userId);
  return data;
}
```

Use Cases:

1. Input Validation: Early validation of function parameters to ensure they meet certain criteria before proceeding.
2. Error Handling: Returning errors or default values early in a function when encountering an invalid state.
3. Feature Flags or Permissions: Checking for permissions or feature flags before executing feature-specific logic.
4. Guard clauses offer a straightforward and effective way to make code more readable and maintainable by handling special conditions early and keeping the main logic clean and uncluttered.

<br><br>

# Array Destructuring

Array destructuring is a syntax introduced in ES6 that allows for unpacking elements from array literals into individual variables, making working with arrays more efficient and readable.


Syntax:
```
const [element1, element2] = array;
```

Examples:

Basic Destructuring
```
const numbers = [1, 2, 3];
const [first, second] = numbers;

console.log(first);  // 1
console.log(second); // 2
```

Skipping Elements
```
const fruits = ["Apple", "Banana", "Orange"];
const [first, , third] = fruits;

console.log(first); // "Apple"
console.log(third); // "Orange"
```

Nested Arrays
```
const colors = ["red", ["green", "darkGreen"], "blue"];
const [primary, [secondary, tertiary]] = colors;

console.log(primary);   // "red"
console.log(secondary); // "green"
console.log(tertiary);  // "darkGreen"
```

Swapping Variables
```
let a = 1, b = 2;
[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1
```

Function Return Values
```
function getCoordinates() {
  return [17.385044, 78.486671]; // Example coordinates
}

const [latitude, longitude] = getCoordinates();

console.log(latitude);  // 17.385044
console.log(longitude); // 78.486671
```


Use cases:

1. Ignoring Unwanted Values: Provides a convenient way to skip over elements of an array that are not needed in the current context, making it easier to focus on relevant data.
2. Function Parameters: Especially useful in functions that accept arrays as arguments, allowing for direct unpacking of array elements into parameters for immediate use within the function.
3. Multiple Return Values: Simplifies the extraction of multiple values returned from a function into separate variables, making the code cleaner and more intuitive.
4. Swapping Variables: Offers an elegant, concise way to swap the values of two variables without needing a temporary variable, enhancing code simplicity.
5. Iterating Over Arrays: Improves readability and efficiency when iterating over arrays of arrays (like matrixes or CSV data), allowing for direct access to nested values.

<br><br>

# Object Destructuring

Object destructuring is a powerful feature in JavaScript (introduced with ES6) that allows for unpacking values from objects into distinct variables.

Object destructuring enhances code readability and efficiency, streamlining the process of working with objects and their properties in JavaScript.

The syntax is both concise and readable, significantly simplifying the task of extracting multiple properties from objects.

syntax:
```
const { property1, property2 } = object;
```


Exmples:

Basic Destructuring
```
const person = { name: 'John Doe', age: 30 };
const { name, age } = person;

console.log(name); // "John Doe"
console.log(age); // 30
```


Destructuring with New Variable Names
```
const person = { name: 'Jane Doe', age: 28 };
const { name: fullName, age: personAge } = person;

console.log(fullName); // "Jane Doe"
console.log(personAge); // 28
```



Destructuring with Defaults

```
const person = { name: 'Emily' };
const { name, age = 25 } = person;

console.log(name); // "Emily"
console.log(age); // 25 (default used)

```

Nested Object Destructuring
```
const person = {
  name: 'Chris',
  age: 34,
  contact: { email: 'chris@example.com', phone: '123-456-7890' },
};
const {
  contact: { email, phone },
} = person;

console.log(email); // "chris@example.com"
console.log(phone); // "123-456-7890"
```

Function Parameter Destructuring
```
function introduce({ name, age }) {
  console.log(`My name is ${name} and I am ${age} years old.`);
}

const person = { name: 'Alex', age: 22 };
introduce(person); // "My name is Alex and I am 22 years old."
```

Use Cases:

1. Function Parameters: Simplifies working with objects as function parameters by directly unpacking the needed properties within the function's signature, reducing the need for repetitive property access within the function body.
2. Configuration Objects: Facilitates the use of configuration objects in function calls, allowing for easy extraction of configuration properties without manually digging into the object structure.
3. React Component Props: In React and other component-based libraries, destructuring is commonly used to unpack props, making the code cleaner and more readable.
4. Multiple Return Values: Allows for returning multiple values from a function in an object and unpacking these values concisely, simulating named return values.
5. Swapping Values: Enables an elegant way to swap the values of two variables without needing a temporary variable.

<br><br>

# Ternary Operator

The ternary operator is a concise way to perform an if-else statement in a single line of code.<br>
However, for complex conditions or multiple if-else branches, traditional control flow statements might be more appropriate to maintain code readability.<br>
It is the only JavaScript operator that takes three operands: a condition, a result for true, and a result for false.

The ternary operator is very versatile, It can be used for conditional assignments, function calls, and even inline conditional operations without the need for multiple lines of code.

Syntax:
```
condition ? expressionIfTrue : expressionIfFalse;
```
* condition: An expression that is evaluated for a boolean value.
* expressionIfTrue: The expression to execute if the condition is true.
* expressionIfFalse: The expression to execute if the condition is false.

Code Examples:

Basic Usage
```
const age = 18;
const canVote = age >= 18 ? 'Yes' : 'No';
console.log(canVote); // Output: "Yes"
```

Nested Ternary<br>
Ternary operators can be nested, but for the sake of readability, it's generally better to use them sparingly in such cases.
```
const score = 85;
const grade = score >= 90 ? 'A' :
              score >= 80 ? 'B' :
              score >= 70 ? 'C' :
              score >= 60 ? 'D' : 'F';

console.log(grade); // Output: "B"
```

Choosing Between Two Functions
```
const isLoggedIn = true;
isLoggedIn ? logout() : login();

function login() {
  console.log('Logging in...');
}

function logout() {
  console.log('Logging out...');
}

// Output: "Logging out..."
```

Assigning Variables Based on Condition
```
const time = 9;
const timeOfDay = time < 12 ? 'Morning' : 'Afternoon';

console.log(`Good ${timeOfDay}!`); // Output: "Good Morning!"
```

Use Cases:

1. Conditional Rendering: Useful in UI programming, such as JavaScript frameworks (React, Vue.js), for conditionally rendering elements.
2. Quick Decisions: Handy for making quick decisions between two values or executing one of two functions.
3. Inline Conditions: Simplifies expressions where traditional if-else statements would be too verbose.

<br><br>

# Rest Parameter

The rest parameter syntax allows a function to accept an indefinite number of arguments as an array, providing a way to handle function parameters more flexibly.<br>
Unlike the arguments object, rest parameters are real arrays, and thus, array methods like map, reduce, or forEach can be applied directly.


Syntax:
```
function functionName(...restParameters) {
  // function body
}
```

...restParameters: An array containing the rest of the function's arguments. This allows the function to collect any number of arguments into an array.

Code Examples:

Collecting Arguments into an Array
```
function sum(...numbers) {
  return numbers.reduce((acc, current) => acc + current, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10
```

Using Rest Parameters with Other Parameters
```
function fullName(firstName, lastName, ...titles) {
  const titleStr = titles.join(' ');
  return `${titleStr} ${firstName} ${lastName}`;
}

console.log(fullName('John', 'Doe', 'Dr.', 'PhD')); // Output: "Dr. PhD John Doe"
```

Rest Parameters vs. arguments Object<br>
Rest parameters provide a real array, so array methods like map, reduce, or forEach can be directly applied, which is not the case with the arguments object.
```
function countArguments(...args) {
  return args.length; // args is a real array
}

console.log(countArguments('a', 'b', 'c')); // Output: 3
```

Use Cases:

1. Variadic Functions: Functions that take an indefinite number of arguments, such as mathematical operations (sum, min, max) or string manipulation functions.
2. Parameter Grouping: When you have a function that takes a fixed number of parameters followed by a variable number of parameters (e.g., a logging function that takes a prefix followed by any number of messages).
3. Function Overloading: Simulating function overloading by handling different numbers of arguments and types dynamically within a single function.

<br><br>

# Spread Syntax

The spread syntax (...) allows an iterable such as an array, string, or object to be expanded in places where zero or more arguments (for function calls), elements (for array literals), or key-value pairs (for object literals) are expected.<br> Introduced in ES6, it provides a more concise and readable way to perform various operations that involve combining or spreading out elements of iterable objects.

The spread syntax is very versatile, It can be used in various contexts, including function calls, array, and object literals.<br>
When used with objects and arrays, the spread syntax creates a shallow copy, meaning that it copies properties and elements by reference for nested objects or arrays.<br><br>

Syntax:
```
Function Calls: myFunction(...iterableObj);

Array Literals or Strings: [...iterableObj, 'newElement', anotherArray];

Object Literals: {...obj, newProp: 123};
```
<br>

Code Examples:

In Function Calls<br>
Expands an array into individual arguments in a function call.
```
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];
console.log(sum(...numbers)); // Output: 6
```

In Array Literals<br>
Combines arrays or adds elements to an array.
```
const fruits = ['apple', 'banana'];
const moreFruits = ['orange', 'grape', ...fruits];

console.log(moreFruits); // Output: ['orange', 'grape', 'apple', 'banana']
```

In Object Literals<br>
Copies properties from one object to another.
```
const user = { name: 'John', age: 30 };
const updatedUser = { ...user, age: 31 };

console.log(updatedUser); // Output: { name: 'John', age: 31 }
```

Copying Arrays<br>
Creates a shallow copy of an array.
```
const arr = [1, 2, 3];
const arrCopy = [...arr];

console.log(arrCopy); // Output: [1, 2, 3]
```

Concatenating Arrays
```
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combinedArr = [...arr1, ...arr2];

console.log(combinedArr); // Output: [1, 2, 3, 4, 5, 6]
```

Use Cases:

1. Function Arguments: Passing an array of values as individual arguments to a function.
2. Combining or Concatenating Arrays: Easily merge or concatenate multiple arrays without concat().
3. Object Cloning and Merging: Creating copies of objects or merging multiple objects into a new object.
4. Converting Iterables to Arrays: Turning iterable values (like NodeLists or Strings) into arrays to use array methods.
5. React Props or State: Spreading props in React components or merging state objects in a concise manner.

<br><br>

# Short Circuiting

Short circuiting in JavaScript refers to the evaluation logic in boolean expressions, where the expression evaluation can stop early without examining all operands.<br>
This behavior is exploited in logical operations (&& and ||) to execute code conditionally without using if-else statements.

Short circuiting can make code more concise and potentially more efficient by avoiding unnecessary evaluations.<br>
Using short circuiting for conditional assignments or function calls can improve code readability but should be used judiciously to avoid confusion.<br>
Logical operators can be used for conditions beyond simple boolean checks, allowing for creative conditional execution patterns.<br>

Simple video explanations available at:<br>
www.youtube.com/watch?v=O4QKfjh8jJM<br>
www.youtube.com/shorts/CuQtGx9kywY<br><br>

**Logical OR (||)**<br>

The OR operator (||) evaluates expressions from left to right. It returns the value of the first operand that converts to true, or the value of the last operand if all are falsy.<br>

Often used to provide a default value for a variable.<br>

Example:
```
const name = "";
const defaultName = name || "John Doe";
console.log(defaultName); // Output: "John Doe"

// In this example, because name is an empty string (a falsy value), the OR operation short-circuits and defaultName is set to "John Doe".
```
<br><br>

**Logical AND (&&)**<br>

The AND operator (&&) evaluates expressions from left to right. It returns the value of the first operand that converts to false, or the value of the last operand if all are truthy.

Used to execute a statement only if all conditions are true.<br>

Example:
```
const isLogged = true;
const hasPermission = true;
isLogged && hasPermission && console.log("Access granted");

// In this case, "Access granted" is logged because both isLogged and hasPermission are true, so the console.log statement executes.
```

Combining && and ||<br>
Short-circuiting can be combined in various ways to perform complex conditional logic without if-else statements.<br>

Example:
```
const user = null;
const defaultAvatar = "default.jpg";

const avatar = user && user.avatar || defaultAvatar;
console.log(avatar); // Output: "default.jpg"

// Here, if user is null (falsy), the AND (&&) operation short-circuits, and defaultAvatar is used because of the OR (||) operation.
```

Setting Default Values: Use the OR (||) operator to assign default values to variables when the initial value is falsy.
```
const username = user.name || 'Guest';
```

Conditional Execution of Functions: Use the AND (&&) operator to execute functions or expressions only if the preceding condition is true.
```
isLoggedIn && displayDashboard();
```

Guard Clauses in Functions: Prevent execution of a function if certain conditions are not met, reducing nested if statements.
```
function processUser(user) {
  user.isActive && updateUser(user);
}
```

Chaining Optional Properties: Safely access nested properties in objects without causing a TypeError if a property in the chain is undefined or null, using the AND (&&) operator.
```
const streetName = user && user.address && user.address.street;
```

Combining Conditions for Complex Logic: Combine && and || for more complex conditional logic without needing multiple if-else statements.
```
const canEdit = user.isAdmin || (user.isEditor && post.isDraft);
```

<br><br>

# Switch Statements

The switch statement evaluates an expression, matching the expression's value to a case clause, and executes statements associated with that case, as well as statements in cases that follow the matching case.

Switch statements offer a structured way to organize multiple branches of logic based on the value of a single expression, improving readability and maintainability for certain types of conditional logic.

Switch statements can be more readable than if-else if there are many conditions.<br>
Uses strict comparison (===) for matching cases.<br>
Variables declared within a switch block are scoped to the switch block.<br>

Syntax:
```
switch (expression) {
  case value1:
    // Statements executed when the result of expression matches value1
    break;
  case value2:
    // Statements executed when the result of expression matches value2
    break;
  // More cases can be added as needed
  default:
    // Statements executed if none of the cases match the expression
}
```

* expression: The expression whose result is matched against each case clause.
* case value: A label where the program jumps to if the expression matches the case.
* break: Terminates the switch statement; without it, the program continues to the next case.
* default (optional): A clause that will execute if no case matches. It's not mandatory to have a default clause.

Code Examples:

Basic Example
```
const fruit = 'apple';

switch (fruit) {
  case 'banana':
    console.log('Bananas are $0.5 per pound.');
    break;
  case 'apple':
    console.log('Apples are $0.7 per pound.');
    break;
  case 'avocado':
    console.log('Avocados are $1.5 per pound.');
    break;
  default:
    console.log('Sorry, we are out of ' + fruit + '.');
}

// Output: "Apples are $0.7 per pound."
```

Using Multiple Cases for the Same Code Block
```
const grade = 'B';

switch (grade) {
  case 'A':
  case 'B':
  case 'C':
    console.log('You passed!');
    break;
  case 'D':
  case 'F':
    console.log('You failed.');
    break;
  default:
    console.log('Invalid grade.');
}

// Output: "You passed!"
```


Use Cases:

1. Enumerated Values: Particularly useful when dealing with known, enumerable values (e.g., days of the week).
2. Menu Systems: Handling different user input commands or menu selections.
3. State Management: Managing state transitions in applications or games.

<br><br>

# Array Methods

<br>

## push

The push() method adds one or more elements to the end of an array and returns the new length of the array.

The push() method directly modifies the original array, unlike methods like concat which return a new array.<br>
After adding the elements, push() returns the new length of the array, allowing for immediate checks on the array size.

Can be ued to add any type of element to the array, including strings, numbers, objects, or even other arrays.


Syntax:
```
array.push(element1, element2, ..., elementN)

// element1, element2, ..., elementN: The elements to add to the end of the array.
```

Code Examples
Adding a Single Element
```
const fruits = ['apple', 'banana'];
const newLength = fruits.push('orange');

console.log(fruits);      // Output: ['apple', 'banana', 'orange']
console.log(newLength);   // Output: 3
```

Adding Multiple Elements
```
const numbers = [1, 2, 3];
numbers.push(4, 5);

console.log(numbers); // Output: [1, 2, 3, 4, 5]
```

Using push() in a Function
```
function addElementToEnd(array, element) {
  array.push(element);
  return array;
}

const originalArray = [1, 2, 3];
const resultArray = addElementToEnd(originalArray, 4);

console.log(resultArray); // Output: [1, 2, 3, 4]
```

Use Cases:

1. Dynamic Array Construction: Useful when you need to construct an array dynamically, such as collecting user inputs or processing data in chunks.
2. Stack Implementation: The push() method, combined with pop(), can be used to implement a stack (LIFO - Last In, First Out data structure) in JavaScript.
3. Appending Elements: Quickly append elements to the end of an array without worrying about the current length of the array.

<br><br>

## pop

The pop() method removes the last element from an array and returns that element.<br>
This method allows for efficient removal of the last element and dynamic adjustment of array length.

* No arguments are needed.
* Returns the removed element from the array.
* If the array is empty, undefined is returned.

Syntax:
```
array.pop()
```


Code Examples:

Removing the Last Element
```
const fruits = ['apple', 'banana', 'cherry'];
const removedFruit = fruits.pop();

console.log(fruits);          // Output: ['apple', 'banana']
console.log(removedFruit);    // Output: 'cherry'
```

Using pop() in a Loop
```
const numbers = [1, 2, 3, 4, 5];
while(numbers.length > 0) {
  let removedNumber = numbers.pop();
  console.log(`Removed: ${removedNumber}`);
}

// Output: Removed: 5
//         Removed: 4
//         Removed: 3
//         Removed: 2
//         Removed: 1
```

Empty Array Case
```
const emptyArray = [];
const result = emptyArray.pop();

console.log(result); // Output: undefined
```

Use Cases:

1. Stack Implementation: Just like push(), the pop() method is integral to implementing stack behavior (LIFO - Last In, First Out) in JavaScript arrays.
2. Undo Functionality: In applications where actions are stored sequentially, using pop() can help in implementing undo functionality by removing the most recent action.
3. Processing and Removing Elements: Useful for algorithms that need to process elements from the end of the array and remove them as part of the process.

<br><br>

## unshift

The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.<br>
The unshift() method enables efficient addition of elements at the start of an array and adjusting the array's length and element positions accordingly.

* The unshift() method mutates the original array by adding new elements to its start.
* Existing elements are shifted to a higher index to make room for the new elements.
* Returns the new length of the array after adding the elements.

Syntax:
```
array.unshift(element1, element2, ..., elementN);

// element1, element2, ..., elementN: The elements to add to the beginning of the array.
```

Code Examples:

Adding a Single Element
```
const fruits = ['banana', 'cherry'];
const newLength = fruits.unshift('apple');

console.log(fruits);       // Output: ['apple', 'banana', 'cherry']
console.log(newLength);    // Output: 3
```

Adding Multiple Elements
```
const numbers = [3, 4];
numbers.unshift(1, 2);

console.log(numbers); // Output: [1, 2, 3, 4]
```

Using unshift() in a Queue

While shift() and unshift() can both be used for queue operations, unshift() adds elements to the start, which could be part of a reverse queue operation.
```
const queue = [];
queue.unshift(1); // Add to the queue
queue.unshift(2); // Add to the queue

console.log(queue.pop()); // Process from the end
console.log(queue.pop()); // Process from the end
// Output: 2
// Output: 1
```

Use Cases:

1. Queue Management: Adding new tasks or items to the beginning of a queue, especially in scenarios where the most recent items should be processed first.
2. Prepending Items: Useful for situations where you need to add elements to the start of an array, like when maintaining a list of items in reverse chronological order.
3. Dynamic Data Structures: Manipulating data structures where elements need to be dynamically added to the beginning of an array structure.

<br><br>


## shift

The shift() method removes the first element from an array and returns that removed element.<br>

The shift method mutates the original array by removing its first element.<br>
All remaining elements are shifted to a new index that is one less than their previous index.

* No arguments are required.
* Returns the removed element from the array.
* If the array is empty, it returns undefined.

Syntax:
```
array.shift()
```

Code Examples:

Removing the First Element
```
const fruits = ['apple', 'banana', 'cherry'];
const firstFruit = fruits.shift();

console.log(fruits);         // Output: ['banana', 'cherry']
console.log(firstFruit);     // Output: 'apple'
```

Iterating and Removing Elements
```
const numbers = [1, 2, 3, 4, 5];
while(numbers.length) {
  let removedNumber = numbers.shift();
  console.log(`Removed: ${removedNumber}`);
}

// Output: Removed: 1
//         Removed: 2
//         Removed: 3
//         Removed: 4
//         Removed: 5
```

Empty Array Case
```
const emptyArray = [];
const result = emptyArray.shift();

console.log(result); // Output: undefined
```

Use Cases:
1. Queue Implementation: The shift() method is used to implement queue behavior (FIFO - First In, First Out) in JavaScript arrays, especially in combination with push() to add new elements to the end of the queue.
2. Processing Tasks: Useful in scenarios where tasks or items need to be processed in the order they were added.
3. Sequential Data Handling: For managing sequential data where the oldest data (first added) needs to be processed or removed first.

<br><br>

## includes

The .includes() method in JavaScript is used to determine whether an array or string contains a specific element or substring, returning true if it does, and false otherwise.

The includes method can also take a second optional parameter fromIndex, The position within the array or string at which to begin the search. Default is 0.

The includes method is case-sensitive.

Syntax:
```
array.includes(searchElement);
string.includes(searchString);

// Or using the optional fromIndex parameter:

array.includes(searchElement, fromIndex);
string.includes(searchString, fromIndex);
```

Examples:
```
let fruits = ["apple", "banana", "mango"];
fruits.includes("banana");  // returns: true
fruits.includes("grape");   // returns: false
fruits.includes("apple", 1); // returns: false (search starts at index 1)
```

```
let sentence = "Hello, world!";
sentence.includes("world");  // returns: true
sentence.includes("World");  // returns: false (due to case-sensitive)
sentence.includes("o", 5);   // returns: false (position starts at index 5)
```


Use Cases:

1. Quickly checking for the presence of an element within an array, which is especially useful for arrays of primitive values where the goal is to verify inclusion without needing the item's index.
2. Checking if a specific word or character sequence is present within a string, useful for form validations or conditionally rendering UI elements based on textual content.
3. In combination with array .filter() method, .includes() can be used to create a subset of an array based on the presence of specific elements or characters, aiding in data processing and manipulation tasks.
4. Conditional Logic, Employing .includes() in if statements or ternary operators to execute code based on the presence of certain values in strings or arrays.
5. Feature Detection, Determining if a string (like a user agent string) includes a certain substring indicating the presence of a feature, capability, or browser.

<br><br>

## join

The .join() method is used to join all elements of an array (or an array-like object) into a string.

This method takes a separator as an optional parameter, which is used to specify what character or string should be used to separate the array elements in the resulting string.

If no separator is specified, a comma (,) is used by default. It's important to note that .join() does not mutate the original array but returns a new string.

```
const names = ['Jack', 'Joan', 'Sam', 'Shane', 'Glory', 'Anton', 'Piper'];

// Joining with default separator
const nameString = names.join();
console.log(nameString); // Output: "Jack,Joan,Sam,Shane,Glory,Anton,Piper"

// Joining with a custom separator
const nameStringWithSpace = names.join(', ');
console.log(nameStringWithSpace); // Output: "Jack, Joan, Sam, Shane, Glory, Anton, Piper"

// Joining with a custom separator (' and ')
const nameStringWithAnd = names.join(' and ');
console.log(nameStringWithAnd); // Output: "Jack and Joan and Sam and Shane and Glory and Anton and Piper"

// Joining with an empty string as separator
const nameStringNoSpace = names.join('');
console.log(nameStringNoSpace); // Output: "JackJoanSamShaneGloryAntonPiper"
```


Use Cases:

1. Array to String Conversion: The most straightforward use of .join() is to convert an array of elements into a single string. This can be useful for displaying array data in UIs, logs, or converting data for further processing.
2. Joining with Different Separators: Beyond commas, .join() can use different separators to suit various formats or visual styles. This flexibility allows for creative uses such as creating space-separated lists, dash-separated slugs, etc.
3. Reverse Engineering Strings: When used in conjunction with the .split() method, .join() can reverse strings or reorder the elements of a string based on specific logic.
4. Path Construction: For web development, .join() can be helpful in dynamically constructing URLs or file paths without worrying about missing or double slashes.
5. Creating CSV Strings: .join() can be used to generate CSV (Comma-Separated Values) strings from an array of data. This is particularly useful when you're trying to export data to a CSV file format.

<br><br>

## filter

The filter() method creates a new array filled with elements that pass a test provided by a given function. The original array remains unchanged.

The filter() function runs a conditional expression against each entry in an array. If this conditional evaluates to true, the element is added to the output array. If the condition fails, the element is not added to the output array.

The original array remains unchanged.

The filter callback function can take in 3 arguments:
1. element - The current element being processed in the array.
2. index - The index of the current element being processed in the array
3. array - The array filter() was called upon
```
myArray.filter((element, index, array) => {
    // Add filtering logic here
});
```

Its common to use it with only the element argument like below:
```
myArray.filter((element) => {
    // Add filtering logic here
});
```

Example:

```
const numbers = [20, 40, 17, 99, 59, 77];
const filteredNumbers = numbers.filter((number) => {
    return number > 20;
});

console.log(filteredNumbers);  // [40,99,59,77]
```

The above code can be refactored to use JavaScripts single line implicit return syntax:

```
const numbers = [20, 40, 17, 99, 59, 77];
const filteredNumbers = numbers.filter((number) => number > 20);

console.log(filteredNumbers); // [40, 99, 59, 77]
```

We can also filter an array of objects based on a specific property of each object.

For example: Suppose we have an array of objects, each representing a person with name and age properties.
We want to filter this array to include only people over a certain age, say 18.

```
let people = [
    { name: 'Alice', age: 25 },
    { name: 'Bob', age: 17 },
    { name: 'Charlie', age: 30 }
];

let adults = people.filter(person => person.age >= 18);

console.log(adults);  // [{ name: 'Alice', age: 25 }, { name: 'Charlie', age: 30 }]
```


It's important to note that the callback function for filter can be declared separately and then passed as an argument to filter. For example:

```
// Separate callback function to identify even numbers
const isEven = number => number % 2 === 0;

// Array of numbers
const numbers = [1, 2, 3, 4, 5, 6];

// Using the separate callback function with filter
const evenNumbers = numbers.filter(isEven);

console.log(evenNumbers); // Output: [2, 4, 6]
```

* When using the filter() method in JavaScript, it's important to remember that while it returns a new array, the objects within that array are shallow copies; they are the same references as in the original array. This means modifications to the objects in the filtered array will affect the objects in the original array and vice versa if those objects are not primitive types (e.g., numbers, strings) but are instead reference types (e.g., objects, arrays). This behavior can lead to unintended side effects.

Use Cases:

1. Filtering Based on Conditions: Sift through an array and extract elements that meet specific criteria. For example, filtering a list of numbers to include only the ones greater than a certain value.
2. Searching or Filtering in Arrays of Objects: .filter() is particularly useful when dealing with arrays of objects. You can use it to find objects that match certain search criteria, such as all users who are older than 18, or all products in a specific category.
3. Removing Unwanted Values: The .filter() method can efficiently remove unwanted values from an array, such as falsy values (undefined, null, 0, false, NaN, and the empty string "") by setting a condition that only truthy elements pass.
4. Data Manipulation and Analysis: In data processing and analysis tasks, .filter() can be used to preprocess data by removing outliers or filtering data sets down to a more manageable size based on specific conditions before further analysis.
5. Combining with Other Array Methods for Complex Operations: .filter() is often used in conjunction with other array methods like .map(), .reduce(), and .sort() to perform complex data manipulation and retrieval operations. For instance, you might filter an array to get a subset of elements and then map over that subset to transform it, or you might filter an array before reducing it to a single value based on the filtered results.

<br><br>

## map

The .map() method creates a new array populated with the results of calling a provided function on every element in the calling array.

It is a Non-mutating Method: .map() does not change the original array but instead returns a new array.

If you don't need to create / return a new array the [.forEach() method](#foreach) is most likely more approriate to use.

Array Length Preserved: The returned array will have the same length as the input array, but with transformed elements.

The map callback function can take in 3 arguments:
1. element - The current element being processed in the array.
2. index - The index of the current element being processed in the array
3. array - The array map() was called upon
```
myArray.map((element, index, array) => {
    // Add mapping / element changing logic here
});
```

Its common to use it with only the element argument for example:

Transforming Array Values: Convert all elements in an array to a different format or type.
```
const numbers = [1, 2, 3, 4];
const squares = numbers.map(number => number * number);
console.log(squares); // Output: [1, 4, 9, 16]
```

Extracting Data from Array of Objects: Extract specific properties from each object in an array.
```
const users = [{id: 1, name: 'Alice'}, {id: 2, name: 'Bob'}];
const names = users.map(user => user.name);
console.log(names); // Output: ['Alice', 'Bob']
```

Parsing Integer from Array of Strings: Convert an array of strings to integers.
```
const stringNumbers = ['1', '2', '3'];
const integers = stringNumbers.map(Number);
console.log(integers); // Output: [1, 2, 3]
```

Applying a Function to Elements: Apply a function to each element in the array without affecting the original array.
```
const lengths = ['Bilbo', 'Gandalf', 'Nazgul'].map(item => item.length);
console.log(lengths); // Output: [5, 7, 6]
```

Using the second optional "index" parameter (So we can use it in the returned array)
```
// Convert these Miles to KM!
const distanceWalkedMilesArr = [140, 153, 161, 153, 128, 148];

const conversionFactorMilesToKm = 1.6;

const distanceWalkedKmArr = distanceWalkedMilesArr.map((distanceMiles, index) => {
    return `Month ${index}: ${distanceMiles * conversionFactorMilesToKm}KM`;
})

console.log(distanceWalkedKmArr);  Output: // ["Month 0: 224KM", "Month 1: 244.8KM", "Month 2: 257.6KM", "Month 3: 244.8KM", "Month 4: 204.8KM", "Month 5: 236.8KM"]
```

Combining .map() with Other Methods: It's common to chain .map() with other array methods like .filter() to perform complex transformations and calculations.
```
const products = [
  { name: 'laptop', price: 1000 },
  { name: 'phone', price: 500 },
  { name: 'tablet', price: 700 },
];

const discountedPrices = products.map(product => product.price * 0.9);
console.log(discountedPrices); // Output: [900, 450, 630]
```

* It's important to note that the callback function for map can be declared separately and then passed as an argument to map.

Use Cases:

1. Transforming Array Elements: Applying a function to each element in an array to create a new array with the transformed elements.
2. Converting Data Types: Changing the data type of each element in an array, such as converting strings to numbers or vice versa.
3. Extracting Properties: Creating an array that contains a specific property value from each object in an array of objects.
4. Adding or Modifying Object Properties: Generating a new array of objects by adding new properties or modifying existing ones in each object of an array.
5. Data Processing for Visual Representation: Preparing data for visual representation, such as charting, by transforming numerical values or aggregating information.

<br><br>

## forEach

The forEach method is an Array method that provides a simple way to iterate over the elements of an array,<br>
providing a clear and concise way to operate on each element of an array without the need for traditional loop constructs.<br>
It executes a provided function once for each array element, in order.<br>

Unlike map or filter, it doesn't return a new array and is used for side effects.<br>
If you need to create / return a new array the [.map() method](#map) is most likely more approriate to use.

Syntax:
```
array.forEach(function(currentValue, index, arr), thisValue)
```

* currentValue: The current element being processed in the array.
* index (Optional): The index of the current element being processed.
* arr (Optional): The array forEach was called upon.
* thisValue (Optional): A value to use as this when executing function.
<br><br>

Examples:

Basic Usage<br>
Iterate over an array, printing each element to the console.
```
const fruits = ['apple', 'banana', 'cherry'];
fruits.forEach(function(item) {
  console.log(item);
});
// Output: apple
//         banana
//         cherry
```

Using Arrow Function <br>
An arrow function makes the syntax more concise.
```
const numbers = [1, 2, 3];
numbers.forEach(number => console.log(number * 2));
// Output: 2
//         4
//         6
```

Accessing Index and Array<br>
You can also access the index of the current element and the array itself.
```
const names = ['Alice', 'Bob', 'Charlie'];
names.forEach((name, index, arr) => {
  console.log(`${index + 1}: ${name} (Array length: ${arr.length})`);
});
// Output: 1: Alice (Array length: 3)
//         2: Bob (Array length: 3)
//         3: Charlie (Array length: 3)
```

Use Cases:
1. Iterating Over Elements: To perform operations on each item of an array, such as logging to the console or appending to a DOM element.
2. Database Operations: Applying functions to each item of an array fetched from a database, like transforming data shapes or values.
3. Asynchronous Operations: Executing asynchronous operations in a loop, such as sending API requests for each item in an array (though map with Promise.all might be better for handling asynchronous results).
4. Data Manipulation: Modifying the elements of an array in place, for example, adding properties to objects in an array.
5. Side Effects: Performing operations that have side effects, such as updating the UI or logging to an external service, for each item in the array.

<br><br>

## reduce

The reduce() method executes a reducer function on each element of the array, resulting in a single output value.<br>
It's designed to accumulate the array's elements into a single value, using a function that is applied to each element in sequence and carries forward the cumulative result.


The reduce method is versatile, It can be used for more than just arithmetic operations, Its suitable for transforming arrays into any aggregated form.<br>
It always returns a single value, even if that value is an array or object.<br>
Providing an initial value is optional but recommended as it ensures the method behaves predictably for empty arrays or arrays with a single element.<br>
[Click Here to see a great explanation from Web Dev Simplified on youtube](https://www.youtube.com/watch?v=s1XVfm5mIuU)<br>

Syntax:
```
array.reduce(function(accumulator, currentValue, currentIndex, array), initialValue);
```
* accumulator: The accumulated value previously returned in the last invocation of the callback, or initialValue, if supplied.
* currentValue: The current element being processed in the array.
* currentIndex (Optional): The index of the current element being processed in the array.
* array (Optional): The array reduce() was called upon.
* initialValue (Optional): A value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used as the initial accumulator value, and currentValue will start from the second element.<br><br>

Code Examples:

Summing an Array of Numbers
```
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, current) => acc + current, 0);

console.log(sum); // Output: 10
```

Flattening an Array of Arrays
```
const arrays = [[1, 2], [3, 4], [5, 6]];
const flat = arrays.reduce((acc, array) => acc.concat(array), []);

console.log(flat); // Output: [1, 2, 3, 4, 5, 6]
```

Object Counting<br>
A common use case is to use reduce() to count the occurrences of items in an array and produce an object as a result:
```
const fruits = ['apple', 'banana', 'apple', 'orange', 'banana'];
const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});

console.log(count); // Output: { apple: 2, banana: 2, orange: 1 }
```

Aggregating data from an array of objects.<br>
In this example (calculating the total cost of all items in the array)
```
const itemsToBuy = [
  {
    item: 'text books',
    cost: 100
  },
  {
    item: 'laptop',
    cost: 500
  },
  {
    item: 'iphone 12',
    cost: 400
  },
]

const totalSavingsReq = itemsToBuy.reduce((acc, current) => acc + current.cost, 0); // Initial value of the accumulator is set to 0, to ensure acc starts with a value of 0 not an object.

console.log(totalSavingsReq)  // Output: 1000
```

Use Cases:

1. Aggregation: Summing up numbers, concatenating strings, or accumulating values into a single output.
2. Data Transformation: Transforming an array of objects into a different structure, like a keyed object map.
3. Flattening Arrays: Combining nested arrays into a single array.
4. Counting Instances: Counting the occurrences of values in an array.
5. Pipeline: Executing a sequence of functions on an initial value where each function's output is the next function's input.

<br><br>

## slice

The slice() method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) without modifying the original array.

The slice() method does not alter the original array, making it useful for creating new arrays based on existing ones without side effects.<br>
Creates a [Shallow Copy](#shallow-copy-vs-deep-copy) : Elements of the original array are copied as references if they are objects, meaning that if the objects are modified, those changes will be reflected in both the original and new array.

Syntax
```
array.slice(start, end)
```

* start (Optional): Zero-based index at which to start extraction. A negative index can be used, indicating an offset from the end of the sequence. If omitted, slice begins from index 0.
* end (Optional): Zero-based index before which to end extraction. slice extracts up to but not including end. A negative index can be used, indicating an offset from the end of the sequence. If omitted, slice extracts through the end of the sequence (array.length). <br><br>

Code Examples:

Extracting a Portion of an Array
```
const fruits = ['apple', 'banana', 'cherry', 'date'];
const citrus = fruits.slice(1, 3);

console.log(citrus); // Output: ['banana', 'cherry']
```

Using Negative Indices
```
const numbers = [1, 2, 3, 4, 5];
const lastThree = numbers.slice(-3);

console.log(lastThree); // Output: [3, 4, 5]
```

Copying an Array
```
const original = [1, 2, 3];
const copy = original.slice();

console.log(copy); // Output: [1, 2, 3]
```

Using slice() in Function Arguments
```
function list() {
  return Array.prototype.slice.call(arguments);
}

const list1 = list(1, 2, 3); // Creates a new array [1, 2, 3]
console.log(list1); // Output: [1, 2, 3]
```

Use Cases:

1. Creating Subarrays: Extracting specific portions of an array for processing or display.
2. Copying Arrays: Making a shallow copy of an array to avoid mutating the original array when performing operations.
3. Arguments Object: Converting the arguments object into a real array in functions that use variadic arguments.
4. Pagination: Displaying a subset of data by slicing the data array based on pagination parameters.


<br><br>

## splice

The splice() method in JavaScript is used to change the contents of an array by removing, replacing, or adding new elements.<br>
This method directly modifies the original array and can serve multiple purposes: deletion, insertion, and replacement of elements within an array.

The splice method returns an array containing the deleted elements. If no elements are removed, it returns an empty array.

The length of the array is automatically updated based on the operation performed.

* If you instead want to access part of an array without modifying it, use the [Slice() method](#slice)
<br><br>

Syntax:
```
array.splice(start, deleteCount, item1, item2);
```

* start: The index at which to start changing the array. If negative, it indicates an offset from the end of the array.
* deleteCount (Optional): The number of elements to remove from the start index. If omitted, all elements from the start to the end of the array will be removed.
* item1, item2, (Optional): Elements to add to the array, starting from the start index.

<br>

Code Examples:

Removing Elements
```
const fruits = ['apple', 'banana', 'cherry', 'dates'];
const removed = fruits.splice(1, 2); // Removes 'banana' and 'cherry'

console.log(fruits); // Output: ['apple', 'dates']
console.log(removed); // Output: ['banana', 'cherry']  (returning the elements what were removed from fruits arr during the function call to splice)
```

Adding Elements
```
const colors = ['red', 'blue'];
colors.splice(1, 0, 'green', 'yellow'); // Adds 'green' and 'yellow' at index 1

console.log(colors); // Output: ['red', 'green', 'yellow', 'blue']
```

Replacing Elements
```
const scores = [1, 2, 3, 4, 5];
scores.splice(2, 2, 99, 100); // Replaces elements at indexes 2 and 3 with 99 and 100

console.log(scores); // Output: [1, 2, 99, 100, 5]
```

Use Cases:
1. Dynamically Modifying Arrays: Ideal for scenarios where you need to dynamically adjust the contents of an array based on application logic, such as managing items in a list.
2. Managing Data Sets: Useful for adding, removing, or replacing items in a data set, such as updating a list of users or products.
3. Array Manipulation: Employed in complex array manipulations where direct and in-place modification of the array is required.

<br><br>

# Classes

Classes are a template for creating objects. They encapsulate data with code to work on that data.<br>
ES6 introduced classes to JavaScript as a syntactic sugar over the existing prototype-based inheritance, providing a clearer and more traditional syntax for creating objects and dealing with inheritance.<br>

Classes in JavaScript provide a structured framework for implementing object-oriented programming (OOP) principles, such as encapsulation, inheritance, and polymorphism, facilitating the creation of more organized and manageable code.<br>

Key Features:<br>
* Simpler Syntax for Constructors: Classes provide a straightforward syntax for defining constructor functions and initializing new objects.<br>
* Method Definition: No need to use the function keyword when defining methods inside a class.<br>
* Inheritance: Classes make inheritance easier to implement and understand, using the extends and super keywords.<br>
* Static Methods: Methods that are relevant to the class itself, not to the instances of the class, can be defined using the static keyword.<br>

Key Points:<br>
* Syntactic Sugar: Classes do not introduce a new object-oriented inheritance model to JavaScript. They are primarily syntactic sugar over the existing prototype-based inheritance.<br>
* Extends: The extends keyword is used in class declarations or class expressions to create a class as a child of another class.<br>
* Static Methods: Static methods are called without instantiating their class and cannot be called through a class instance.<br>
<br>



Syntax:
```
class ClassName {
  constructor(/* arguments */) {
    // initialization
  }

  method1(/* arguments */) {
    // body
  }

  static staticMethod1(/* arguments */) {
    // body
  }
}
```
<br>

Code Examples:<br>

Defining and Using a Class:
```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  introduce() {
    console.log(`My name is ${this.name}, and I am ${this.age} years old.`);
  }
}

const person1 = new Person('Alice', 30);
person1.introduce(); // Output: My name is Alice, and I am 30 years old.
```

Inheritance
```
class Employee extends Person {
  constructor(name, age, position) {
    super(name, age); // Call the parent class constructor
    this.position = position;
  }

  describe() {
    console.log(`${this.name} works as a ${this.position}.`);
  }
}

const employee1 = new Employee('Bob', 25, 'Developer');
employee1.introduce(); // Inherits method from Person
employee1.describe(); // Output: Bob works as a Developer.
```

Static Methods
```
class Utility {
  static randomNumber() {
    return Math.floor(Math.random() * 100);
  }
}

console.log(Utility.randomNumber()); // Outputs a random number
```


Use Cases:
1. Object-Oriented Programming: For implementing encapsulation, inheritance, and polymorphism in complex applications.
2. UI Components: In frameworks like React for creating and managing reusable UI elements with state and behavior.
3. Data Models: To define the structure and methods for data entities, facilitating interactions with databases.
4. Business Logic: For organizing and encapsulating application-specific logic and operations.
5. Framework Extensions: To extend or customize functionalities in libraries and frameworks through inheritance.

<br><br>

# Advanced Console Methods

The console object in JavaScript is most commonly used with console.log for debugging purposes.<br>
However, it offers a variety of other methods that can greatly enhance debugging sessions and provide more structured and informative outputs.<br>

Here are some lesser-known yet cool console methods that can significantly improve your debugging experience by providing more context, structure, and detail to your console output.
<br>

console.table()<br>
This method displays tabular data as a table. It can be very handy when you need to visualize arrays or objects in a structured format.

```
const people = [
  { name: 'John', age: 30 },
  { name: 'Jane', age: 25 }
];

console.table(people);
```

console.assert()<br>
This method writes an error message to the console if the assertion is false. If the assertion is true, nothing happens. It's useful for testing invariants within your code.
```
console.assert(1 === 2, 'Assertion failed: 1 is not equal to 2');
```

console.warn() and console.error()<br>
These methods output warning and error messages to the console. They can help differentiate between normal log messages, warnings, and errors.
```
console.warn('This is a warning');

console.error('This is an error');
```

console.time() and console.timeEnd()<br>
These methods help you measure how long an operation takes. You start a timer with console.time() and end it with console.timeEnd(), passing the same label to both. The console then logs the time elapsed.
```
console.time('Array initialization');
let arr = new Array(1000000).fill(0);
console.timeEnd('Array initialization');
```

console.group() and console.groupEnd()<br>
These methods allow you to group related messages together. You can nest groups and collapse or expand them in the console to better organize the output.
```
console.group('Fruit Details');
console.log('Name: Apple');
console.log('Color: Red');
console.groupEnd();

console.group('Vehicle Details');
console.log('Type: Car');
console.log('Color: Blue');
console.groupEnd();
```

console.count()<br>
This method logs the number of times it has been called with a particular label. It's useful for counting occurrences or ensuring a piece of code has run a certain number of times.
```
console.count('Loop');
console.count('Loop');
console.countReset('Loop'); // Resets the counter
console.count('Loop');
```

console.dir()<br>
This method displays an interactive list of the properties of a specified JavaScript object. This can be helpful for inspecting objects in detail.
```
const obj = { a: 1, b: 'Hello' };

console.dir(obj);
```

console.trace()<br>
This method outputs a stack trace to the console, showing how the code ended up at a certain point. It's helpful for debugging by tracing function calls.
```
function firstFunction() {
  secondFunction();
}

function secondFunction() {
  console.trace('Trace');
}

firstFunction();
```

## Using CSS properties with console.log()

Using CSS properties with console.log() in JavaScript can add a visual enhancement to your log messages, making them more noticeable and easier to differentiate from other messages in the console.<br>
Whether you're using it to highlight errors, categorize logs, or simply make your console output more engaging, it's a useful technique to have in your JavaScript debugging toolkit.

To apply CSS styles to your console messages, follow this syntax:

```
console.log('%cYour message', 'CSS-properties');

// Replace 'Your message' with the text you want to log, and 'CSS-properties' with the CSS styles you want to apply. The CSS properties should be written in the same string syntax you would use in a stylesheet.
```

Code Examples:

Here's a simple example to change the color and font-size of the message:
```
console.log('%cThis is a styled message', 'color: blue; font-size:20px');
```

Multiple Styles<br>
You can apply multiple styles within the same console.log() by including additional %c directives and corresponding style strings:<br>
```
console.log('%cMessage part 1 %cMessage part 2', 'color: red;', 'color: green; font-weight: bold;');

// This will output "Message part 1" in red, and "Message part 2" in green and bold.
```

Use Cases:

1. Highlighting Important Logs: Make critical messages stand out with bold text or distinctive colors.<br>
2. Categorizing Logs: Use different colors or styles for logs of different levels (info, warning, error) or parts of an application.<br>
3. Enhancing Readability: Apply styles like background-color, padding, or border to make complex log messages more readable.<br>

<br><br>

# Code Snippets

### Generate A Random Number
```
// Function to generate a random number within a specified range (inclusive)
const getRandomNumberInRange = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

const randomNumber = getRandomNumberInRange(1, 100);
console.log(`Random number between 1 and 100: ${randomNumber}`);
```

<br><br>

### Generate a Random Boolean - 50% chance of returning true
```
const randomBoolean = Math.random() >= 0.5;
```

<br><br>

### Get The Current Year

* As a number data type (numeric Value):
```
const currentYear = new Date().getFullYear();
```

* As a string data type:
```
const currentYear = new Date().getFullYear().toString();
```
<br><br>

### Enabling Document Edit Mode

```
document.designMode = 'on';
```

Enables the "Design Mode" in the web document, making the entire webpage content editable just like a text field.<br>
This feature is particularly useful for quick editing or testing purposes without needing to modify the HTML code directly through a developer console or editor.<br>
Allows writers or content creators to experiment with different headings, body text, or layouts directly in the browser.

<br><br>

### Copying Text To Clipboard

```
const copyText = (text) => navigator.clipboard.writeText(text);
```

Uses the navigator.clipboard.writeText method to copy text to the user's clipboard, allowing users to easily copy content - commonly implemented to work on a click event on an element or button.

<br><br>

# Helpful JavaScript Developer Tools and Resources

## cdnjs

[cdnjs](https://cdnjs.com/) is a free and open-source Content Delivery Network (CDN) service that hosts a wide range of libraries, plugins, and frameworks related to web development.<br>
It provides developers with an easy and efficient way to include popular JavaScript libraries, CSS frameworks, fonts, and other web resources directly into their web pages.<br>

Reasons to consider using:

1. Free to Use: cdnjs is completely free, making it accessible to projects of all sizes.
2. Implementing libraries from cdnjs is as simple as including a link to the CDN-hosted file in your HTML document. This eliminates the need to download, host, and manage these files on your own server.
3. Wide Library Selection: cdnjs hosts thousands of libraries, including jQuery, Bootstrap, React, Angular, and many others, covering a vast array of functionalities and use cases.
4. In some cases using cdnjs can help improved performance, reduced server load and increased reliability due to the distributed nature of a CDN means that if one server is unavailable, the content can be served from another server without interrupting the user's access to your website.

## uuid

The uuid library, available on GitHub at [uuidjs/uuid](https://github.com/uuidjs/uuid#cdn-builds), can be effortlessly incorporated into your web projects.<br>
This method delivers the uuid library directly to your web pages, facilitating the generation of universally unique identifiers (UUIDs) in your JavaScript applications.<br>

Example Of Use:<br>
// Utilizing the uuidv4() function from the 'uuid' library to generate a unique identifier for a new cafe deal and appending it to the cafeDeals array.
```
import { v4 as uuidv4 } from 'https://jspm.dev/uuid';

const cafeDeals = [
    {
    cafe: 'Quiet Life Cafe',
    meal: 'Coffee and Cake Combo',
    price: 10,
    uuid: '4fb2b6b7-c7ee-4c80-8de1-390e89f43d7f'
    },
];

cafeDeals.push({
    cafe: 'Coffee Shack',
    meal: 'Beef Burger Combo',
    price: 7,
    uuid: uuidv4()
    });


console.log(cafeDeals[1]); // Output: { "cafe": "Coffee Shack", "meal": "Beef Burger Combo", "price": 7, "uuid": "ed3ad93d-2647-4a43-822c-4bfc223d514d" }
```

Reasons to consider using:

1. Free to Use: uuidjs is completely free, making it accessible to projects of all sizes.
2. Ease of Integration: Including uuid via a CDN link directly in your JavaScript simplifies the process of adding unique identifier generation capabilities to your projects without the need to manually download and host the library.
3. Reduced Project Complexity: By leveraging the CDN delivery, you eliminate the need for local library management, streamlining your project's dependencies and setup.
4. Improved Performance: Delivering uuid from a CDN can enhance your application's load times since CDNs are optimized to serve content from the closest location to the user, reducing latency.

<br><br>

# Glossary Programming Terminology

**JavaScript (JS) :** A high-level, dynamic programming language used to create interactive effects within web browsers. It is a core technology of the web, alongside HTML and CSS.

**Variable :** A symbolic name associated with a value and used to store data. In JavaScript, variables are declared using var, let, or const.

**Function :** A block of code designed to perform a particular task. It is executed when "called" (invoked).

**Array :** An ordered collection of items, where each item can be accessed by its index (position in the array).

**Object :** A collection of related data and/or functionality (properties and methods), stored as key-value pairs. Objects are used to model real-world entities and relationships.

**Scope :** The current context of execution where variables, functions, and objects are accessible. JavaScript has both global and local (function) scopes.

**Closure :** A feature where an inner function has access to the outer (enclosing) function’s variables — a scope chain.

**Promise:** An object representing the eventual completion (or failure) of an asynchronous operation and its resulting value.

**Callback Function:** A function passed into another function as an argument and executed at a later time upon an event or the completion of an asynchronous operation.

**Arrow Function:** A shorter syntax for writing functions using =>. Arrow functions do not have their own this, arguments, super, or new.target.

**Asynchronous Programming:** A programming method used to run tasks concurrently without blocking the execution thread, using features like callbacks, promises, and async/await.

**Event Loop:** A JavaScript runtime model that handles executing multiple chunks of code over time, allowing for non-blocking operations.

**DOM (Document Object Model):** A programming interface for web documents. It represents the page so that programs can change the document structure, style, and content.

**Event:** An action or occurrence recognized by software, often triggered by user interactions. JavaScript uses events to perform tasks in web pages.

**JSON (JavaScript Object Notation):** A lightweight data-interchange format, easy for humans to read and write, and for machines to parse and generate.

**Hoisting:** JavaScript's default behavior of moving declarations to the top of the current scope (script or function) before code execution.

**Prototype:** A mechanism by which JavaScript objects inherit features from one another. Every JavaScript object has a prototype property.

**this Keyword:** Refers to the object it belongs to, providing a way to reference the object that is currently calling the function.

**Strict Mode:** A way to opt in to a restricted variant of JavaScript, aiming to catch more errors and providing a cleaner syntax.

**Template Literals:** String literals allowing embedded expressions and multi-line strings, enclosed by backticks (``).

**Module:** A reusable piece of JavaScript code that can be exported from one program and imported for use in another program.

**ECMAScript (ES):** A standardized version of JavaScript. ES6/ES2015 introduced significant changes and improvements to the language.

**Type Coercion:** The automatic or implicit conversion of values from one data type to another (e.g., string to number).

**Truthy and Falsy:** Terms used in JavaScript to describe values that are coerced to true or false in a Boolean context.

**Execution Context:** The environment in which JavaScript code is executed, including everything the JavaScript code has access to at a given time.

**Garbage Collection:** The process of automatically freeing up memory space that is no longer in use or referenced, to prevent memory leaks.

**IIFE (Immediately Invoked Function Expression):** A JavaScript function that runs as soon as it is defined.

**Spread Operator:** Allows an iterable such as an array expression or string to be expanded in places where zero or more arguments or elements are expected.

**Destructuring Assignment:** A JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

**Event Delegation:** A technique for adding event listeners to a parent element instead of adding them to the descendant elements individually.

**CDN (Content Delivery Network):** A distributed network of servers strategically located across different geographical areas, designed to deliver internet content, such as webpages, images, and videos, to users more efficiently. By caching content closer to the user's location, CDNs reduce latency, improve site load times, and enhance user experience. They also provide protection against large surges in traffic and DDoS attacks.

**UUID (Universally Unique Identifier):** A 128-bit number used to uniquely identify information in computer systems. UUIDs are generated through algorithms that ensure a high probability of uniqueness over space and time, making them ideal for identifying objects within distributed systems without significant central coordination. They are commonly represented as 32 hexadecimal digits, displayed in five groups separated by hyphens (e.g., 123e4567-e89b-12d3-a456-426614174000).