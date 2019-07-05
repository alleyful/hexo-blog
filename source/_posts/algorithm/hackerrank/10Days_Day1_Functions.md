---
title: Day1 Functions
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-05-31 22:19:26
---

## Objective

Today, we're discussing JavaScript functions. Check out the attached tutorial for more details.

<br/>

## Task

Implement a function named factorial that has one parameter: an integer, **n**. It must return the value of **n!** (i.e., **n** factorial).

<br/>
<!-- more -->

## Input Format

Locked stub code in the editor reads a single integer, **n**, from stdin and passes it to a function named factorial.

<br/>

## Constraints
- **1 <= n <= 10**

<br/>

## Output Format

The function must return the value of  **n!**.

<br/>

## Sample Input 0

```
4
```

<br/>

## Sample Output 0

```
24
```

<br/>

## Explanation

We return the value of **4! = 4 X 3 X 2 X 1 = 24**.

<br/>

---

### Solution 1

```javascript

const factorial = (n) => (n - 1) > 0 ? n * factorial(n - 1) : 1;

```

### Solution 2

```javascript

let memoization = [0, 1];

const factorial = (n) => {
    (typeof memoization[n] !== 'number') && (
        memoization[n] = (n - 1) > 0 ? n * factorial(n - 1) : 1 
    );

    return memoization[n];
}

```
