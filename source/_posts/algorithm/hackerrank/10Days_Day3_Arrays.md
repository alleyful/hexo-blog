---
title: Day3 Arrays
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-02 21:49:15
---

## Objective

In this challenge, we learn about Arrays. Check out the attached tutorial for more details.

<br/>

## Task

Complete the getSecondLargest function in the editor below. It has one parameter: an array, **nums**, of **n** numbers. The function must find and return the second largest number in **nums**.

<br/>
<!-- more -->
 
## Input Format

Locked stub code in the editor reads the following input from stdin and passes it to the function: 
The first line contains an integer, **n**, denoting the size of the **nums** array. 
The second line contains **n** space-separated numbers describing the elements in **nums**.

<br/>
 
## Constraints
- **1 <= n <= 10**
- **0 <= nums <= 100**, where **nums** is the number at index **i**.
- The numbers in  are not distinct.

<br/>

## Output Format

Return the value of the second largest number in the **nums** array.

<br/>

## Sample Input 0

```
5
2 3 6 6 5
```

<br/>

## Sample Output 0

```
5
```

<br/>

## Explanation

Given the array **nums = [2,3,6,6,5]**, we see that the largest value in the array is **6** and the second largest value is **5**. Thus, we return **5** as our answer.

<br/>

---

### Solution 1

```javascript
function getSecondLargest(nums) {
    // Complete the function
    const max = Math.max(...nums);

    nums = nums.filter(num => num !== max);

    return Math.max(...nums);
}
```

### Solution 2

```javascript
function getSecondLargest(nums) {
    // Complete the function
    let results = nums.sort((a, b) => a - b)
        .filter((el, index, array) => index === array.indexOf(el));

    return results[results.length - 2];
}
```

### Solution 3

```javascript
function getSecondLargest(nums) {
   
    const result = nums.reduce((target, num) => {
        num > target[1] && (
            num > target[0] ? (
                target[1] = target[0],
                target[0] = num
            ) : !(num === target[0]) && (target[1] = num)            
        );

        return target;
    }, [0, 0]);

    return result[1];
}
```

