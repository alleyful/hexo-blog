---
title: Chocolate Feast
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- ProblemSolving
tags:
- Algorithm
- HackerRank
- ProblemSolving
- Javascript
date: 2019-08-28 01:03:51
---
  
  
Little Bobby loves chocolate. He frequently goes to his favorite **5 & 10** store, Penny Auntie, to buy them. They are having a promotion at Penny Auntie. If Bobby saves enough wrappers, he can turn them in for a free chocolate.

For example, Bobby has **n = 15** to spend on bars of chocolate that cost **c = 3** each. He can turn in **m = 2** wrappers to receive another bar. Initially, he buys **5** bars and has **5** wrappers after eating them. He turns in **4** of them, leaving him with **1**, for **2** more bars. After eating those two, he has **3** wrappers, turns in **2** leaving him with **1** wrapper and his new bar. Once he eats that one, he has **2** wrappers and turns them in for another bar. After eating that one, he only has **1** wrapper, and his feast ends. Overall, he has eaten `5 + 2 + 1 + 2 = 9` bars.

<br/>
<!-- more -->

## Function Description

Complete the chocolateFeast function in the editor below. It must return the number of chocolates Bobby can eat after taking full advantage of the promotion.

chocolateFeast has the following parameter(s):

- n: an integer representing Bobby's initial amount of money
- c: an integer representing the cost of a chocolate bar
- m: an integer representing the number of wrappers he can turn in for a free bar   

**Note**: Little Bobby will always turn in his wrappers if he has enough to get a free chocolate.

<br/>

## Input Format

The first line contains an integer, **t**, denoting the number of test cases to analyze. 
Each of the next **t** lines contains three space-separated integers: **n**, **c**, and **m**. They represent money to spend, cost of a chocolate, and the number of wrappers he can turn in for a free chocolate.

<br/>

## Constraints
- ![](https://latex.codecogs.com/gif.latex?1\leq&space;t\leq&space;1000)
- ![](https://latex.codecogs.com/gif.latex?2\leq&space;n\leq&space;10^{5})
- ![](https://latex.codecogs.com/gif.latex?1\leq&space;c\leq&space;n)
- ![](https://latex.codecogs.com/gif.latex?2\leq&space;m\leq&space;n)

<br/>

## Output Format

For each trip to Penny Auntie, print the total number of chocolates Bobby eats on a new line.

<br/>

## Sample Input
```
3
10 2 5
12 4 4
6 2 2
```

<br/>

## Sample Output
```
6
3
5
```

<br/>

## Explanation

Bobby makes the following **3** trips to the store:

1. He spends his **10** dollars on **5** chocolates at **2** dollars apiece. He then eats them and exchanges all **5** wrappers to get **1** more. He eats **6** chocolates.   
2. He spends his **12** dollars on **3** chocolates at **4** dollars apiece. He has **3** wrappers, but needs **4** to trade for his next chocolate. He eats **3** chocolates.   
3. He spends **6** dollars on **3** chocolates at **2** dollars apiece. He then exchanges **2** of the **3** wrappers for **1** additional piece. Next, he uses his third leftover chocolate wrapper from his initial purchase with the wrapper from his trade-in to do a second trade-in for **1** more piece. At this point he has **1** wrapper left, which is not enough to perform another trade-in. He eats **5** chocolates.   

<br/>

---

### Solution `Accepted`

```javascript
function chocolateFeast(n, c, m) {
  let result = Math.floor(n / c);
  let wrapper = result;
  let rest = 0;
  let total = result + rest;

  while (total / m >= 1) {
    total = wrapper + rest;
    wrapper = Math.floor(total / m);
    rest = total % m;
    result += wrapper;
  }

  return result;
}
```