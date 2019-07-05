---
title: Day7 Regular Expressions III
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-07 23:13:11
---

## Task

Complete the function in the editor below by returning a RegExp object, **re**, that matches every integer in some string **s**.

<br/>

## Constraints
   
- The length of string **s** is **>= 3**.
- It's guaranteed that string **s** contains at least one integer.

<br/>
<!-- more -->

## Output Format
   
The function must return a RegExp object that matches every integer in some string **s**.

<br/>

## Sample Input 0
```
102, 1948948 and 1.3 and 4.5
```

<br/>

## Sample Output 0
```
102
1948948
1
3
4
5
```

<br/>

## Explanation 0

When we call match on string **s** and pass the correct RegExp as our argument, it returns the following array of results: [ '102', '1948948', '1', '3', '4', '5' ].

<br/>

## Sample Input 1
```
1 2 3
```

<br/>

## Sample Output 1
```
1
2
3
```

<br/>

## Explanation 1

When we call match on string **s** and pass the correct RegExp as our argument, it returns the following array of results: [ '1', '2', '3' ].

<br/>

---

### Solution

```javascript
function regexVar() {
    /*
     * Declare a RegExp object variable named 're'
     * It must match ALL occurrences of numbers in a string.
     */
    const re = new RegExp(/[0-9]+/gm);
    
    /*
     * Do not remove the return statement
     */
    return re;
}
```