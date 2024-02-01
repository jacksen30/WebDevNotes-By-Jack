# JavaScript Notes

Format and style these readme's better
Look up most popular JS array methods on youtube

Variables:

Arrow Syntax:


Single Line Implicit Return:

math functions
random number function
functions:

selectors such as getElementById ect

loops, for, for of / forEach + index:

includes method

forEach

### Shallow Copy
A shallow copy of an object creates a new object with the same first-level properties as the original. However, it does not create copies of nested objects; instead, it copies their references. Thus, if you modify a nested object in the copy, the change will also reflect in the original object, and vice versa. Shallow copying is useful when you want to duplicate an object's structure without needing to create independent copies of its internal objects.

### Deep Copy
A deep copy goes further by duplicating every level of an object, including all nested objects. This means that the copy and the original are completely independent; changes made to deeply nested objects in the copy do not affect the original, and vice versa. Deep copying is essential when you need to work with a truly separate copy of an object without affecting the original, preserving the integrity of nested structures.


## Array Functions

### filter

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

### map


# Code Snippets

### Generate A Random Number
```
// Function to generate a random number within a specified range (inclusive)
const getRandomNumberInRange = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

const randomNumber = getRandomNumberInRange(1, 100);
console.log(`Random number between 1 and 100: ${randomNumber}`);
```
