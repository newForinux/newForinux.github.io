---
layout: post
title: 유용한 자바스크립트 테크닉
tag: [프론트엔드 삽질 여행]
image: 
  path: /assets/img/blog/js_shorthands.png
description: >
  지름길을 통한 테크닉 쌓기
sitemap: false
---

코드 작성 시간을 줄여주는 몇 가지 팁 (또는 트릭😁)을 정리한다.

<br />

## `includes`
if 조건문 내에서 여러 OR(`||`)을 사용할 경우, `includes`로 간결하게 작성할 수 있다.

~~~js

if (conditions === null || condition === undefined || condition === '') { ... }

// shorthand
if ([ null, undefined, '' ].includes(conditions)) { ... }
~~~

<br>

## 여러 값 한번에 할당
~~~js
let elem1 = 1;
let elem2 = 2;
let elem3 = 3;

// shorthand
let [elem1, elem2, elem3] = [1, 2, 3];
~~~

<br>

## String을 숫자로
~~~js
let intg = parseInt('99');
let flt = parseFloat('3.141592');

// shorthand
let intg = +'99';
let flt = +'3.141592';
~~~

❗ 단, `parseInt` 함수는 문자열의 숫자를 뽑아낼 수 있으나, `+`는 숫자 외에 문자가 포함되어 있다면 `NaN`을 반환하므로 유의

<br>

## Nullish Coalescing Operator
`??` 논리 연산자로, 어느 한 쪽 피연산자가 `null` 또는 `undefined`일 때 그 반대 피연산자를 반환한다.

만약 둘 다 아니라면, 왼쪽 피연산자를 반환한다.

~~~js
const cond = null ?? 'Typescript';

// 'Typescript'
console.log(cond);

const condt = 'Javascript' ?? 'Typescript';

// 'Javascript'
console.log(condt);
~~~

OR 연산자 (`||`) 또한 사용할 수 있는데, 왼쪽 피연산자가 `null`, `undefined`, `0`, `false`, `Empty (비어 있는 값)`이면 오른쪽 피연산자를 반환한다.

<br>

## 배열에서 유일한 값 추출
중복을 허용하지 않는 자료구조 `Set`을 활용한다.

~~~js
const langs = ['Javascript', 'Python', 'Java', 'Java', 'Python', 'HTML'];

const uniqLangs = [ ...new Set(langs) ];

// ["Javascript", "HTML"]
console.log(uniqLangs);
~~~

<br>

## 자릿수의 숫자 추출
전개 연산자, `map`, `parseInt`를 사용해 정수의 각 자릿수를 배열로 만들 수 있다.

~~~js
const toArr = num => [ ... `${num}`].map(digit => parseInt(digit));

// [1, 2, 9, 9, 5]
console.log(toArr(12995)) 
~~~

<br>

## 배열 초기화 방법
~~~js
let arr = [1, 2, 3, 4, 5];

// 1. 빈 배열 할당
arr = [];


// 2. 길이 0으로 설정
arr.length = 0;


// 3. splice 함수 사용
arr.splice(0, arr.length);

// 모두 삭제한다면 2번째 인자 생략 가능
arr.splice(0);
~~~
