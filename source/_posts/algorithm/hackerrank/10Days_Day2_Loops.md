---
title: Day2 Loops
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-01 22:13:09
---

## Objective

In this challenge, we practice looping over the characters of string. Check out the attached tutorial for more details.

<br/>

## Task

Complete the vowelsAndConsonants function in the editor below. It has one parameter, a string, **s**, consisting of lowercase English alphabetic letters (i.e., a through z). The function must do the following:

1. First, print each vowel in **s** on a new line. The English vowels are a, e, i, o, and u, and each vowel must be printed in the same order as it appeared in **s**.
2. Second, print each consonant (i.e., non-vowel) in **s** on a new line in the same order as it appeared in **s**.

<br/>
<!-- more -->

## Input Format

Locked stub code in the editor reads string **s** from stdin and passes it to the function.

<br/>

## Output Format

First, print each vowel in **s** on a new line (in the same order as they appeared in **s**). Second, print each consonant (i.e., non-vowel) in **s** on a new line (in the same order as they appeared in **s**).

<br/>

## Sample Input 0

```
javascriptloops
```

<br/>

## Sample Output 0

```
a
a
i
o
o
j
v
s
c
r
p
t
l
p
s
```

<br/>

## Explanation 0

Observe the following:

- Each letter is printed on a new line.
- Then the vowels are printed in the same order as they appeared in **s**.
- Then the consonants are printed in the same order as they appeared in **s**.

<br/>

---

### Solution1

```javascript
/*
 * Complete the vowelsAndConsonants function.
 * Print your output using 'console.log()'.
 */
const vowel = [ 'a', 'e', 'i', 'o', 'u' ];

function vowelsAndConsonants(s) {
    let { vowels, consonants } = (s.split('') || []).reduce((target, item) => {
        target[vowel.includes(item) ? 'vowels' : 'consonants'].push(item)

        return target;
    }, { vowels: [], consonants: [] });

    vowels.concat(consonants).forEach((item) => {
        console.log(item);
    });
}


```

### Solution2

```javascript
function vowelsAndConsonants(s) {
    const vowelArray = [...s];
    let result = [];

    const newArray = vowelArray.reduce((target, item) => {
        switch (item) {
            case 'a':
            case 'e':
            case 'i':
            case 'o':
            case 'u':
                target['first'].push(item);
                break;

            default:
                target['second'].push(item);
                break;
        }

        return target;
    }, {first: [], second: []});

    result = [...newArray['first'], ...newArray['second']].map(item => console.log(item))
}
```

### Solution3

```javascript
function vowelsAndConsonants(s) {
    const vowelArray = [...s];
    const result = [];

    const newArray = vowelArray.reduce((target, item) => {
        switch (item) {
            case 'a':
            case 'e':
            case 'i':
            case 'o':
            case 'u':
                target[0].push(item);
                break;

            default:
                target[1].push(item);
                break;
        }
        
        return target;
    }, [[], []]);

    newArray.reduce((target, items) => {
        target.push(
            items.reduce((target, item) => {
                result.push(item);

                return target;
            }, [])
        );

        return target;
    }, []);

    result.map(item => console.log(item))
}
```
