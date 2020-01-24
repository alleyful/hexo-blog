---
title: 클로저(Closure)
toc: true
thumbnail: images/gallery/thumbnails/javascript.png
categories:
	- develop
	- javascript
tags:
	- closure
	- 클로저
	- javascript
date: 2019-08-23 20:20:22
---



<br/>
<br/>

---
# 클로저(Closure)의 개념

<br/>
<br/>

## 정의
클로저(closure)는 자바스크립트에서 중요한 개념 중 하나로 자바스크립트 고유의 개념이 아니라 함수를 일급 객체로 취급하는 함수형 프로그래밍 언어(Functional Programming language)에서 사용되는 중요한 특성이다.
클로저에 대해 MDN에서는 다음과 같이 정의하고 있다.

> A closure is the combination of a function and the `lexical environment` within which that function was declared.  
>
> 클로저는 함수와 그 함수가 선언됐을 때의 렉시컬 환경(Lexical environment)과의 조합이다.

- **함수**와 `그 함수가 선언될 당시의 환경정보` 사이의 조합 ⇒ `SCOPE`
- 함수 내부에서 생성한 **데이터**와 그 **유효범위**로 인해 발생하는 특수한 **현상/상태**
- `return` : 외부에 정보를 제공할 수 있는 유일한 수단
- return function ⇒ scope 및 lexical environment는 변하지 않는다. (`최초 선언시의 정보를 유지!!`)

<!-- more -->

아래의 코드를 보며 확인 해보자.

```javascript
function outFunc(x) {
    var y = 0;
    return function innerFunc(z) {
        y = 20;
        return x + y + z
    }
}

var outer = outFunc(10);
//  함수 outFunc 호출하면 내부 함수 innerFunc 반환된다.
//  그리고 함수 outFunc의 실행 컨텍스트는 소멸한다.

console.log(outer(5)); // 25
```
<br/>

outer 는 outFunc(10)을 실행해서 그 결과값으로 innerFunc를 받는다. 즉, outer는 x자리에 5가 들어간 상황에 대해서 저장한다.   

> 클로저의 정의에서 말하는 “함수”란 반환된 내부함수를 의미하고 “그 함수가 선언될 때의 렉시컬 환경(Lexical environment)”란 내부 함수가 선언됐을 때의 스코프를 의미한다. 
>
> 즉, 클로저는 반환된 내부함수가 자신이 선언됐을 때의 환경(Lexical environment)인 스코프를 기억하여 자신이 선언됐을 때의 환경(스코프) 밖에서 호출되어도 그 환경(스코프)에 접근할 수 있는 함수를 말한다. 
> 
> 이를 조금 더 간단히 말하면 `클로저는 자신이 생성될 때의 환경(Lexical environment)을 기억하는 함수`다라고 말할 수 있다.  
>
![](/images/develop/javascript/closure-01.png)

<br/>

<br/>

<br/>

---
# 클로저(Closure)의 활용

<br/>
<br/>

## 상태 유지와 전역변수의 사용 억제
클로저가 가장 유용하게 사용되는 상황은 현재 상태를 기억하고 변경된 최신 상태를 유지하는 것이다.  
호출할때마다 1씩 더해지는 카운터를 만들어보자. 이 count가 바로 유지해야할 상태이다.

![](/images/develop/javascript/closure-02.png)

setCount를 실행하여 반환된 익명함수를 count에 할당함으로써, count를 실행할때마다 setCount 스코프에서 count를 탐색하여 count에 1을 더한값을 반환할 것이다.

<br/>

## 정보의 은닉 (private 변수)
아래의 조건을 실행할 수 있는 자동차 게임을 만들어 보자.

{% blockquote %}
**자동차 게임**
- 차량별로 연료량 및 연비는 랜덤
- 유저별로 차량 하나씩 고르면 게임 시작
- 각 유조는 자신의 턴에 주사위를 굴려 랜덤하게 나온 숫자만큼 이동함.
- 연료가 부족하면 이동불가
- 가장 멀리 간 사람이 승리
{% endblockquote %}

```javascript
var car = {
    fuel: 10, //연료(l)
    power: 2, //연비(km / l)
    total: 0,
    run: function(km) {
        var wasteFuel = km / this.power;
        if(this.fuel < wasteFuel) {
            console.log('이동불가');
            return;
        }
        this.fuel -= wasteFuel;
        this.total += km;
    }
};
```

조건에 만족하는 게임을 만들었지만, 한가지 문제가 있다. 외부에서 연료와 연비를 마음대로 수정할 수 있는점이다.
이럴때 클로저를 이용하여 아래와 같이 수정하여 private member를 만들 수 있다.

```javascript
var createCar = function(f, p) {
    var fuel = f;
    var power = p;
    var total = 0;
    return {
        run: function(km) {
            var wasteFuel = km / power;
            if(fuel < wasteFuel) {
                console.log('이동불가');
                return;
            }
        fuel -= wasteFuel;
        total += km;
        }
    }
};

var car = createCar(10, 2);
```

<br/>

## 클로저를 이용해서 프라이빗 메소드 (private method) 흉내내기
자바와 같은 몇몇 언어들은 메소드를 프라이빗으로 선언할 수 있는 기능을 제공한다. 이는 같은 클래스 내부의 다른 메소드에서만 그 메소드들을 호출할 수 있다는 의미이다.

자바스크립트는 태생적으로는 이런 방법을 제공하지 않지만 클로저를 이용하여 프라이빗 메소드를 흉내내는 것이 가능하다. 프라이빗 메소드는 코드에 제한적인 접근만을 허용한다는 점 뿐만 아니라 전역 네임 스페이스를 관리하는 강력한 방법을 제공하여 불필요한 메소드가 공용 인터페이스를 혼란스럽게 만들지 않도록 한다.

아래 코드는 프라이빗 함수와 변수에 접근하는 퍼블릭 함수를 정의하기 위해 클로저를 사용하는 방법을 보여준다. 이렇게 클로저를 사용하는 것을 모듈 패턴이라 한다.

```javascript
var counter = (function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  };   
})();

console.log(counter.value()); // logs 0
counter.increment();
counter.increment();
console.log(counter.value()); // logs 2
counter.decrement();
console.log(counter.value()); // logs 1
```

이전 예제에서 각 클로저들이 고유한 문법적 환경을 가졌지만 여기서 우리는 `counter.increment`, `counter.decrement`, `counter.value` 세 함수에 의해 공유되는 하나의 어휘적 환경을 만든다.

공유되는 어휘적 환경은 실행되는 익명 함수 안에서 만들어진다. 이 익명 함수는 정의되는 즉시 실행된다. 이 어휘적 환경은 두 개의 프라이빗 아이템을 포함한다. 하나는 `privateCounter`라는 변수이고 나머지 하나는 `changeBy`라는 함수이다. 둘 다 익명 함수 외부에서 접근될 수 없다. 대신에 익명 래퍼에서 반환된 세 개의 퍼블릭 함수를 통해서만 접근되어야만 한다.

위의 세 가지 퍼블릭 함수는 같은 환경을 공유하는 클로저다. 자바스크립트의 어휘적 유효 범위 덕분에 세 함수 각각 `privateCounter` 변수와 `changeBy` 함수에 접근할 수 있다.

<br/>

<br/>

<br/>

<br/>

---
# 일반적인 실수 

<br/>
<br/>

## 루프에서 클로저 생성하기

1초마다 1,2,3,4,5,6,7,8,9 이 나오는 반복문 코드를 작성해보자.

```javascript
function count() {
    var i;
    for (i = 1; i < 10; i += 1) {
        setTimeout(function timer() {
            console.log(i);
        }, i*1000);
    }
}
count();
```

console에는 1~9가 출력되는 대신, 10이 9번 출력되었다. 그 이유는 이미 반복문의 실행이 끝난 시점의 변수 i값을 출력하고 있기 때문이다.

timer는 클로저로 언제 어디서 어떻게 호출되던지 항상 상위 스코프인 count에게 i를 알려달라고 요청할 것이다. 
timer는 1초 후 호출되는데, 1초가 지날 동안 이미 i는 10이 되어버렸기 때문에 이미 10이 되어버린 i만 출력하게 된다.

의도대로 1~9까지 차례대로 출력하고 싶으면 다음과 같은 방법을 사용할 수 있다.

1. 새로운 스코프를 추가하여 반복 시마다 그곳에 각각 따로 값을 저장하는 방식
2. ES6에서 추가된 블록 스코프를 이용하는 방식

<br/>

## 수정 (IIFE)
새로운 스코프를 추가하여 반복 시마다 그곳에 각각 따로 값을 저장하는 방식

```javascript
function count() {
     var i;
     for (i = 1; i < 10; i += 1) {
         (function(countingNumber) {
             setTimeout(function timer() {
                 console.log(countingNumber);
             }, i * 1000);
         })(i);
     }
 }
 count();
```

익명함수를 불러서 바로 호출하는 (IIFE) 즉시호출 함수로 만들어서 부를 수 있다.

<br/>

## 수정 (ES6)
ES6에서 추가된 블록 스코프를 이용하는 방식

```javascript
function count() {
     'use strict';
     for (let i = 1; i < 10; i += 1) {
         setTimeout(function timer() {
             console.log(i);
         }, i * 1000);
     }
 }
 count();
```
ES6에서 새로 추가된 const, let은 기존의 Lexical Scope이 아닌, Block Scope 단위로 동작한다.
그러므로, i는 블록 단위로 변수가 만들어지기 때문에 값이 남지 않고 블록 단위로 값이 다르게 출력될 수 있다.

<br/>

<br/>

<br/>

<br/>

---
# Reference

- Javascript 핵심 개념 알아보기 - [JS Flow](https://www.inflearn.com/course/%ED%95%B5%EC%8B%AC%EA%B0%9C%EB%85%90-javascript-flow#)
- MDN [클로저](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Closures)
- Poiemaweb [클로저](https://poiemaweb.com/js-closure)
- [번역] [자바스크립트 스코프와 클로저](https://medium.com/@khwsc1/%EB%B2%88%EC%97%AD-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%8A%A4%EC%BD%94%ED%94%84%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80-javascript-scope-and-closures-8d402c976d19)

