---
title: 프로그래머스 - 문자열 내 p와 y의 개수
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-17 23:26:40
---


## 문제 설명
대문자와 소문자가 섞여있는 문자열 s가 주어집니다. 
s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 
'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.
예를들어 s가 pPoooyY면 true를 return하고 Pyy라면 false를 return합니다.

<!-- more -->
<br/>

## 제한사항
- 문자열 s의 길이 : 50 이하의 자연수
- 문자열 s는 알파벳으로만 이루어져 있습니다.

<br/>

## 입출력 예
| s | answer |
| :---: | :---: |
| pPoooyY | true |
| Pyy | false |

<br/>

## 입출력 예 설명
- 입출력 예 #1
	- 'p'의 개수 2개, 'y'의 개수 2개로 같으므로 true를 return 합니다.

- 입출력 예 #2
	- 'p'의 개수 1개, 'y'의 개수 2개로 다르므로 false를 return 합니다.
	
<br/>

---

### Solution 1

```javascript
function solution(s){
     let pList = [...s].filter(v => v === 'p' || v === 'P');
     let yList = [...s].filter(v => v === 'y' || v === 'Y');
   
     return pList.length === yList.length;
}
```

### Solution 2

```javascript
function solution(s){
     return (s.match(/p/gi) || []).length === (s.match(/y/gi) || []).length;
}

```