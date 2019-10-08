---
title: 프로그래머스 - 행렬의 곱셈
thumbnail: images/gallery/thumbnails/programmers.png
categories:
  - Algorithm
  - Programmers
  - Level2
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-10-08 20:17:12
---

## 문제 설명
2차원 행렬 arr1과 arr2를 입력받아, arr1에 arr2를 곱한 결과를 반환하는 함수, solution을 완성해주세요.

<br/>

## 제한 조건
- 행렬 arr1, arr2의 행과 열의 길이는 2 이상 100 이하입니다.
- 행렬 arr1, arr2의 원소는 -10 이상 20 이하인 자연수입니다.
- 곱할 수 있는 배열만 주어집니다.

<br/>
<!-- more -->

## 입출력 예
| arr1 | arr2 | return |
| :--- | :--- | :--- |
| [[1, 4], [3, 2], [4, 1]] | [[3, 3], [3, 3]] | [[15, 15], [15, 15], [15, 15]] |
| [[2, 3, 2], [4, 2, 4], [3, 1, 4]] | [[5, 4, 3], [2, 4, 1], [3, 1, 1]] | [[22, 22, 11], [36, 28, 18], [29, 20, 14]] |

<br/>

---

### Solution
```javascript
function solution(arr1, arr2) {
    return Array(arr1.length).fill('').map(
        (rowValue, index) => Array(arr2[0].length).fill('').map(
            (verticalValue, innerIndex) => arr1[index].reduce(
                (target, current, array) =>target + current * arr2[array][innerIndex], 0
            )
        )
    )
}
```