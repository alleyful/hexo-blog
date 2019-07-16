---
title: Birthday Chocolate
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- ProblemSolving
tags:
- Algorithm
- HackerRank
- ProblemSolving
date: 2019-07-16 22:28:51
---
  
  
Lily has a chocolate bar that she wants to share it with Ron for his birthday. Each of the squares has an integer on it. She decides to share a contiguous segment of the bar selected such that the length of the segment matches Ron's birth month and the sum of the integers on the squares is equal to his birth day. You must determine how many ways she can divide the chocolate.

Consider the chocolate bar as an array of squares, `s = [2, 3, 1, 3, 2]`. She wants to find segments summing to Ron's birth day, `d = 4` with a length equalling his birth month, `m = 2`. In this case, there are two segments meeting her criteria: `[2, 2]` and `[1, 3]`.

<br/>
<!-- more -->

## Function Description

Complete the birthday function in the editor below. It should return an integer denoting the number of ways Lily can divide the chocolate bar.

birthday has the following parameter(s):

- s: an array of integers, the numbers on each of the squares of chocolate
- d: an integer, Ron's birth day
- m: an integer, Ron's birth month

<br/>

## Input Format

The first line contains an integer **n**, the number of squares in the chocolate bar.  
The second line contains **n** space-separated integers **s[i]**, the numbers on the chocolate squares where ![](https://latex.codecogs.com/gif.latex?0\leq&space;i<&space;n).   
The third line contains two space-separated integers, **d** and **m**, Ron's birth day and his birth month.

<br/>

## Constraints


## Output Format

Print an integer denoting the total number of ways that Lily can portion her chocolate bar to share with Ron.

<br/>

## Sample Input 0
```
5
1 2 1 3 2
3 2
```

<br/>

## Sample Output 0
```
2
```

<br/>

## Explanation 0

Lily wants to give Ron **m = 2** squares summing to **d = 3**. The following two segments meet the criteria:

![](./images/birthdayChocolate_01.png)

Sample Input 1
```
6
1 1 1 1 1 1
3 2
```

<br/>

## Sample Output 1
```
0
```

<br/>

## Explanation 1

Lily only wants to give Ron **m = 2** consecutive squares of chocolate whose integers sum to **d = 3**. There are no possible pieces satisfying these constraints:

![](./images/birthdayChocolate_02.png)

Thus, we print **0** as our answer.

<br/>

## Sample Input 2
```
1
4
4 1
```

<br/>

## Sample Output 2
```
1
```

<br/>

## Explanation 2

Lily only wants to give Ron `m = 1` square of chocolate with an integer value of `d = 4`. Because the only square of chocolate in the bar satisfies this constraint, we print `1` as our answer.

<br/>

---

### Solution

```javascript
function birthday(s, d, m) {
    return new Array(s.length - m + 1).fill('').reduce((target, chocolate, index) => {
        (s.reduce((target, number, innerIndex) => {
            (innerIndex >= index && innerIndex < index + m) && (target += number);

            return target;
        }, 0) === d) && target++;
        
        return target;
    }, 0)
}
```