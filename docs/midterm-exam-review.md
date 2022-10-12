# Midterm Written Exam Review


## I. Scope of exam 

- Everything we have covered this semester is "fair game":
  - you should review all of the class notes starting at [week 1](../weekly/)
  - you should review all of the PDFs in myCourses (Powerpoints, HW assignments, and PEs)
  - review  **quiz-practice-2A.pdf**, **midterm-practice-6A.pdf** and **midterm-practice-7B.pdf** 
    - the PDFs for these have all been posted to myCourses, the Week 8 content section

<hr>

##  II. "Cheat Sheet"
- A hand-written 3x5 index card can be created by you and used during the exam
- I will also give you the exact same "cheat sheet" that you received for midterm practice 6A

<hr>

## III. Accommodations
- If you are allowed extra time for exams, contact the accommodations office ASAP to schedule your exam for Friday

<hr>

## IV. Week 1 (and later) - a review of basic programming concepts


### IV-A. Variables
- "named containers for values"
- have *scope* , which is where they are visible in the program
  - *global* scope is when a variable is declared *outside* of a function - with either `var`, `let` or `const`
	- *local* scope is when a variable is declared *inside* of a function - with either `var`, `let` or `const`
	- *block* scope is when a variable is declared *inside* of a *block* (i.e. curly braces `{}`) with either `let` or `const`

**Sample Question (slightly more elaborate version of a question from 2A quiz)**

```js
"use strict";

let score = 1000;
const maxIncrement = 10;


function addToScore(){
  let counter = 0;
  let score = 11;
  score += maxIncrement
  if(true){
    let score = 111;
    score += maxIncrement;
  }
  return score;
}


//console.log(addToScore()); 	// log #1
//console.log(++score); 	// log #2
//console.log(++counter); 	// log #3
//console.log(++maxIncrement); 	// log #4
```

```
1) For the code fragment above, identify which variables and functions are of local scope, and which one are of global scope.

local:

global:

block: 

2) For the code fragment above, indicate the output for each of the console.log() calls above.
If there will be an error associated with the log then write ERROR and the reason why

log #1 - 

log #2 -

log #3 -

log #4 -


3) How will removing the `let` keyword from `let score = 111;` change the output of log #1 and log #2?
```


<hr>

### IV-B. Functions   
  - how to pass a parameter
  - how to return a value
  - how to return "multiple values"
  - giving parameters default values
  
**Sample Question (pretty much right off of the 2A quiz)** 

- *Declare a function named `doubleIt()` that takes 1 argument and returns that value doubled. If no value is given for the argument, it will default to `0`*
- *Now call the function and pass in `10`. Store the returned value in constant named `tenDoubled`*

<hr>

### IV-C. Types

- `String`, `Number`, `Boolean` are called *value* or *primitive* types because they hold simple values (strings of characters, numbers, true/false) and are *immutable* (can't change) 

```js
"use strict";

// declare `score1` as a variable
let score1 = 1000;
// allowed, because `score1` is allowed to store the new value of `1001`
score1 = score1 + 1;

// declare `score2` as a constant
const score2 = 1000;
// NOT allowed, because `score2` is NOT allowed to store the new value of 1001
score2 = score2 + 1;

////////// PRIMITIVE VALUES ARE COPIED "BY VALUE" /////////////
let score3 = score1; // makes its own independent "copy" of `score1`
score3 = score3 + 1; // change `score3` only
console.log("score1:", score1);
console.log("score3:", score3);
```

- Objects and Arrays are called *reference* types - they are copied "by reference" and are *mutable* (i.e. they can be changed)
- They are sometimes called "compound types" because they can hold multiple values of *different types*

```js
const car = {
  "model": "Bronco", // a string
  "cylinders": 6 // a number
};
car.cylinders = 4; // dot notation to assign (set) a new value to a property
console.log(car.model, car.cylinders); // dot notation get values

// square brackets to access the index (aka "offset) and get/set the values
const colors = ["red", "green"];
colors[1] = "yellow";
console.log(colors[1]);
```

- **Reference types behave differently when assigned to variables!**

```js
////////// REFERENCE TYPES ARE COPIED "BY REFERENCE" /////////////
// declare `colors1` as a constant that points at an array
const colors1 = ["red", "green"];
// the following modification to `colors1` is legal because we are not changing what colors1 is pointing at
// which is still the same array object that was created in the system "heap" 
// the "heap" is an area of dynamic memory which can grow
// (this is opposed to where primitive values are stored, which is the "stack", which is fixed size memory that tends to be more temporary)
colors1.push("blue"); 
console.log("colors1:", colors1);

const colors2 = colors1; // `colors2` is pointing at the same array!
colors1.push("yellow");
colors2.push("purple");
console.log("colors1 is now:", colors1);
console.log("colors2 is now:", colors2); // they are pointing at the same thing!
console.log("colors1 === colors2?", colors1 === colors2); // they are pointing at the same thing!

// Now create a new array, with the same contents as the above array that `colors1` and `colors2` are pointing at
const colors3 = ["red", "green", "blue", "yellow", "purple"];
console.log("colors3:", colors3);
console.log("colors1 === colors3?", colors1 === colors3); // they are NOT pointing at the same thing!
console.log("colors2 === colors3?", colors2 === colors3); // they are NOT pointing at the same thing!

// AND this works exactly the same way for object instances!
const obj1 = {};
obj1.make = "Ford";
const obj2 = obj1;

obj1.model = "Bronco";
obj2.cylinders = 6;

console.log("obj1 is now:", obj1);
console.log("obj2 is now:", obj2); // they are pointing at the same thing!
console.log("obj1 === obj2?", obj1 === obj2); // they are pointing at the same thing!

// and so on
// BTW - functions are objects and thus reference types too!


```

<hr>

### IV-D. Comparison Operators and Equality (for value types)

- The JS equality operator - `==` will do a *type conversion** before doing the comparison

```js
// With `==`, JS will convert "0" the String to 0 the Number *before* doing the comparison
console.log('0 == "0"?',0 == "0"); // true, according to this operator! (even though it's really not)
```

- The JS strict equality operator - `===` will first check to see if the operands are of the same *type*, and if they are not it will return `false` and not bother to do the rest of the comparison

```js
// Not the same type!
console.log('0 === "0"?',0 === "0"); // false!
```

<hr>

### IV-E. Type casting and arithmetic operations
- *Type casting refers to changing an variable of one data type into another*

```js
console.log('1 + "1"?',1 + "1"); // string concatenation, not addition like we hoped for!
console.log('1 + Number("1")?',1 + Number("1")); // turn "1" into a number before doing the addition

// the + sign here is a "unary" operator that will also convert a string to a number
// although it's kind of confusing in this situation because of the first `+`
console.log('1 + +"1")?',1 + (+"1")); 

// What happens if we try to multiply (or add, subtract etc) a number to `undefined`?
let car = {make: "Ford"};
let distanceTravelled = 10 * car.speed; // car.speed was never defined
console.log("distanceTravelled:",distanceTravelled); // `NaN` means "Not a Number"
```

<hr>

## V. Other Topics to focus on:

- Carefully reviewing the 3 practice PDFs will prepare you pretty well, but still be sure to review:
  - Classes & Inheritance
  - Object Literals
  - Array operations
  - Loops 
  - `typeof()`




### V-A. Don't worry about:

- Maps, Stacks, Queues, Sets
