---
title: Lodash 활용
thumbnail: images/gallery/thumbnails/lodash.jpg
categories:
  - develop
  - javascript
tags:
  - javascript
  - lodash
  - functional
  - 함수형
date: 2019-11-13 23:30:17
---


개인적으로 lodash를 사용한 코드를 더욱 정확하게 파악하기 위해 코드에서 사용한 Method들을 확인하는 용도로 정리하기 시작했습니다.  
기본적인 Method를 정리 후 추가로 사용된 Method가 있을때마다 업데이트 하도록 하겠습니다.

<br/>

# Lodash
[Lodash](https://lodash.com/docs/4.17.15#findIndex)는 underscore에서 성능을 개선한 라이브러리로 사이드 이펙트가 없는 즉 외부 상태를 바꾸지 않는 순수 함수를 사용하는 함수형 프로그래밍으로 되어있다.

<br/>

## 함수형 프로그래밍
> 함수형 프로그래밍은 계산결과를 표현의 평가로서 모델링하는 프로그래밍 스타일이다. 따라서 실행될 때 전역 상태를 변경하는 명령문으로 구성된 명령형 프로그래밍과 대조를 이룬다. 함수형 프로그래밍은 일반적으로 변경가능한 상태를 사용하지 않고 사이드 이펙트 없는 함수와 불변 데이터를 대신 사용한다.

중요한 점은 함수는 반드시 사이드 이펙트가 없어야 한다는 것이다. 그렇게 될 경우 테스트, 유지 보수, 그리고 대부분 예측가능한 것들이 쉬워진다.

<br/>
<!-- more -->


---

<br/>

## Array

### filter
```javascript

```

<br/>

### head(first)
첫번째 요소를 가지고 온 뒤 나머지 요소를 버리는 등 여러 방식으로 사용할 수 있다.
```javascript
const names = ["first", "middle", "last", "suffix"]

const firstName = _.head(names) 

const [firstName, ...otherNames] = names
console.log(firstName) // 'first'
```

<br/>


### each
```javascript
_.each([1, 2, 3], (value, index) => {
  console.log(value)
})

[1, 2, 3].forEach((value, index) => {
  console.log(value)
})

_.forEach({ 'a': 1, 'b': 2 }, (value, key) => {
  console.log(key);
});

({ 'a': 1, 'b': 2 }).forEach((value, key) => { // !error
  console.log(key); 
});
```

<br/>

### every
배열의 모든 요소가 특정한 조건을 만족하는지 테스트한 결과를 반환한다. (네이티브 함수가 더 빠르다)
```javascript
const elements = ["cat", "dog", "bat"]
_.every(elements, el => el.length == 3)
elements.every(el => el.length == 3) //true
```

<br/>

### some
배열의 요소중 하나라도 특정한 조건을 만족하는지 테스트한 결과를 반환한다.
```javascript
const elements = ["cat", "dog", "bat"]
_.some(elements, el => el.startsWith('c'))
elements.some(el => el.startsWith('c'))
```

<br/>

### includes
콜렉션에 해당 요소를 갖고 있는지를 확인한다.
```javascript
const primes = [2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,97]
_.includes(primes, 47) // true
primes.includes(79) // true
```

<br/>

### uniq   
배열의 요소들중 중복값을 제거한 결과를 반환한다.
```javascript
var elements = [1,2,3,1,2,4,2,3,5,3]
_.uniq(elements) //  [1,2,3,4,5]
[...new Set(elements)] //  [1,2,3,4,5]
```

<br/>

### compact   
배열에서 undefined혹은 falsy 값을 제거하는 유용한 함수이다.
```javascript
var array = [undefined, 'cat', false, 434, '', 32.0]
_.compact(array)
array.filter(Boolean)
```

<br/>

### reverse
```javascript
var array = [1, 2, 3];
 
_.reverse(array);
// => [3, 2, 1]
 
console.log(array);
// => [3, 2, 1]
```

<br/>

## Collection

<br/>

## Date

<br/>


## Function

<br/>


## Math

<br/>


## Number

<br/>


## Object

<br/>


## Seq

<br/>


## String

<br/>


## Util