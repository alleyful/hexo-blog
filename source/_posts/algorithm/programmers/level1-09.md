---
title: 프로그래머스 - 두 정수 사이의 합
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-14 20:06:38
---


## 문제 설명
두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요. 
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

<!-- more -->
<br/>

## 제한 조건
a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
a와 b의 대소관계는 정해져있지 않습니다.

<br/>

## 입출력 예
| a | b | return |
| --- | :---: | :---: |
| 3 | 5 | 12 |
| 3 | 3 | 3 |
| 5 | 3 | 12 |

<br/>

---

### Solution 1
```javascript
function solution(a, b) {
    const array = [a, b].sort((a, b) => a - b);
    const bigNum = array[1];
    const smallNum = array[0];
    const baseNum = smallNum - 1;
    const length = bigNum - smallNum + 1;
    return bigNum === smallNum ? bigNum : (baseNum * length) + ((1 + length) * length / 2);
}
```

### Solution 2
```javascript
function solution(a, b) {
  return (a + b) * ((a > b ? a - b : b - a) + 1) / 2;
}
```
