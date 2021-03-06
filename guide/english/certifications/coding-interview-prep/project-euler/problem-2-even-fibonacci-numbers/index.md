---
title: Even Fibonacci Numbers
---
# Problem 2: Even Fibonacci Numbers

---
## Problem Explanation
- A fibonacci sequence is a sequence where `fib(n) = fib(n-1) + fib(n-1)`.
- In this challenge we have to sum all the even numbers upto `nth` term in the sequence.
- Example for `fiboEvenSum(10)`:
  + The sequence till 10th term is:
  1, 2, 3, 5, 8, 13, 21, 34, 55, 89

  + Sum of all even number in the above sequence is:
  2 + 8 + 34 = 44

#### Relevant Links
- [Wikipedia](https://en.wikipedia.org/wiki/Fibonacci_number)


---
## Solutions

<details><summary>Solution 1 (Click to Show/Hide)</summary>

Iterative
```js
function fiboEvenSum(n) {
  let first = 1,
    second = 2,
    sum = 2,
    fibNum; // declaring and initializing variables
  if (n <= 1) return sum; // edge case
  for (let i = 3; i <= n; i++) {
    // looping till n
    fibNum = first + second; // getting the ith fibonacci number
    first = second;
    second = fibNum;
    if (fibNum % 2 == 0) sum += fibNum; // If even add to the sum variable
  }
  return sum;
}
```
</details>

<details><summary>Solution 2 (Click to Show/Hide)</summary>

Recursive
```js
// We use memoization technique to save ith fibonacci number to the fib array
function fiboEvenSum(n) {
  const fib = [1, 1, 2];
  let sumEven = fib[2];
  function fibonacci(n) {
    if (n <= 1) return fib[n];
    // base condition
    else if (fib[n]) return fib[n];
    // if the number exists in the array we cache it and return
    else {
      fib[n] = fibonacci(n - 1) + fibonacci(n - 2); // otherwise calculcate and save it to the array
      if (fib[n] % 2 == 0) sumEven += fib[n]; //if the number is even, add it to the sumEven variable
      return fib[n];
    }
  }
  fibonacci(n); // run the recursive function
  return sumEven;
}
```
</details>


