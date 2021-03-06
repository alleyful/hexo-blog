---
title: Day10 Binary Numbers
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 30DaysOfCode
tags:
- Algorithm
- HackerRank
date: 2019-06-16 01:01:34
---

## Objective

Today, we're working with binary numbers. Check out the Tutorial tab for learning materials and an instructional video!

<br/>

## Task

Given a base-**10** integer, **n**, convert it to binary (base-**2**). Then find and print the base-**10** integer denoting the maximum number of consecutive **1**'s in **n**'s binary representation.

<br/>
<!-- more -->

## Input Format

A single integer, **n**.

<br/>

## Constraints
   
- **1 <= n <= 10<sup>6</sup>**

<br/>

## Output Format

Print a single base-**10** integer denoting the maximum number of consecutive **1**'s in the binary representation of **n**.

<br/>

## Sample Input 1

```
5
```

<br/>

## Sample Output 1

```
1
```

<br/>

## Sample Input 2

```
13
```

<br/>

## Sample Output 2

```
2
```

<br/>

## Explanation

Sample Case 1: 
The binary representation of **5** is **101**, so the maximum number of consecutive **1**'s is **1**.

Sample Case 2: 
The binary representation of **13** is **1101**, so the maximum number of consecutive **1**'s is **2**.

<br/>
<br/>

---


### Solution 1

```javascript
function main() {
    let n = parseInt(readLine(), 10);
    let values = [];

    while (+n != 0) {
        values.push(n % 2);

        n = Math.floor(n / 2);
    }

    let { result } = values.reduce((target, item, index) => {
        item
            ? target['accumulator']++
            : (target['accumulator'] = 0);

        target['accumulator'] > target['result'] && (target['result'] = target['accumulator']);

        return target;
    }, { accumulator: 0, result: 0 });

    console.log(result);
}
```

### Solution 2

```javascript
function main() {
    const n = parseInt(readLine(), 10);
    let result = 0;

    const temp = n.toString(2).split('').reduce((target, num) => {
        let value = Number(num) > 0 ? Number(target) + Number(num) : (
            result = target > result ? target : result,
            0
        );

        return value;

    }, 0);

    console.log(result - temp > 0 ? result : temp)
}
```


### Solution 3

```javascript
function main() {
    const n = parseInt(readLine(), 10);
    const array = n.toString(2).split('');
    let max = 0;
    let cur = 0;

    for (let i = 0, itotal = array.length; i < itotal; i++) {
        if (array[i] == 1) {
            cur++;
        } else if (array[i] == 0) {
            if (cur > max) {
                max = cur;
            }
            cur = 0;
        }
    }

    if (cur > max) {
        max = cur;
    }
    
    console.log(max);
}
```
