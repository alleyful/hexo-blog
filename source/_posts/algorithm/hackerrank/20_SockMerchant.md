---
title: Sock Merchant
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- ProblemSolving
tags:
- Algorithm
- HackerRank
- ProblemSolving
date: 2019-07-23 00:13:45
---
  
  
  
John works at a clothing store. He has a large pile of socks that he must pair by color for sale. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

For example, there are **n = 7** socks with colors `ar = [1, 2, 1, 2, 1, 3, 2]`. There is one pair of color *1* and one of color *2*. There are three odd socks left, one of each color. The number of pairs is *2*.

<br/>
<!-- more -->

## Function Description

Complete the sockMerchant function in the editor below. It must return an integer representing the number of matching pairs of socks that are available.

sockMerchant has the following parameter(s):

- n: the number of socks in the pile
- ar: the colors of each sock

<br/>

## Input Format

The first line contains an integer **n**, the number of socks represented in *ar*. 
The second line contains *n* space-separated integers describing the colors *ar[i]* of the socks in the pile.

<br/>

## Constraints

- ![](https://latex.codecogs.com/gif.latex?1\leq&space;n\leq&space;100)
- ![](https://latex.codecogs.com/gif.latex?1\leq&space;ar[i]\leq&space;100) where ![](https://latex.codecogs.com/gif.latex?0\leq&space;i&space;<&space;n)

<br/>

## Output Format

Return the total number of matching pairs of socks that John can sell.

<br/>

## Sample Input
```
9
10 20 20 10 10 30 50 10 20
```

<br/>

## Sample Output
```
3
```

<br/>

## Explanation

![](https://github.com/alleyful/algorithm-solutions/raw/master/HackerRank/ProblemSolving/images/sock.png)

John can match three pairs of socks.

<br/>

---

### Solution

```javascript
function sockMerchant(n, ar) {
    let socks = [];
    return ar.reduce((target, sock) => {
        let index = socks.findIndex(v => v === sock);
        index >= 0
            ? (socks.splice(index, 1), target++)
            : (socks.push(sock))
        return target;
    }, 0);
}
```