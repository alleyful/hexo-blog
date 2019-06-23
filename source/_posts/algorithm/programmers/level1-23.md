---
title: 프로그래머스 - 짝수와 홀수
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-22 21:35:48
---


## 문제 설명
정수 num이 짝수일 경우 Even을 반환하고 홀수인 경우 Odd를 반환하는 함수, solution을 완성해주세요.

<!-- more -->
<br/>

## 제한 조건
num은 int 범위의 정수입니다.
0은 짝수입니다.

<br/>

## 입출력 예
| num | return |
| :---: | :---: |
| 3 | Odd |
| 4 | Even |

<br/>

---

### Solution
```javascript
function solution(num) {
    return num % 2 === 0 ? "Even" : "Odd";
}
```




