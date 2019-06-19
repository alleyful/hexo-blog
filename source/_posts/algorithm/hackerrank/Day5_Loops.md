---
title: Day5 Loops
categories:
- Algorithm
- HackerRank
- 30DaysOfCode
tags:
- Algorithm
- HackerRank
date: 2019-06-15 15:01:34
---

## Objective

In this challenge, we're going to use loops to help us do some simple math. Check out the Tutorial tab to learn more.

<br/>

## Task

Given an integer, **n**, print its first **10** multiples. Each multiple **n x i** (where **1 <= i <= 10**) should be printed on a new line in the form: n x i = result.

<!-- more -->
<br/>

## Input Format

A single integer, **n**.

<br/>

## Constraints
   
- **2 <= n <= 20**

<br/>

## Output Format

Print **10** lines of output; each line **i** (where **1 <= i <= 10**) contains the **result** of **n x i** in the form: 
n x i = result.

<br/>

## Sample Input

```
2
```

<br/>

## Sample Output

```
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
2 x 10 = 20
```

<br/>
<br/>

---

### Solution 1
```javascript
function main() {
    const n = parseInt(readLine(), 10);
    
    for (let i = 1; i <= 10; i++) {
        console.log(`${n} x ${i} = ${n * i}`);
    }
}

```


### Solution 2

```javascript

function main() {
    const n = parseInt(readLine(), 10);

    new Array(10).fill(n).forEach((time, index) => {
        console.log(`${time} x ${index + 1} = ${time * (index + 1)}`);
    });
}

```
