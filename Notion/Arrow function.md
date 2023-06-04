# Arrow Function

생성일: 2023년 5월 22일 오후 7:07

**화살표 함수 :**

기존의 함수표현식에서  function  키워드를 삭제하고 

인자를 받는 매개변수의 `괄호 ()` `코드블록{}` 사이에 `화살표 ⇒`를 넣어줌

---

```jsx
let sum = (a,b) => {
  return a+b;
}

const sum = (a,b) => a+b;
// ( 매개변수 ) => { 본문 } 
```

```jsx
let func = function (arg1, arg2, ...argN) {
   return expression; 
};

let func = (arg1, arg2, ...argN) => expression
```

화살표 함수 사용시 축약이 가능함

---

> **중괄호 없이 작성 ( …args ) ⇒ expression**                                                                                     함수는 표현식을 평가하고 결과값을 반환함
> 

```jsx
let sum = (a,b) => a + b;
// (a,b) => a+b 실행 시 표현식 a+b를 평가하고 값을 반환함

alert (sum (1,2)); 
```

함수 몸체가 한줄의 구문이고, return 문 밖에 없다면 중괄호 return 키워드 생략가능

```jsx
x => { return x * x}
x => x * x
```

---

> **중괄호 같이 작성 ( …args ) ⇒ { body }**                                                                                         본문이 여러줄로 구성되었다면 중괄호 사용
> 

```jsx
let sum (a,b) => {
  let result = a+b;
   return result; 
   //중괄호를 사용했다면, return 지시자로 결과값을 반환해야함
};

alert (sum (1,2)); 
```

---

**매개변수 표현**

- 매개변수가 없을 경우  ( ) => { ... }
- 매개변수가 한 개인 경우,  소괄호 생략   a => { ... }
- 매개변수가 여러 개인 경우, 소괄호 생략 불가  (a, b) => { ... }

```jsx
let sayHi = () => alert ("안녕하세요");

sayHi();
```

**객체 리터럴 반환**

객체 반환시 소괄호를 사용함

```jsx
() => { return { a : 1 }; }
() => ({ a : 1 }) 
```

---

- 화살표 함수 제약
    - 일반 객체의 메소드 사용
    - prototype 메소드로 사용 x
    - 생성자 함수로 사용 x
    - 화살표 함수는 call, apply, bind 메소드를 사용하여 this 변경 불가

`**this`  `super`  `arguments`  [`new.target`](http://new.target) 등을 바인딩 하지않음**

화살표 함수는 함수 스코프 생성, 실행컨텍스트 생성시 this를 바인딩하지 않음

```jsx
const obj = {
  a : function() {
    console.log(this);  //obj

    const b = function() {
      console.log(this);  //this 바인딩하는 객체가 window
     };
     b();
   }
 };

obj.a();

const obj2 = {
  a : function() {
    console.log(this);  //obj
  
    const b = () => {  //this를 바인딩하는 동작 자체를 하지 않음
      console.log(this);
     };
     b();
   }
 };

obj2.a();
```

(화살표 함수는 자신만의 고유의 this가 없기 때문에 외부의 this를 따름)

`**call` `apply` 메소드는 본연의 기능은 수행하지만 제약이 있어 주의해야함**

```jsx
// 기존 함수 선언문
function sum (...arg) {
  console.log (this);
   return arg.reduce ( (p,c) => p+c );
 }

console.log ( sum (1,2,3,4,5) );
 sum.call ( {}, 1,2,3,4,5 );

// 화살표 함수를 사용한 경우
const sum2 = (...arg) => {
  console.log (this);
   return arg.reduce ( (p,c) => p+c);
 };

console.log ( sum2 (1,2,3,4,5) );
sum2.call ( {}, 1,2,3,4,5);
```

---

ex ))

```jsx
let age = prompt ("나이를 알려주세요", 18);

let welcome = (age < 18) ?
  () => alert ('안녕') :
  () => alert ("안녕하세요");

welcome();
```