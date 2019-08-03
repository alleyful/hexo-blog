---
title: Beautiful Days at the Movies
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- ProblemSolving
tags:
- Algorithm
- HackerRank
- ProblemSolving
date: 2019-08-04 00:15:29
---
  
  
  

Lily likes to play games with integers. She has created a new game where she determines the difference between a number and its reverse. For instance, given the number **12**, its reverse is **21**. Their difference is **9**. The number **120** reversed is **21**, and their difference is **99**.

She decides to apply her game to decision making. She will look at a numbered range of days and will only go to a movie on a beautiful day.

Given a range of numbered days, **[i ... j]** and a number **k**, determine the number of days in the range that are beautiful.  
Beautiful numbers are defined as numbers where `|i - reverse(i)|` is evenly divisible by **k**. If a day's value is a beautiful number, it is a beautiful day. Print the number of beautiful days in the range.

<br/>
<!-- more -->

## Function Description

Complete the beautifulDays function in the editor below. It must return the number of beautiful days in the range.

beautifulDays has the following parameter(s):

- i: the starting day number
- j: the ending day number
- k: the divisor

<br/>

## Input Format

A single line of three space-separated integers describing the respective values of **i**, **j**, and **k**.

<br/>

## Constraints

- ![](https://latex.codecogs.com/gif.latex?1\leq&space;i\leq&space;j\leq&space;2\times&space;10^{6})
- ![](https://latex.codecogs.com/gif.latex?1\leq&space;k\leq&space;2\times&space;10^{9})

<br/>

## Output Format

Print the number of beautiful days in the inclusive range between **i** and **j**.

<br/>

## Sample Input
```
20 23 6
```

<br/>

## Sample Output
```
2
```

<br/>

## Explanation

Lily may go to the movies on days **20**, **21**, **22**, and **23**. We perform the following calculations to determine which days are beautiful:

- Day **20** is beautiful because the following evaluates to a whole number: ![](https://latex.codecogs.com/gif.latex?\frac{|20-02|}{6}=\frac{18}{6}=3)
- Day **21** is not beautiful because the following doesn't evaluate to a whole number: ![](https://latex.codecogs.com/gif.latex?\frac{|21-12|}{6}=\frac{9}{6}=1.5)
- Day **22** is beautiful because the following evaluates to a whole number: ![](https://latex.codecogs.com/gif.latex?\frac{|22-22|}{6}=\frac{0}{6}=0)
- Day **23** is not beautiful because the following doesn't evaluate to a whole number: ![](https://latex.codecogs.com/gif.latex?\frac{|23-32|}{6}=\frac{9}{6}=1.5)

Only two days, **20** and **22**, in this interval are beautiful. Thus, we print **2** as our answer.

<br/>

---

### Solution

```javascript
function beautifulDays(i, j, k) {
    return new Array(j - i + 1).fill(0).reduce((target, number, index) => { 
        (Number([...String(index + i)].reverse().join('')) - (index + i)) % k === 0 && ++target;
        
        return target;
    }, 0)
}
```