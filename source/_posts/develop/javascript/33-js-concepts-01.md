---
title: 자바스크립트 개발자라면 알아야하는 핵심 컨셉 33 (1~5)
thumbnail: images/gallery/thumbnails/javascript.png
categories:
  - develop
  - javascript
tags:
  - ES6
  - javascript
  - call stack
  - Primitive Types
  - Reference Types
date: 2019-10-11 17:31:19
---

# 1. Call Stack
여러 함수들(functions)을 호출하는 스크립트에서 해당 위치를 추적하는 인터프리터 (웹 브라우저의 자바스크립트 인터프리터같은)를 위한 메커니즘. 
현재 어떤 함수가 동작하고 있는지, 그 함수 내에서 어떤 함수가 동작하는지, 다음에 어떤 함수가 호출되어야 하는지 등을 제어.
- 스크립트가 함수를 호출하면 인터프리터는 이를 호출 스택에 추가한 다음 함수를 수행하기 시작.
- 해당 함수에 의해 호출되는 모든 함수는 호출 스택에 추가되고 호출이 도달하는 위치에서 실행.
- 메인 함수가 끝나면 인터프리터는 스택을 제거하고 메인 코드 목록에서 중단된 실행을 다시 시작.
- 스택이 할당된 공간보다 많은 공간을 차지하면 "stack overflow" 에러가 발생.

<!-- more -->

```javascript
function three() {
  console.log('I love JS');
}

function two() {
  three();
}

function one() {
  two();
}

function zero() {
  one();
}

zero();
```

`callstack`
```
0. empty 스택
1. zero() 스택 삽입
2. zero() => one() 스택 삽입
3. zero() => one() => two() 스택 삽입
4. zero() => one() => two() => three() 스택 삽입
5. zero() => one() => two() => three() => console.log() 실행완료
6. zero() => one() => two() => three() 스택에서 제거
7. zero() => one() => two() 스택에서 제거
8. zero() => one() 스택에서 제거
9. zero() 스택에서 제거
10. empty 스택
```

## reference
- [MDN Callstack](https://developer.mozilla.org/ko/docs/Glossary/Call_stack)
- [Nomadcoders](https://www.youtube.com/watch?v=QkFkFqg-J04&list=PL7jH19IHhOLMmmjrwCi7-dMFVdoU0hhgF&index=10)

<br/>

# 2. Primitive Types
Primitive Types는 원시 자료형 또는 기본 자료형으로 자바스크립트의 기본이 되는 자료형을 의미. 

## Number
- 숫자의 자료형을 의미. 
- 숫자가 아님을 뜻하는 NaN(Not a Number)도 숫자 자료형.  

```javascript
typeof 1 // "number"
typeof NaN // "number"
Math.pow(2, 'abc') //NaN
```

<br/>

## String  
- 자바스크립트 문자열을 의미하며, 텍스트 데이터를 나타내는데 사용. 
- ", ' 또는 ` 기호 안에 텍스트를 기입하는 방식으로 사용하며 시작한 기호로 끝내야 한다.

```javascript
"Hello"
'Hi'
`Nice`
```
- " " 안에 ' ' 쌍을 쓸 수 있습니다. 하지만 " " 쌍 안에 " "를 쓰려면 역슬래쉬로 이스케이프(escape) 해야 한다.

```javascript
"Hello \"Javascript\" "
```

<br/>

## Boolean
- 논리적인 요소를 나타내는 타입으로 true(참)와 false(거짓)이 있음. 
- 만약 "true"와 "false"로 쓰면 이는 문자형으로 인지됨.

```javascript
"Hello" === "Hi" //false
typeof true //"boolean"
typeof "true" //"string"
```

<br/>

## Null
- Null은 존재하지 않음이라는 정의를 한 것.

<br/>

## Undefined
- 정의 자체를 하지 않은 것을 의미.

```javascript
typeof null === typeof undefined //false
```

<br/>

## Symbol(ES6에서 추가)
- 심볼(symbol)은 ES6에서 새롭게 추가된 7번째 타입으로 변경 불가능한 원시 타입의 값. 
- 주로 이름의 충돌 위험이 없는 유일한 객체의 프로퍼티 키(property key)를 만들기 위해 사용.

```javascript
let mySymbol = Symbol();
console.log(mySymbol);        // Symbol()
console.log(typeof mySymbol); // symbol
```
```javascript
const obj = {};

const mySymbol = Symbol('mySymbol');
obj[mySymbol] = 123;

console.log(obj); // { [Symbol(mySymbol)]: 123 }
console.log(obj[mySymbol]); // 123
```

## Reference
- [MDN data types](https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures#Primitive_values)
- [7번째 타입 심볼(Symbol)](https://poiemaweb.com/es6-symbol)

<br/>

# 3. Value Types and Reference Types
![Value Types and Reference Types](/images/develop/javascript/33-js-1.png)

## Value Types
- 원시타입(Value Types or primitive type) : Number, String, Boolean, Null, Undefined, Symbol
- 원시 타입 데이터는 변수에 할당될 때 메모리 상에 고정된 크기로 저장되고 해당 변수가 원시 데이터의 값을 보관한다. 
- 원시 타입 자료형은 모두 변수 선언, 초기화, 할당시 값이 저장된 메모리 영역에 직접적으로 접근한다, 즉 변수에 새 값이 할당 될 때 변수에 할당된 메모리 블럭에 저장된 값을 바로 변경한다는 뜻이다.
![Value Types](/images/develop/javascript/33-js-2.png)

## Referunce Types
- 참조타입(reference type) : Object, Array, Function
- 참조 타입 데이터는 변수에 할당될 때 값이 직접 해당 변수에 저장될 수 없으며, 변수에는 데이터에 대한 참조, 즉 변수의 값이 저장된 힙(Heap) 메모리의 주소값을 저장한다. 
- 참조 타입은 변수의 값이 저장된 메모리 블럭의 주소를 가지고 있고, 자바스크립트 엔진이 변수가 가지고 있는 메모리 주소를 이용해서 변수의 값에 접근한다
![Referunce Types](/images/develop/javascript/33-js-3.png)

<br/>

# 4. Type Coercoin
동적 타입 언어인 자바스크립트는 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다. 
이를 암묵적 타입 변환(Implicit coercion) 또는 타입 강제 변환(Type coercion)이라고 한다.

<br/>

## String
- 위의 + 연산자는 피연산자중 문자열이 있으면 문자열의 연결 연산자로 동작한다. 
- 때문에 4 (Number) -> '4' (String)의 묵시적 형변환이 일어난다.
```javascript
console.log(4 + "hello"); //4hello
console.log(4 + 4 + "hello"); //8hello
console.log(1 + ''); // "1"
```

<br/>

## Number
- '-', '*', '/' 등의 산술연산자는 피연산자가 숫자가 아니면 숫자 타입으로 묵시적 형변환 후 연산한다.
```javascript
console.log(1 - '1'); //0
console.log(+'0'); // 0
```

<br/>

## Boolean : Truthy 값(참으로 인식할 값) 또는 Falsy 값(거짓으로 인식할 값)
JavaScript에서는 아래의 값들은 모두 falsy이고, 이를 제외한 모든 값들은 truthy다.
- false
- undefined
- null
- 0, -0
- NaN
- ’’ (빈문자열)
```javascript
console.log("" == true); //false
console.log(1 == true); //true
console.log(true + ''); // "true"

console.log(+true); // 1
console.log(true * 1); // 1
console.log(66 + true); //67
```

<br/>

# 5. == vs === vs typeof

## typeof
변수의 데이터 타입을 반환하는 연산자.
- undefined : 변수가 정의되지 않거나 값이 없을 때
- number : 데이터 타입이 수일 때
- string : 데이터 타입이 문자열일 때
- boolean : 데이터 타입이 불리언일 때
- object : 데이터 타입이 함수, 배열 등 객체일 때
- function : 변수의 값이 함수일 때
- symbol : 데이터 타입이 심볼일 때

<br/>

## ==
두 가지를 비교할 때 유형 변환을 수행하고 IEEE 754를 준수하기 위해 NaN, -0 및 +0을 특별히 처리합니다 (NaN != NaN, -0 == +0)
```javascript
var num = 0;
var obj = new String("0");
var str = "0";
var b = false;

console.log(num == num); // true
console.log(obj == obj); // true
console.log(str == str); // true

console.log(num == obj); // true
console.log(num == str); // true
console.log(obj == str); // true
console.log(null == undefined); // true

// 둘 다 false, 드문 경우를 제외하고는
console.log(obj == null);
console.log(obj == undefined);
```

<br/>

## ===
이중 equals (NaN, -0 및 +0의 특수 처리 포함)와 동일한 비교를 수행하지만 유형 변환은 수행하지 않습니다. 형식이 다른 경우 false가 반환됩니다.
```javascript
var num = 0;
var obj = new String("0");
var str = "0";
var b = false;

console.log(num === num); // true
console.log(obj === obj); // true
console.log(str === str); // true

console.log(num === obj); // false
console.log(num === str); // false
console.log(obj === str); // false
console.log(null === undefined); // false
console.log(obj === null); // false
console.log(obj === undefined); // false
```

<br/>

## Object.is
형식 변환을하지 않으며 NaN, -0 및 +0에 대한 특수 처리를 수행하지 않습니다 (특수 숫자 값을 제외하고는 ===와 동일한 동작을 제공함).

