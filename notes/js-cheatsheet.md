# Notes

## Variables

+ Undeclared: `a = 8;` **NOT** recommended
+ `var` keyword: `var a = 8;` only use to support older browsers
+ `const` keyword: `const a = 8;` variable cannot be changed. Use for variables where the value or the type should not be changed
+ `let` keyword: `let b = a + 8;` use when variable can change value

## Arithmetic

+ `+` addition
+ `-` subtraction
+ `*` multiplication
+ `**` exponentiation
+ `/` division
+ `%` modulus
+ `++` increment
+ `--` decrement

## If else statement

```js
let a = 5;
if (a > 0) {
    console.log("positive");
} else if (a === 0) {
    console.log("is 0");
} else {
    console.log("negative");
}
```

## Switch statement

```js
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
     day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
}
```

## For loops

```js
for (let i = 0; i < 5; i++) {
    console.log(i)
}
```

## While loops

```js
let i = 0;
while (i < 10) {
    console.log(i);
    i++
}

// do while executes at least once
let i = 10;
do {
    i++;
    console.log(i);
} while (i < 10); // returns 11

```

## Functions

Functions are defined by `function` keyword followed by function name and `()` - optionally with comma-separated paremeters inside parentheses. Functions stop executing immediately after a `return` statement.

```js
function myfunc(a, b) {
    return a * b;
}

console.log(myfunc(5, 4); // returns 20
```

### Scope and local variables

Variables inside functions have local scope

```js
const mynum = 11;

function luckynumber() {
    let mynum = 121;
    return mynum;
}

console.log(luckynumber()); // returns 121
console.log(mynum); // returns 11
```

### Function expressions

```js
const square = function (number) {
  return number * number;
};

console.log(square(4)); // returns 16
```

### Nested functions

```js
function addSquares(a, b) {
  function square(x) {
    return x * x;
  }
  return square(a) + square(b);
}

console.log(addSquares(2, 3)); // returns 13
```

### Anonymous functions

Functions without a name, declared with the `function` keyword and the parameters. They are normally bound to a variable, so that they can be called with variable's name.

```js
const plushundred = (function (a) {
  return a + 100;
});

console.log(plushundred(5));
```

### Arrow functions

Simplified (shorter) form to write anonymous functions.

```js
let x = 5;
let y = 8;

// function with parameters
const doublesum = (a, b) => (a + b) * 2;
doublesum(x, y); // returns 26
doublesum(10, 20); // returms 60

// function without parameters
const double_sum = () => (x + y) * 2;
double_sum(x, y); // returns 26
double_sum(10, 20); // returns 26 again
```

The difference between the examples above is that the equivalent anonymous function in the second case takes no parameters and directly returns a value:

```js
// equivalent to `const doublesum = (a, b) => (a + b) * 2;`
const mydoublesum = (function (a, b) {
  result = (a + b) * 2;
  return result;
});

// equivalent to `const double_sum = () => (a + b) * 2;`
const my_double_sum = (function() {
  return (x + y) * 2;
})
```

## Arrays

```js
const myarr = [11, 5, 8, 1];

const pets = [];
pets[0] = "Cats";
pets[1] = "Dogs";
pets[2] = "Parrots";

const trees = new Array("Pine", "Oak", "Acacia");

const myints = new Int8Array([11, 5, 8, 1]); //typed Array

// Array methods
myarr.sort() // sorts alphabetically: Array(4) [ 1, 11, 5, 8 ]
myints.sort() // typed arrays are sorted by value: Int8Array(4) [ 1, 5, 8, 11 ]
pets.length() // returns 3
pets.reverse(); // Array(3) [ "Parrots", "Dogs", "Cats" ]
trees.join(" - "); // returns "Pine - Oak - Acacia"
trees.pop(); // removes last element: "Acacia"
trees.push("Fig"); // adds element at the end and returns new array length: 3
trees.shift(); // removes first element: "Pine"
trees.unshift("Acacia") // adds element at beginning and returns new array length: 3
trees.splice(2, 0, "Pine"); // add element at index 2, remove 0 elements, element to add
const sometrees = trees.slice(2); // returns new array from index 2 of trees array
                                  // sometrees: Array [ "Pine", "Fig" ]
                                  // original array is not altered

// Searching array methods
// const pets = ["Cats", "Dogs", "Parrots"];
pets.indexOf("Cats"); // returns 0
pets.includes("Dogs"); // returns true
```

### Array manipulation

```js
const numbers = [8, 19, 21, 17, 6, 5, 11];

// forEach()
numbers.forEach((element) => console.log(element));

// map()
const num1 = [1, 4, 9, 16];
const num1_map = num1.map((x) => x * 2);
console.log(num1_map); // Array(4) [ 2, 8, 18, 32 ]

// flatMap()
const mynestednums = [[1, 4], [3, 8], [5, 7]];
const myflatmap = mynestednums.flatMap(x => x.map(y => y * 2));
myflatmap; // Array(6) [ 2, 8, 6, 16, 10, 14 ]

// filter()
const evennumbers = numbers.filter((x) => x % 2 == 0);
console.log(evennumbers); // Array [ 8, 6 ]

const words = ['spray', 'elite', 'exuberant', 'destruction', 'present'];
const longwords = words.filter((word) => word.length > 6);
console.log(longwords); // Array(3) [ "exuberant", "destruction", "present" ]

// reduce()
const x = 0;
const sumnumbers = numbers.reduce((a, b) => a + b, x);
console.log(sumnumbers); // 87

// some() and every()

const iseven = (element) => element % 2 === 0;
console.log(numbers.some(iseven)); // true, at least one element is even
console.log(numbers.every(iseven)); // false, not every element is even
console.log(evennumbers.every(iseven)); // true, numbers array filtered by even

// Array.from()
Array.from("Hello, world!");
// returns: Array(13) [ "H", "e", "l", "l", "o", ",", " ", "w", "o", "r", "l", "d", "!" ]

// find() and findIndex()
const numfind = numbers.find((element) => element > 10); // returns 19
const numfindind = numbers.findIndex((element) => element > 10); // returns 1 (position of 19)
```

## Strings

Strings are *primitive types* in JavaScript. They are immutable (cannot be altered) and can only be passed by value, not by reference (when assigning or manipulating a string, we copy the original string value). Strings are typically defined as collection of characters enclosed in single or double quotes.

Primitive types in JavaScript don't have properties. However, they can be *coerced* to behave as [objects - see below](#objects): the string is wrapped with an object, the property of the object is used and immediately the object gets disposed [stackoverflow](https://stackoverflow.com/a/40331210).

```js
const mystring1 = "A string primitive"
const mystring2 =  = new String("A string object");
```

### String (object) properties

```js
const str1 = "Lorem ipsum dolor sin amet";
console.log(str1.length); //returns 26
```

### String (object) methods

```js
const sentence = 'The quick brown fox jumps over the lazy dog.';
const hi = "Hello World"
const text1 = "Lorem"
const text2 = "Ipsum"

// String.at()
console.log(sentence.at(5)); // returns u, 5th character from beginning
console.log(sentence.at(-4)); // returns d, 4th character from end, starting counting from -1

// String.slice()
console.log(sentence.slice(10)); // returns "brown fox jumps over the lazy dog."
console.log(sentence.slice(10, 19)); // returns "brown fox"
console.log(sentence.slice(-4)); // returns "dog."
console.log(sentence.slice(-10, -5)); // returns "lazy"

// String.substring() - negative values are treated as 0
console.log(sentence.substring(-4, 9)); // returns "The quick"

// String.substr() - second parameter is substring length
console.log(sentence.substr(4, 11)); // returns "quick brown"
console.log(sentence.substr(10, 9)); // returns "brown fox"

// String.toUpperCase() and String.toLowerCase()
console.log(hi.toUpperCase()); // returns "HELLO WORLD"
console.log(hi.toLowerCase()); // returns "hello world"

// String concatenation
console.log(text1 + " " + text2); // returns "Lorem ipsum"
console.log(text1.concat(" ", text2)); // returns "Lorem ipsum"

// Remove whitespace from beginning and end of string
let mytext = "     Hello, world          " ;
console.log(mytext.trim()); // returns "Hello, world"

// Pad string with a character String.pad(total length, character to pad with)
let mynum = "4";
console.log(mynum.padStart(4, 0)); // returns "0004"
console.log(mynum.padEnd(4, 0)); // returns "4000"

console.log(text1.padStart(8,"-").padEnd(11, "-")); // returns "---Lorem---"

// String.split() - to array
console.log(sentence.split(" ")); // returns Array(9) [ "The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog." ]

// String.replace() - case sensitive
console.log(hi.replace("world", "JavaScript")); // returns "Hello World"
console.log(hi.replace("World", "JavaScript")); // returns "Hello JavaScript"

// String.repeat()
console.log(text1.repeat(3)); // returns "LoremLoremLorem"

// String.chatAt() - behaves like String.at()
console.log(sentence.charAt(4)); // returns "q"

// String.charCodeAt() - returns unicode value of char, as long as it is < 65536
console.log(sentence.charCodeAt(4)); // returns 113

// String.codePointAt() - returns unicode value of char
let  str = "𠮷𠮷";
console.log(str.charCodeAt(0)); // returns 55362, which is wrong
console.log(str.codePointAt(0)); // returns 134071 , which is correct

// String.startsWith() and String.endsWith()
console.log(sentence.startsWith("The")); // returns true
console.log(sentence.endsWith("dog")); // returns false
console.log(sentence.endsWith("dog.")); // returns true
```

## Objects

Objects store collections of key-value pairs

```js
const cat = {name: "Miu", color: "Black", age: 2, likes: "fish"}

console.log(cat.age); // returns 2
console.log(cat["color"]); // returns "Black"

// delete an object property
delete cat.likes;
console.log(cat); // returns "Object { name: "Miu", color: "Black", age: 2 }"
```
