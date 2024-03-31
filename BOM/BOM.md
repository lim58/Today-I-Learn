# BOM

**브라우저 객체 모델 (Browser Object Model, BOM)**

웹 브라우저와 관련된 객체 모델을 의미함

# window 객체

브라우저에서 제공하는 여러 가지 기능들은 window 인터페이스를 통해 사용할 수 있음

![Untitled](BOM%20d56bac307739499199136558411dab7c/Untitled.png)

window 인터페이스는 일반적으로 두가지 의미가 있음

1. **브라우저 환경에서의 자바스크립트 전역 객체를 의미함**
2. **브라우저 창을 의미함**

---

## History객체

History 객체는 현재 브라우저의 세션 기록을 갖고 있음

(현재 문서의 탭이나 프레임에서의 방문기록)

```jsx
세션 기록 내에서 앞으로 이도하려면 forward 뒤로 가려면 back
history.forward()
history.back()

현재 위치를 기준으로 오프셋에 해당하는 숫자를 넣어 위치를 이동함
history.go(1) // 현재 위치를 기준으로 앞으로 1페이지 이동
history.go(0) // 현재 페이지를 새로고침

브라우저의 세션 기록에 상태를 추가
새로운 세션으로 넘겨줘야 할 정보를 나타내는 state, 이동할 페이지의 title, 이동할 페이지의 url 매개변수로 가짐
Http 호출을 만들지 않아 페이지의 존재 여부와 상관 없이 추가됨
const state = { userId : 123 }
const title = ""
const url = "/docs/1"

history.pushState(state, title, url)

브라우저의 현재 세션 기록을 인자로 넘어온 상태로 대체함
현재 세션이 대체됨
const state = { userId : 123 }
const title = ""
const url = "/docs/1"

history.replaceState(state, title, url)

같은 문서에 대해 히스토리 엔트리가 변화할 때 발생하는 이벤트
브라우저의 버튼을 눌러 페이지를 이동하거나 go back forward 같은 API를 호출할 때 발생함
// popstate 이벤트
```

## Location 객체

Location 객체는 현재 페이지의 URL, 프로토콜, hostname, 포트 번호 등 위치에 관련된 정보를 포함함

```jsx
매개변수에 해당하는 URL로 이동함
location.assign("https://test.com")

매개변수에 해당하는 URL로 이동함
현재 페이지에 대한 history 스택이 초기화됨
location.replace("https://test.com")

현재 URL 리소스를 다시 불러옴
location.reload()
```

## navigator 객체

Navigator 인터페이스의 navigator 객체는 클라이언트의 ID 및 상태를 나타냄

window.navigator로 객체에 접근할 수 있으며 

사용자의 브라우저 이름과 벤더사, 모바일 사용 여부, 버전 등의 정보를 가짐

---

# Web Storage

Web Storage는 클라이언트 측에 `이름 : 값` 쌍의 데이터를 저장하는 두 가지 매커니즘을 의미함

```jsx
- getItem (key) 키에 해당하는 값을 얻음
- setItem (key, value) 키에 해당하는 값을 설정
- removeItem (key) 키에 해당하는 값을 삭제
- clear ( ) 저장된 모든 키-값 쌍을 제거함
- key (index) index에 해당하는 키를 얻음
```

값은 항상 문자열이며 다른 타입의 값을 넣어도 문자열 형태로 타입이 변환되어 저장됨

**localStorage과 sessionStorage**

localStorage는 origin이 같을 경우 여러 탭과 창에서 공유됨

세션 이후에도 지속되는 저장소 용으로 설계되어 컴퓨터를 종료하거나 브라우저를 종료하더라도 지속됨

sessionStorage는 한 탭에서 페이지의 세션이 유지되는 동안 origin별로 스토리지를 관리함

페이지가 열린 동안은 페이지 리로딩 혹은 복원 시 데이터가 유지되지만 

다른 세션이나 창이 종료되 경우 데이터에 접근할 수 없음