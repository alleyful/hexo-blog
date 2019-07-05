---
title: Day9 Recursion 3
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 30DaysOfCode
tags:
- Algorithm
- HackerRank
date: 2019-06-16 00:01:34
---

## Objective

Today, we're learning and practicing an algorithmic concept called Recursion. Check out the Tutorial tab for learning materials and an instructional video!

**Recursive Method for Calculating Factorial**

![Recursive Method for Calculating Factorial](https://latex.codecogs.com/svg.latex?factorial(N)&space;=&space;\begin{cases}&space;1&space;&&space;\text{&space;}&space;N\leq&space;1&space;\\&space;N&space;\times&space;factorial(N&space;-&space;1)&space;&&space;\text{}&space;otherwise&space;\end{cases})

<br/>
<!-- more -->

## Task

Write a factorial function that takes a positive integer, **N** as a parameter and prints the result of **N!** (**N** factorial).

**Note:** If you fail to use recursion or fail to name your recursive function factorial or Factorial, you will get a score of **0**.

<br/>

## Input Format

A single integer, **N** (the argument to pass to factorial).

<br/>

## Constraints
   
- **2 <= N <= 12**
- Your submission must contain a recursive function named factorial.

<br/>

## Output Format

Print a single integer denoting **N!**.

<br/>

## Sample Input

```
3
```

<br/>

## Sample Output

```
6
```
<br/>

## Explanation

Consider the following steps:

1. factorial(3) = 3 X factorial(2)
2. factorial(2) = 2 X factorial(1)
3. factorial(1) = 1

From steps **2** and **3**, we can say **factorial(2) = 2 X 1 = 2**; then when we apply the value from **factorial(2)** to step **1**, we get **factorial(3) = 3 X 2 X 1 = 6**. Thus, we print **6** as our answer.


<br/>
<br/>

---

### Solutions 1

```javascript
function factorial(n) {
    return n < 2 ? 1 : n * factorial(n - 1);
}
```

### Solution 2

```javascript
function factorial(n) {
    return (!+n) ? 1 : n * factorial(n - 1);
}
```

### Solution 3

```javascript
let memoization = [0, 1];

const factorial = (n) => {
    (typeof memoization[n] !== 'number') && (
        memoization[n] = (n - 1) > 0 ? n * factorial(n - 1) : 1 
    );

    return memoization[n];
}
```

