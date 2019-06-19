---
title: Day7 Arrays
categories:
- Algorithm
- HackerRank
- 30DaysOfCode
tags:
- Algorithm
- HackerRank
date: 2019-06-15 17:01:34
---

## Objective

Today, we're learning about the Array data structure. Check out the Tutorial tab for learning materials and an instructional video!

<br/>

## Task

Given an array, **A**, of **N** integers, print **A**'s elements in reverse order as a single line of space-separated numbers.

<!-- more -->
<br/>

## Input Format

The first line contains an integer, **N** (the size of our array). 
The second line contains **N** space-separated integers describing array **A**'s elements.

<br/>

## Constraints
   
- **1 <= N <= 1000**
- **1 <= A<sub>i</sub> <= 10000**, where **Ai** is the **i<sup>th</sup>** integer in the array.

<br/>

## Output Format

Print the elements of array **A** in reverse order as a single line of space-separated numbers.

<br/>

## Sample Input

```
4
1 4 3 2
```

<br/>

## Sample Output

```
2 3 4 1
```

<br/>
<br/>

---

### Solution 1

```javascript
function main() {
    const n = parseInt(readLine(), 10);

    const arr = readLine().split(' ').map(arrTemp => parseInt(arrTemp, 10));

    console.log(arr.reverse().join(' '));
}
```

### Solution 2

```javascript
function main() {
    const n = parseInt(readLine(), 10);

    const arr = readLine().split(' ').map(arrTemp => parseInt(arrTemp, 10));

    const reverseArray = (array) => {
        let temp = null;
        const length = array.length;
        for (let i = 0; i < length / 2; i++){
            temp = array[i];
            array[i] = array[length - 1 - i];
            array[length - 1 - i] = temp;
        }

        return array;
    };
    console.log(reverseArray(arr).join(' '));
}

```
