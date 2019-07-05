---
title: Day7 Regular Expressions I
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-07 22:33:56
---

## Objective

In this challenge, we use a Regular Expression to evaluate a string. Check out the attached tutorial for more details.

<br/>

## Task

Complete the function in the editor below by returning a RegExp object, **re**, that matches any string **s** that begins and ends with the same vowel. Recall that the English vowels are a, e, i, o, and u.

<br/>
<!-- more -->

## Constraints
   
- The length of string **s** is **>= 3**.
- String **s** consists of lowercase letters only (i.e., [a-z]).

<br/>

## Output Format
   
The function must return a RegExp object that matches any string **s**   beginning with and ending in the same vowel.

<br/>

## Sample Input 0
```
bcd
```

<br/>

## Sample Output 0
```
false
```

<br/>

## Explanation 0

This string starts with (and ends in) a consonant, so it cannot start and end with the same vowel.   


<br/>

## Sample Input 1
```
abcd
```

<br/>

## Sample Output 1
```
false
```

<br/>

## Explanation 1

This string ends in a consonant, so it cannot start and end with the same vowel.

<br/>

## Sample Input 2
```
abcda
```

<br/>

## Sample Output 2
```
true
```

<br/>

## Explanation 2

This string starts and ends with the same vowel (a).

<br/>

## Sample Input 3
```
abcdo
```

<br/>

## Sample Output 3
```
false
```

<br/>

## Explanation 3

This string starts with the vowel a but ends in the vowel o.

<br/>

---

### Solution

```javascript
function regexVar() {
    /*
     * Declare a RegExp object variable named 're'
     * It must match a string that starts and ends with the same vowel (i.e., {a, e, i, o, u})
     */
    return new RegExp(/^([aeiou]).*\1$/);
    
    /*
     * Do not remove the return statement
     */
    return re;
}
```