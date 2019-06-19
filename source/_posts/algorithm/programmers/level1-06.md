---
title: 프로그래머스 - 가운데 글자 가져오기
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-13 23:00:47
---


## 문제 설명
단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요.
단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

<!-- more -->
<br/>

## 제한사항
s는 길이가 1 이상, 100이하인 스트링입니다.

<br/>

## 입출력 예
| s | return |
| --- | :---: |
| "abcde" | "c" |
| "qwer" | "we" |

<br/>

---

### Solution 1

```javascript
function solution(s) {
    let string = [...s];
    const leng = string.length;
    return (leng % 2 === 0 ? string.splice(leng/2 - 1, 2) : string.splice(leng/2, 1)).join('');
}
```

### Solution 2

```javascript
function solution(s) {
  return s.substr(Math.ceil(s.length / 2) - 1, s.length % 2 === 0 ? 2 : 1);
}
```