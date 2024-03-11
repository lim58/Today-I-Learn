# DOM 노드

---

> **주요 노드 프로퍼티**
> 

---

> **innerHTML**
> 

요소 안 HTML을 문자열 형태로 받아올 수 있음

요소의 내용을 변경할 수 있음

```html
<div id = "area1">
     js에서 태그 엘리먼트 값을 읽거나 변경 시 사용
</div>
<button onclick = "checkValue();"> innerHTML 확인 </button>

<script>
   function checkValue ( ) {
     let divEl = document.getElementById ('area1'); //요소 접근
        alert(divEl.innerHTML); // alert 출력 (초기상태)

            divEl.innerHTML = "innerHTML 속성으로 값 변경함"; } // 값 변경 (버튼클릭)
</script>

```

HTML 구문 해석 X 

---

> **outerHTML**
> 

innerHTML에 요소 자체를 더한 것

```html
<div id="area2">
   area2 영역입니다.
</div>
    
<script>
    let area2 = document.querySelector("#area2");
      console.log(area2.outerHTML);
</script>

//// 출력 ////
 <div id = "area2">
   area2 영역입니다.
 </div>
```

DOM 안의 요소를 교체함 (html 요소 자체가 바뀌지 않음)

할당 연산이 DOM 요소를 수정하지 않기 때문

<aside>
🧾 div.outerHTML = …

</aside>

 문서에서 div를 삭제함 → 새로운 html 조각을 삭제한 후 생긴 공간에 삽입

---

> **textContent**
> 

요소 내 텍스트에 접근할 수 있음

<태그> 제외, 텍스트 추출

```html
<div id="area3">
   <p>area3 영역</p>
   <p>문단을 나누어봅니다</p>
</div>
<div id="area4"></div>
<div id="area5"></div>

<script>
   let area3 = document.getElementById('area3');
    console.log(area3.textContent); 
      
       // area3 영역
       // 문단을 나누어봅니다

     let input = prompt("값을 입력하세요", "<p><b>강조할거에요</b></p>");
     let area4 = document.querySelector("#area4");
     let area5 = document.querySelector("#area5");
        area4.innerHTML = input;
        area5.textContent = input;

        // 강조할거에요
        // <p><b>강조할거에요<b><p> 특수문자가 문자열로 처리됨

        // innerHTML 사용자가 입력한 문자열이 HTML 형태로 태그와 같이 저장
        // textContent 사용자가 입력한 문자열이 텍스트 형태로 저장
</script>
```