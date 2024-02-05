# JavaScript Notes

Format and style these readme's better
Look up most popular JS array methods on youtube

Data Types

Arrow Syntax:


Single Line Implicit Return:

math functions

functions:

selectors such as getElementById ect

loops, for, for of / forEach + index:

forEach


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


# Shallow Copy vs Deep Copy
A shallow copy of an object creates a new object with the same first-level properties as the original. However, it does not create copies of nested objects; instead, it copies their references. Thus, if you modify a nested object in the copy, the change will also reflect in the original object, and vice versa. Shallow copying is useful when you want to duplicate an object's structure without needing to create independent copies of its internal objects.

A deep copy goes further by duplicating every level of an object, including all nested objects. This means that the copy and the original are completely independent; changes made to deeply nested objects in the copy do not affect the original, and vice versa. Deep copying is essential when you need to work with a truly separate copy of an object without affecting the original, preserving the integrity of nested structures.

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

# Array Functions

<br>

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

# Code Snippets

### Generate A Random Number
```
// Function to generate a random number within a specified range (inclusive)
const getRandomNumberInRange = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

const randomNumber = getRandomNumberInRange(1, 100);
console.log(`Random number between 1 and 100: ${randomNumber}`);
```
