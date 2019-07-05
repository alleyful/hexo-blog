---
title: Day5 Template Literals
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-04 23:06:27
---

## Objective

In this challenge, we practice using JavaScript Template Literals. Check the attached tutorial for more details.

<br/>
<!-- more -->

## Task

The code in the editor has a tagged template literal that passes the area and perimeter of a rectangle to a tag function named sides. Recall that the first argument of a tag function is an array of string literals from the template, and the subsequent values are the template's respective expression values.

Complete the function in the editor so that it does the following:

1. Finds the initial values of **s1** and **s2** by plugging the area and perimeter values into the formula:

	![](https://latex.codecogs.com/gif.latex?s=\frac{P\pm&space;\sqrt{P^{2}-16\cdot&space;A}}{4})

	- where **A** is the rectangle's area and **P** is its perimeter.
2. Creates an array consisting of **s1** and **s2** and sorts it in ascending order.
3. Returns the sorted array.

<br/>

## Input Format

The first line contains an integer denoting **s1**. <br/>
The second line contains an integer denoting **s2**.
   
<br/>

## Constraints
   
- **1 <= s1, s2 <= 100**

<br/>

## Output Format
   
Return an array consisting of **s1** and **s2**, sorted in ascending order.

<br/>

## Sample Input 0
```
10
14
```

<br/>

## Sample Output 0
```
10
14
```

<br/>

## Explanation 0
   
The locked code in the editor passes the following arrays to the tag function:

- The value of **literals** is [ 'The area is: ', '.\nThe perimeter is: ', '.' ].
- The value of **expressions** is [ 140, 48 ], where the first value denotes the rectangle's area, **A**, and the second value denotes its perimeter, **P**.

When we plug those values into our formula, we get the following:<br/>

```
s1=
s2=

```

We then store these values in an array, [14, 10], sort the array, and return the sorted array, [10, 14], as our answer.

<br/>

---

### Solution 1

```javascript
/*
 * Determine the original side lengths and return an array:
 * - The first element is the length of the shorter side
 * - The second element is the length of the longer side
 * 
 * Parameter(s):
 * literals: The tagged template literal's array of strings.
 * expressions: The tagged template literal's array of expression values (i.e., [area, perimeter]).
 */
function sides(literals, ...expressions) {
    const [a, p] = expressions;
    const value = Math.sqrt((p ** 2 - (16 * a)));

    return [((p - value) / 4), ((p + value) / 4)];
}

```


### Solution 2

```javascript
function sides(literals, ...expressions) {
    const value = [...expressions]
    const p = value[1];
    const a = value[0];
    let calSqrt = (p, a) => Math.sqrt(Math.pow(p, 2) - (16 * a));

    return value.reduce((target, item, index) => {
        target.push(
            (index % 2 === 0 
                ? p - calSqrt(p, a)
                : p + calSqrt(p, a))/4
        );

        return target;
    },[])   
}

```