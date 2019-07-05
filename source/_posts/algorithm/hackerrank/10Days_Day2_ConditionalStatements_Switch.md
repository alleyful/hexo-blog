---
title: Day2 Conditional Statements (Switch)
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-01 19:49:58
---

## Objective

In this challenge, we learn about switch statements. Check out the attached tutorial for more details.

<br/>

## Task

Complete the getLetter(s) function in the editor. It has one parameter: a string, **s**, consisting of lowercase English alphabetic letters (i.e., a through z). It must return A, B, C, or D depending on the following criteria:

- If the first character in string **s** is in the set **{a, e, i, o, u}**, then return A.
- If the first character in string **s** is in the set **{b, c, d, f, g}**, then return B.
- If the first character in string **s** is in the set **{h, j, k, l, m}**, then return C.
- If the first character in string **s** is in the set **{n, p ,q,r, s, t, v, w, x, y, z}**, then return D.
**Hint**: You can get the letter at some index **i** in **s** using the syntax s[i] or s.charAt(i).

<br/>
<!-- more -->

## Input Format

Stub code in the editor reads a single string denoting **s** from stdin.

<br/>

## Constraints
- **1 <= |s| <= 100**, where **|s|** is the length of **s**.
- String **s** contains lowercase English alphabetic letters (i.e., a through z) only.

<br/>

## Output Format

Return either A, B, C, or D according to the criteria given above.

<br/>

## Sample Input 0

```
adfgt
```

<br/>

## Sample Output 0

```
AA
```

<br/>

## Explanation

The first character of string **s = adfgt** is a. Because the given criteria stipulate that we print A any time the first character is in **{a, e, i, o, u}**, we return A as our answer.

<br/>

---

### Solution1

```javascript
function getLetter(s) {
    const firstCharacter = s.slice(0, 1);
    let letter;
    // Write your code here
    switch (firstCharacter) {
        case 'a':
        case 'e':
        case 'i':
        case 'o':
        case 'u':
            letter = 'A';
            break;

        case 'b':
        case 'c':
        case 'd':
        case 'f':
        case 'g':
            letter = 'B';
            break;

        case 'h':
        case 'j':
        case 'k':
        case 'l':
        case 'm':
            letter = 'C';
            break;

        default:
            letter = 'D';
            break;
    }
    return letter;
}
```

### Solution2

```javascript

function getLetter(s) {
    let letter;
    // Write your code here
    switch (s[0]) {
        case ('a' || 'e' || 'o' || 'i' || 'u'):
            letter = 'A';
            break;

        case ('b' || 'c' || 'd' || 'f' || 'g'):
            letter = 'B';
            break;

        case ('h' || 'j' || 'k' || 'l' || 'm'):
            letter = 'C';
            break;

        case ('z' || 'n' || 'p' || 'q' || 'r' || 's' || 't' || 'v' || 'w' || 'x' || 'y'):
            letter = 'D';

    }

    return letter;
}
```
