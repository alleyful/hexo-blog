---
title: Day1 Let and Const
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-05-31 23:49:21
---

## Objective

In this challenge, we practice declaring variables using the let and const keywords. Check out the attached tutorial for more details.

<br/>

## Task

1. Declare a constant variable, `PI`, and assign it the value Math.PI. You will not pass this challenge unless the variable is declared as a constant and named PI (uppercase).
2. Read a number, **r**, denoting the radius of a circle from stdin.
3. Use `PI` and **r** to calculate the **area** and **perimeter** of a circle having radius r.
4. Print **area** as the first line of output and print **perimeter** as the second line of output.

<br/>
<!-- more -->

## Input Format

A single integer, **r**, denoting the radius of a circle.

<br/>

## Constraints
- **0 <= r <= 100**
- **r is a floating-point number scaled to at most 3 decimal places.**

<br/>

## Output Format

Print the following two lines:

1. On the first line, print the **area** of the circle having radius **r**.
2. On the second line, print the **perimeter** of the circle having radius **r**.

<br/>

## Sample Input 0

```
2.6
```

<br/>

## Sample Output 0

```
21.237166338267002
16.336281798666924
```

<br/>

## Explanation

Given the radius **r = 2.6**, we calculate the following:
- ![](https://latex.codecogs.com/gif.latex?area&space;=&space;\pi&space;\cdot&space;r^{2}&space;=&space;21.237166338267002)
- ![](https://latex.codecogs.com/gif.latex?perimeter&space;=&space;2\cdot&space;\pi&space;\cdot&space;r&space;=&space;16.336281798666924)
 
We then print **area** as our first line of output and **perimeter** as our second line of output.

<br/>

---

## Solution

```javascript
function main() {
    let r = parseFloat(readLine());
    let PI = Math.PI;
    
    console.log(PI * r * r);
    console.log(PI * 2 * r);

    try {    
        PI = 0;
        console.log(PI);
    } catch(error) {
        console.error("You correctly declared 'PI' as a constant.");
    }
}
```

