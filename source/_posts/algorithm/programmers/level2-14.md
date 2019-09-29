---
title: 프로그래머스 - 피보나치 수
thumbnail: images/gallery/thumbnails/programmers.png
categories:
  - Algorithm
  - Programmers
  - Level2
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-09-28 22:19:52
---


## 문제 설명
피보나치 수는 F(0) = 0, F(1) = 1일 때, 1 이상의 n에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 수 입니다.

예를들어

F(2) = F(0) + F(1) = 0 + 1 = 1
F(3) = F(1) + F(2) = 1 + 1 = 2
F(4) = F(2) + F(3) = 1 + 2 = 3
F(5) = F(3) + F(4) = 2 + 3 = 5
와 같이 이어집니다.

2 이상의 n이 입력되었을 때, n번째 피보나치 수를 1234567으로 나눈 나머지를 리턴하는 함수, solution을 완성해 주세요.

<br/>
<!-- more -->

## 제한 사항
* n은 1이상, 100000이하인 자연수입니다.

<br/>

## 입출력 예
| n | return |
| :---: | :---: |
| 3 | 2 |
| 5 | 5 |

<br/>

## 입출력 예 설명
피보나치수는 0번째부터 0, 1, 1, 2, 3, 5, ... 와 같이 이어집니다.

<br/>

---

### Solution
```javascript
function solution(n) {
    const fibonacci = [0, 1];
    for (let i = 1; i <= n; i++) {
        fibonacci.push((fibonacci[i - 1] + fibonacci[i]) % 1234567);
    }   
    return fibonacci[n];
}
```