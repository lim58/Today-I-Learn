# localStrorage

**브라우저 상에서 데이터 저장**

여러 탭이나 창 사이에 데이터가 공유 됨

탭이나 창을 닫아도 데이터는 브라우저에 그대로 남아있음

localStrorage 영속성? 

동일한 컴퓨터에서 같은 브라우저를 사용할때만 저장

브라우저나 OS가 재 시작하더라도 데이터가 파기되지 않음

**기본적으로 key와 value로 이루어진 데이터를 저장**

```jsx
localStorage.setItem("key", value) //데이터 보관

localStorage.getItem("key") //데이터 읽기

localStorage.removeItem("key") //키의 데이터 삭제

localStorage.clear(); //모든 키의 데이터 삭제
```

- **사용 시 주의해야될 점 🚨**
    
    `문자형 string` 데이터 타입만 지원
    
    ```jsx
    localStorage.setItem('num', 1) //undefined
    
    localStorage.getItem('num') //"1"
    typeof localStorage.getItem('num') //"string"
    ```
    
    **객체와 배열 형태의 데이터를 저장하려면?**
    
    데이터를 JSON 형태로 직렬화 하고 
    
    읽은 데이터를  JSON 형태로 역직렬화하면 원본 데이터를 그대로 얻을 수 있음
    
    ```jsx
    localStorage.setItem('json', JSON.stringify({a: 1, b: 2})) //undefined
    JSON.parse(localStorage.getItem('json')) //{a: 1, b: 2}
    ```