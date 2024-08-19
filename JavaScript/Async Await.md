# Async Await

상태: 완료
작성일: 2024년 8월 18일 오후 10:10
작성자: LIM 
태그: Javascript

<aside>
💡 **자바스크립트 비동기 처리 방식 중 하나**

1️⃣ **async** 해당 함수가 비동기 함수임을 나타내고 Promise 객체로 반환함

2️⃣ **await** 기다려!! 비동기 함수의 실행 결과를 기다림

Promise의 상태가 변경될 때까지 코드 실행을 일시 중지함

</aside>

### async / await 기본 사용법

function 키워드 앞에 `async` 를 붙이고 비동기로 처리되는 부분 앞에 `await` 를 붙임

```jsx
async function getData() {
  const response = await fetch('/api');
  const data = await response.json();
  return data;
}
```

async / await은 비동기적 접근 방식을 **동기적으로 작성**할 수 있게 하여

코드가 간결해지고 가독성을 높여 유지보수를 용이하게 함

- Promise.then 핸들러 방식 코드 비교
    
    ```jsx
    //then 핸들러 방식
    fetch(url)
        .then(res => res.json())
        .then(data => {
          console.log(data);
    })
        
    //await 방식
    async function func() {
        const res = await fetch(url); 
        const data = await res.json();
        console.log(data);
    }
    func();
    ```
    

### async / await 에러처리

에러처리는 `try / catch` 문을 사용하여 처리함

```jsx
async function func() {
    try {
        const res = await fetch(url);
        const data = await res.json(); 
        console.log(data);
    } catch (err) { //에러처리
        console.error(err);
    }
}
func();
```

await을 막무가내로 사용하면 성능 및 기타 문제가 발생할 수 있음

병렬적으로 처리할 수 있는 작업을 억지로 동기적으로 처리하게 하기 때문