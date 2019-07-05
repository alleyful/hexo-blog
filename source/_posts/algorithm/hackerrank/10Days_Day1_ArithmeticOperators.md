---
title: Day1 Arithmetic Operators
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-05-31 18:22:42
---

## Objective

In this challenge, we practice using arithmetic operators. Check out the attached tutorial for resources.

<br/>

## Task

Complete the following functions in the editor below:

1. getArea(length, width): Calculate and return the area of a rectangle having sides **length** and **width**.
2. getPerimeter(length, width): Calculate and return the perimeter of a rectangle having sides **length** and **width**.

The values returned by these functions are printed to stdout by locked stub code in the editor.

<br/>
<!-- more -->

## Input Format

### getArea
| Data Type | Parameter | Description |
|:---:|:---:|:---:|
| Number | length | A number denoting the length of a rectangle. |
| Number | height | A number denoting the height of a rectangle. |

<br/>

### getPerimeter(length, height)
| Data Type | Parameter | Description |
|:---:|:---:|:---:|
| Number | length | A number denoting the length of a rectangle. |
| Number | height | A number denoting the height of a rectangle. |

<br/>

## Constraints
- **1 <= length,width <= 100**
- **length** and **height** are scaled to at most three decimal places.

<br/>

## Output Format
| Function | Return Type | Description |
|:---:|:---:|:---:|
| getArea | Number | The area of a rectangle having sides **length** and **width**. |
| getPerimeter | Number | The perimeter of a rectangle having sides **length** and **width**. |

<br/>

## Sample Input 0

```
3
4.5
```

<br/>

## Sample Output 0

```
13.5
15
```

<br/>

## Explanation

The area of the rectangle is **length X width = 3 X 4.5 = 13.5**.<br/>
The perimeter of the rectangle is **2 X (length + height) = 2 X (3 + 4.5) = 15**.

<br/>

---

### Solution

```javascript
function getArea(length, width) {
    let area;
    area = length * width;

    return area;
}

function getPerimeter(length, width) {
    let perimeter;
    perimeter = 2 * (length + width);
    
    return perimeter;
}
```

