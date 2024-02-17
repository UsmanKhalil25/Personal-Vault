### var
- Before the introduction of let and const, var was the primary way to declare variables in JavaScript. The scope of a var variable is either the function in which it is declared (function scope) or the global scope if it's declared outside any function
```js
function example() {
  if (true) {
    var x = 10;
    console.log(x); // Output: 10
  }
  console.log(x); // Output: 10
}

example();
```
- In this example, the variable x is declared using var. It has a function scope, so it is accessible both inside and outside the if block. This behaviour is known as hoisting, where the variable declaration is moved to the top of the function. Therefore, even though x is declared inside the if block, it can still be accessed outside of it.

### let
- let was introduced in ECMAScript 6 (ES6) to address some of the issues with var. The scope of a let variable is limited to the block in which it is declared (block scope), which is typically denoted by a set of curly braces { }.
```js
function example() {
  if (true) {
    let y = 20;
    console.log(y); // Output: 20
  }
  console.log(y); // ReferenceError: y is not defined
}

example();
```
- In this example, the variable y is declared using let. It has block scope, which means it is only accessible within the block it's declared in (inside the if block). When we try to access y outside of the block, we get a ReferenceError because y is not defined in that scope. This behavior helps prevent unintended variable leakage and makes the code easier to understand.
### const
- const is also introduced in ES6 and stands for "constant." Variables declared with const are ==block-scoped, just like let==, but they have an additional characteristic, their value cannot be reassigned once it has been assigned. In other words, const variables are immutable.
```js
function example() {
  const z = 30;
  console.log(z); // Output: 30

  z = 40+z;  // error: assignment to constant variable
  z = 30;    // error: assignment to constant variable
}

example();
```