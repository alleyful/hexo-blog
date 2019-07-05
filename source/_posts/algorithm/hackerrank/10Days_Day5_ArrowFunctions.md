---
title: Day5 Arrow Functions
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-04 19:25:07
---

## Objective

In this challenge, we practice using arrow functions. Check the attached tutorial for more details.

<br/>

## Task

Complete the function in the editor. It has one parameter: an array, **nums**. It must iterate through the array performing one of the following actions on each element:

- If the element is even, multiply the element by **2**.
- If the element is odd, multiply the element by **3**.

The function must then return the modified array.

<br/>
<!-- more -->

## Input Format

The first line contains an integer, **n**, denoting the size of **nums**. <br/>
The second line contains **n** space-separated integers describing the respective elements of **nums**.

<br/>

## Constraints
- **1 <= n <= 10**
- 1 <= **nums[i]** <= 100, where **nums[i]** is the **ith** element of **nums**.

<br/>

## Output Format

Return the modified array where every even element is doubled and every odd element is tripled.

<br/>

## Sample Input 0
```
5
1 2 3 4 5
```

<br/>

## Sample Output 0
```
3 4 9 8 15
```

<br/>

## Explanation 0

Given **nums = [1,2,3,4,5]**, we modify each element so that all even elements are multiplied by **2** and all odd elements are multipled by **3**. In other words, **[1,2,3,4,5] => [1*3,2*2*,3*3*,4*2,5*3] -> [3,4,9,8,15]**. We then return the modified array as our answer.

<br/>

---

### Solution 1

```javascript
/*
 * Modify and return the array so that all even elements are doubled and all odd elements are tripled.
 * 
 * Parameter(s):
 * nums: An array of numbers.
 */
function modifyArray(nums) {
    return (nums || []).map(num => num * (num % 2 === 0 ? 2 : 3));
}
```

### Solution 2

```javascript
function modifyArray(nums) {
    return nums.reduce((target, num) => {
        target.push(
            num % 2 === 0
                ? num * 2
                : num * 3
        );
        return target;
    },[])
}
```