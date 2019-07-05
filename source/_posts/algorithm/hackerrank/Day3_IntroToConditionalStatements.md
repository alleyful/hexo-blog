---
title: Day3 Intro to Conditional Statements
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 30DaysOfCode
tags:
- Algorithm
- HackerRank
date: 2019-06-15 13:01:34
---

## Objective

In this challenge, we're getting started with conditional statements. Check out the Tutorial tab for learning materials and an instructional video!

<br/>
<!-- more -->

## Task

Given an integer, **n**, perform the following conditional actions:

- If **n** is odd, print Weird
- If **n** is even and in the inclusive range of **2** to **5**, print Not Weird
- If **n** is even and in the inclusive range of **6** to **20**, print Weird
- If **n** is even and greater than **20**, print Not Weird

Complete the stub code provided in your editor to print whether or not  is weird.

<br/>

## Input Format

A single line containing a positive integer, **n**.

<br/>

## Constraints
   
- **1 <= n <= 100**

<br/>

## Output Format

Print Weird if the number is weird; otherwise, print Not Weird.

<br/>

## Sample Input 0

```
3
```

<br/>

## Sample Output 0

```
Weird
```
<br/>

## Sample Input 1

```
24
```

<br/>

## Sample Output 1

```
Not Weird
```

<br/>

## Explanation

Sample Case 0: **n = 3**
**n** is odd and odd numbers are weird, so we print Weird.

Sample Case 1: **n = 24**
**n > 20** and **n** is even, so it isn't weird. Thus, we print Not Weird.
 

<br/>
<br/>

---

### Solution 1

```javascript

// Complete the solve function below.
function main() {
    var N = parseInt(readLine());
    
    if(N % 2 == 0) {
        if(N >= 2 && N < 6) {
            console.log('Not Weird');
        } else if(N >= 6 && N <= 20) {
            console.log('Weird');
        } else if(N > 20) {
            console.log('Not Weird');
        }
    } else {
        console.log('Weird');
    }
}

```

### Solution 2

```javascript

// Complete the solve function below.
function main() {
    const N = parseInt(readLine(), 10);
    let result = (N % 2 === 1 || (N % 2 === 0 && N >= 6 && N <= 20)) ? 'Weird' : 'Not Weird';

    console.log(result);
}

```

---