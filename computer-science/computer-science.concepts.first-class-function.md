---
id: 28b61d94-259f-4e30-8285-957babc62de2
title: First Class Function
desc: ""
updated: 1621818272191
created: 1621818260946
---

## General Concept

If the programming language use functions as a first-class citizens.

- Pass functions as Arguments to other functions
- Return a function from other one
- Assign a functions into a variable
- Store them into data structure

### First class citizen

Is an entity that supports operations like being passed as an argument, returned from a function, modified, and assigned to a variable

## Example

```javascript
const operationSum = (a, b) => {
  return a + b;
};
const calculate = (a, b, operation) => {
  return () => {
    const answer = operation(a, b);
    return answer;
  };
};

// Execute
const result = calculate(1, 3, operationSum)();
console.log(result);
```
