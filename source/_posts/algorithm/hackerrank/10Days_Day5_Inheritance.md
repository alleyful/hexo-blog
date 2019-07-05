---
title: Day5 Inheritance
thumbnail: images/gallery/thumbnails/hackerrank.jpg
categories:
- Algorithm
- HackerRank
- 10DaysOfJS
tags:
- Algorithm
- HackerRank
- 10DaysOfJS
date: 2019-06-04 21:19:49
---

## Objective

In this challenge, we practice implementing inheritance and use JavaScript prototypes to add a new method to an existing prototype. Check out the attached Classes tutorial to refresh what we've learned about these topics.

<br/>
<!-- more -->

## Task

We provide the implementation for a Rectangle class in the editor. Perform the following tasks:

1. Add an area method to Rectangle's prototype.
2. Create a Square class that satisfies the following:
 - It is a subclass of Rectangle.
 - It contains a constructor and no other methods.
 - It can use the Rectangle class' area method to print the area of a Square object.
 
Locked code in the editor tests the class and method implementations and prints the area values to STDOUT.

<br/>

---

### Solution 1

```javascript
/*
 *  Write code that adds an 'area' method to the Rectangle class' prototype
 */
Rectangle.prototype.area = function () {
    return (this.w * this.h);
}

/*
 * Create a Square class that inherits from Rectangle and implement its class constructor
 */
class Square extends Rectangle {
    constructor(s) {
        super(s, s);
    }
}
```

### Solution 2

```javascript
Rectangle.prototype.area = function () {
    return this.w * this.h;
}

class Square extends Rectangle {
    constructor(w) {
        super(w);

        this.h = w;
    }
}
```