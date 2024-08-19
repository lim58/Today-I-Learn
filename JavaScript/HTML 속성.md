# HTML 속성

> **DOM 프로퍼티와 HTML 속성**
> 

브라우저는 html 표준 속성을 인식하고 DOM 프로퍼티를 생성함

비표준 속성은 DOM 프로퍼티로 전환되지 않음

- ⇒
    - **getAttribute ( )**  - 속성 값 가져옴
    - **setAttribute** **( )** - 속성 값 변경
    - **removeAttribute ( )**  - 속성 값 지움
    

```html
<!DOCTYPE html>
<html>
<body>

<button id="myButton" data-value="initial">Click me</button>

<script>
let button = document.getElementById("myButton"); // 요소 선택

let value = button.getAttribute("data-value"); // 속성 값 가져옴

console.log("현재 속성 값:", value);

button.setAttribute("data-value", "updated"); // 속성 값 변경
console.log("변경된 속성 값:", button.getAttribute("data-value"));

button.removeAttribute("data-value"); // 속성 제거
console.log("속성 제거 후 값:", button.getAttribute("data-value"));
</script>

</body>
</html>
```