---
title: 프로그래머스 - 시저 암호
categories:
  - Algorithm
  - Programmers
  - Level1
tags:
  - Algorithm
  - Programmers
  - 프로그래머스
date: 2019-06-18 00:52:18
---


## 문제 설명
어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 
예를 들어 AB는 1만큼 밀면 BC가 되고, 3만큼 밀면 DE가 됩니다. 
z는 1만큼 밀면 a가 됩니다. 
문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

<!-- more -->
<br/>

## 제한 조건
- 공백은 아무리 밀어도 공백입니다.
- s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
- s의 길이는 8000이하입니다.
- n은 1 이상, 25이하인 자연수입니다.

<br/>

## 입출력 예
| s | n | result |
| :---: | :---: | :---: |
| "AB" | 1 | "BC" |
| "z" | 1 | "a" |
| "a B z" | 4 | "e F d" |

<br/>

---

### Solution 1
```javascript
function solution(s, n) {
    //ASCII : A~Z(65~90) , a~z(97~122)
    return [...s].reduce((target, string, index) => {
        let asciiCode = s.charCodeAt(index)
        let changedCode = asciiCode + n
        let sCode = asciiCode < 65 ? asciiCode : (
            (asciiCode >= 65 && asciiCode <= 90) 
            ? (changedCode > 90 ? changedCode - 26 : changedCode)
            : (changedCode > 122 ? changedCode - 26 : changedCode)
        )
        target.push(String.fromCharCode(sCode))
        
        return target;
    }, []).join('')
}
```

### Solution 2

```javascript
function solution(s, n) {
    return (s || '').split('').reduce((target,item,index) => {
        target += (
            item == ' ' 
            ? ' ' 
            : String.fromCharCode((s.charCodeAt(index)>90)
                    ? (s.charCodeAt(index)+n-97)%26+97 
                    : (s.charCodeAt(index)+n-65)%26+65 )
            );

        return target;
    }, '')
}
```