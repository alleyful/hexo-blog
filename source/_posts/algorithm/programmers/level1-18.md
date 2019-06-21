---
title: 프로그래머스 - 자릿수 더하기
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-21 01:09:22
---


## 문제 설명
자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

<!-- more -->
<br/>

## 제한 사항
N의 범위 : 100,000,000 이하의 자연수

<br/>

## 입출력 예
| N | answer |
| :--- | :--- |
| 123 | 6 |
| 987 | 24 |

<br/>

### 입출력 예 설명
- 입출력 예 #1
  - 문제의 예시와 같습니다.

- 입출력 예 #2
  - 9 + 8 + 7 = 24이므로 24를 return 하면 됩니다.

<br/>
<br/>

---

### Solution
```javascript
function solution(n)
{
    return [...n.toString()].reduce((target, item) => {    
        return target += Number(item);
    }, 0);
}
```
