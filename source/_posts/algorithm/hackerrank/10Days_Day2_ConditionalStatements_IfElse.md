---
title: Day2 Conditional Statements (If-Else)
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-01 12:28:17
---

## Objective

In this challenge, we learn about if-else statements. Check out the attached tutorial for more details.

<br/>

## Task

Complete the getGrade(score) function in the editor. It has one parameter: an integer, **score**, denoting the number of points Julia earned on an exam. It must return the letter corresponding to her **grade** according to the following rules:

- If **\(25 < score <= 30\)**, then **grade = A**.
- If **\(20 < score <= 25\)**, then **grade = B**.
- If **\(15 < score <= 20\)**, then **grade = C**.
- If **\(10 < score <= 15\)**, then **grade = D**.
- If **\(5 < score <= 10\)**, then **grade = E**.
- If **\(0 < score <= 5\)**, then **grade = F**.

<br/>
<!-- more -->

## Input Format

Stub code in the editor reads a single integer denoting **score** from stdin and passes it to the function.

<br/>

## Constraints
- **0 <= score <= 30**

<br/>

## Output Format

The function must return the value of **grade** (i.e., the letter grade) that Julia earned on the exam.

<br/>

## Sample Input 0

```
11
```

<br/>

## Sample Output 0

```
D
```

<br/>

## Explanation

Because **score = 11**, it satisfies the condition **\(10 < score <= 15\)** (which corresponds to D). Thus, we return D as our answer.

<br/>

---

### Solution1

```javascript
function getGrade(score) {
    let grade;

    if (score <= 5) {
        return 'F';
    } else if (score <= 10) {
        return 'E';
    } else if (score <= 15) {
        return 'D';
    } else if (score <= 20) {
        return 'C';
    } else if (score <= 25) {
        return 'B';
    } else {
        return 'A';
    }

    return grade;
}
```

### Solution2

```javascript
function getGrade(score) {
    let grade;
    // Write your code here
    grade = score <= 5 ? 'F'
        : score <= 10 ? 'E'
            : score <= 15 ? 'D'
                : score <= 20 ? 'C'
                    : score <= 25 ? 'B'
                        : score <= 30 ? 'A' : '';

    return grade;
}
```
