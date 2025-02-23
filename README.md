# setTimeout and Closures: An Unexpected Log Output

This repository demonstrates a common issue encountered when using `setTimeout` within a loop in JavaScript.  The problem arises from how closures work with variables in loops.

## The Bug

The `bug.js` file contains a function `myFunction` that uses a `for` loop and `setTimeout` to log numbers from 0 to 9 after a 1-second delay.  However, instead of logging 0 to 9, it logs 10 ten times.  This is because the closure created by the `setTimeout` callback doesn't capture the value of `i` at the time it's set, but instead captures a reference to `i`. By the time `setTimeout` executes, the loop has already finished, and `i` has its final value of 10.

## The Solution

The `bugSolution.js` file corrects the issue by using an immediately invoked function expression (IIFE) to create a new scope for `i`.  This ensures that each `setTimeout` callback captures its own copy of `i`'s value, producing the expected output.

## How to Run

1. Clone this repository.
2. Open `bug.js` and `bugSolution.js` in your favorite text editor.
3. Run the code using a JavaScript environment (e.g., Node.js).
   ```bash
   node bug.js  //Incorrect output
   node bugSolution.js //Correct output
   ```

This example demonstrates an important concept in JavaScript closures and highlights the need to be mindful of variable scoping when working with asynchronous operations.