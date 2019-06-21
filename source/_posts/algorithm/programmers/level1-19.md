---
title: 프로그래머스 - 자연수 뒤집어 배열로 만들기
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-21 22:59:39
---


## 문제 설명
자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요.
예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

<!-- more -->
<br/>

## 제한 조건
n은 10,000,000,000이하인 자연수입니다.

<br/>

## 입출력 예
| n | return |
| :---: | :---: |
| 12345 | [5,4,3,2,1] |  

<br/>

---

```javascript
function solution(n) {
    return [...n.toString()].reverse().map(v => Number(v))
}

```
