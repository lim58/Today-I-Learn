# callBack함수 & Promise

상태: 정리 전
작성일: 2024년 8월 18일 오후 10:07
작성자: LIM

## callBack함수??

다른 함수가 실행을 끝낸 뒤 실행되는 callBack되는 함수

즉 매개변수로 함수 객체를 전달하여 **호출 함수 내에서 매개변수 함수를 실행**하는 것

```jsx
functio func(callback) { 
	callback(); //매개변수의 함수(콜백함수) 호출
}
function callback() {
	console.log("callback이다");
}

func(callback); //결과:callback이다
```

함수 호출을 통해 비동기 작업 결과를 받아서 인자로 주면 이를 가지고 후속 처리가 가능함

but 여러개의 비동기 작업을 순차적으로 수행 할 때 **콜백지옥 발생⚠️**

콜백지옥? 콜백함수가 중첩되어 코드 깊이가 깊어지는 현상 

(코드 복잡해지고 가독성 떨어짐 👎)

![image.png](callBack%E1%84%92%E1%85%A1%E1%86%B7%E1%84%89%E1%85%AE%20&%20Promise%2050c7eb2700044e92ae9a786401134fdc/image.png)

프로미스를 사용하면 콜백함수를 대체하고 비동기 작업의 흐름을 쉽게 제어할 수 있음😆

## Promise!!

Promise객체를 생성하려면 new 키워드와 Promise 생성자 함수를 사용

`resolve(성공)` & `reject(실패)` 매개 변수를 가진 콜백함수를 넣음

```jsx
const myPromise = new Promise((resolve, reject) => {
    const data = fetch('서버로부터 요청할 URL');
    
    if(data)
    	resolve(data); //요청 성공시 실행
    else
    	reject("Error"); //요청 실패시 실행
})
```

<aside>
💡 **Promise 상태 정보**

✋ Pending 대기 → 처리 진행 중

✅ Fulfilled 이행 → 성공적으로 처리가 완료된 상태

⛔️ Eejected 거부 → 처리가 실패로 끝난 상태

</aside>

비동기 작업 완료 이후 작업을 연결시킬 수 있음

결과에 따라 `then` `catch` 메소드 체이닝을 통해 성공과 실패에 대한 후속 처리를 진행함

```jsx
new Promise((resolve, reject) => {
		.then(() => {
        console.log("성공시 실행, 다음 핸들러 실행")
    })
    .then(() => {
        console.log("프로미스로 객체로 반환되기에 체이닝 가능!")
    });
    .catch((error) => {
      console.log("예외 발생시 실행);
    })
 })
```

**프로미스 체이닝?** 프로미스 핸들러를 연달아 연결하는 것

여러 개의 비동기 작업을 순차적으로 수행할 수 있음