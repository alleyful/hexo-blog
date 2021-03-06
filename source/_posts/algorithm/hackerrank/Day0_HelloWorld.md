---
title: Day0 Hello World
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 30DaysOfCode
tags:
- Algorithm
- HackerRank
date: 2019-06-15 00:01:34
---

## Objective

In this challenge, we review some basic concepts that will get you started with this series. You will need to use the same (or similar) syntax to read input and write output in challenges throughout HackerRank. Check out the Tutorial tab for learning materials and an instructional video!

<br/>
<!-- more -->

## Task

To complete this challenge, you must save a line of input from stdin to a variable, print Hello, World. on a single line, and finally print the value of your variable on a second line.

You've got this!

**Note**: The instructions are Java-based, but we support submissions in many popular languages. You can switch languages using the drop-down menu above your editor, and the **InputString** variable may be written differently depending on the best-practice conventions of your submission language.

<br/>

## Input Format

A single line of text denoting **inputString** (the variable whose contents must be printed).

<br/>

## Output Format

Print Hello, World. on the first line, and the contents of **inputString** on the second line.

<br/>

## Sample Input 0

```
Welcome to 30 Days of Code!
```

<br/>

##Sample Output 0

```
Hello, World. 
Welcome to 30 Days of Code!
```

<br/>

## Explanation

On the first line, we print the string literal Hello, World.. On the second line, we print the contents of the **inputString** variable which, for this sample case, happens to be Welcome to 30 Days of Code!. If you do not print the variable's contents to stdout, you will not pass the hidden test case.


<br/>
<br/>

---

### Solution

```javascript

function processData(inputString) {
    // This line of code prints the first line of output
    console.log("Hello, World.");
    
    // Write the second line of output that prints the contents of 'inputString' here.
}

```

