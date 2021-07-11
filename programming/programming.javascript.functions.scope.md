---
id: d4cb4ba7-5cf8-4e05-96ae-e0e238da53e7
title: Scope
desc: ""
updated: 1621708978574
created: 1621708963632
---

## Global Scope

Context created and execution time.

## Execution context

Depending where we are calling our function it will have an scope called `execution context` that is pushed onto the `callstack` and will be deleted when there a `return` statement or a closing bracket `}`

## Lexical Scope

Is it said when an `execution context` can access to the variables that are defined in the `calling context`

## Clousure

Is a technique that store all the variables of the `enclosing scope` when a function is created.

```javascript
function incrementer() {
  var counter = 0;

  return function () {
    counter++;
    console.log("counter: " + counter);
  };
}

var func = incrementer();

func(); // counter: 1
func(); // counter: 2
```
