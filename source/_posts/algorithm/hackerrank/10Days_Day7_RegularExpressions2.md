---
title: Day7 Regular Expressions II
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

Complete the function in the editor below by returning a RegExp object, **re**, that matches any string **s** satisfying both of the following conditions:

- String **s** starts with the prefix Mr., Mrs., Ms., Dr., or Er.
- The remainder of string **s** (i.e., the rest of the string after the prefix) consists of one or more upper and/or lowercase English alphabetic letters (i.e., [a-z] and [A-Z]).

<br/>
<!-- more -->

## Constraints
   
- The length of string **s** is **>= 3**.

<br/>

## Output Format
   
The function must return a RegExp object that matches any string **s** satisfying both of the given conditions.

<br/>

## Sample Input 0
```
Mr.X
```

<br/>

## Sample Output 0
```
true
```

<br/>

## Explanation 0

This string starts with Mr., followed by an English alphabetic letter (X).

<br/>

## Sample Input 1
```
Mrs.Y
```

<br/>

## Sample Output 1
```
true
```

<br/>

## Explanation 1

This string starts with Mrs., followed by an English alphabetic letter (Y).

<br/>

## Sample Input 2
```
Dr#Joseph
```

<br/>

## Sample Output 2
```
false
```

<br/>

## Explanation 2

This string starts with Dr# instead of Dr., so it's invalid.

<br/>

## Sample Input 3
```
Er .Abc
```

<br/>

## Sample Output 3
```
false
```

<br/>

## Explanation 3

This string starts with Er but there is a space before the period (.), making the string invalid.

<br/>

---

### Solution

```javascript
function regexVar() {
    /*
     * Declare a RegExp object variable named 're'
     * It must match a string that starts with 'Mr.', 'Mrs.', 'Ms.', 'Dr.', or 'Er.', 
     * followed by one or more letters.
     */
    const re = new RegExp(/^(Mr\.|Dr\.|Er\.|Ms\.|Mrs\.)\s?[a-z|A-Z]+$/);
    /*
     * Do not remove the return statement
     */
    return re;
}
```