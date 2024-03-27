# DOM 이벤트

이벤트는 어떠한 일이 발생했을 때 그 시점에 발생하는 신호를 의미함

DOM 에서는 요소를 클릭하거나 특정 키를 입력했을 때처럼 다양한 상황에서 이벤트가 발생함

---

# Event 객체

**Event 객체는 DOM 내에서 발생한 이벤트에 대한 정보를 담고 있음**

![Event 객체에 담긴 프로퍼티들…](DOM%20%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%20798c59a585324e9d9d922d4fe29a6de5/Untitled.png)

Event 객체에 담긴 프로퍼티들…

### target과 currentTarget

이벤트가 발생한 요소에 접근하고 싶은 경우 target 혹은 currentTarget 프로퍼티를 통해 접근할 수 있음

**target** - 이벤트가 처음 발생했던 대상 DOM 요소의 참조를 갖음

**currentTarget** - 발생한 이벤트가 등록된 DOM 요소의 참조를 갖음

### stopPropagation preventDefault

Event 를 제어할 수 있는 메서드

preventDefault - 이벤트를 취소할 수 있는 경우 이벤트를 취소함, 현재의 이벤트의 기본 동작만 중단함

stopPropagation - 기본 동작을 중단하지는 못하지만 이벤트가 전파되는 것을 막음

---

# 이벤트 종류

### **User Interface 이벤트**

이벤트 문서나 요소의 조작 시 발생하는 이벤트

<aside>
🧥 
**load** 문서나 종속된 리소스가 완전히 로드될 때

**unload** 문서나 종속된 리소스가 완전히 제거될 때

**abort** 리소스가 중단된 경우

**error** 리소스가 로드되었지만 유효하지 않을 때, 스크립트 실행 오류, 잘못된 형식 등 에러 발생 시

**select** <input> <textarea> 요소 안에 작성된 텍스트를 선택할 경우 발생

</aside>

### **Focus 이벤트**

이벤트 대상이 포커스를 받거나 잃을 때 발생하는 이벤트

<aside>
🔭 
**focusin** 포커스를 받으려 할 때 

**focusout** 포커스를 잃으려 할 때 

**focus** 대상이 포커스를 받을 때

**blur** 대상이 포커스를 잃을 때

</aside>

### **마우스 이벤트**

마우스 같은 입력장치 탐지하여 이벤트 발생

<aside>
🐁 
**mousedown** - 타깃을 눌렀을 때 발생

**mouseup** - 타깃의 위에서 눌렀던 포인트가 해제될 때

**click** - 타깃에 클릭 동작을 했을 경우 (mousedown mouseup 이벤트가 발생한 뒤 발생)

**dblclick** - 더블 클릭을 했을 경우

**mousemove** - 타깃 내에서 포인터가 이동할 경우

**mouseenter** - 타깃 밖에서 타깃으로 처음 포인터가 이동할 때 

**mouseleave** - 타깃 밖으로 이동할 때 발생

**mouseover** - mouseenter와 동일한 조건에서 발생

**mouseout** - mouseleaver와 동일한 조건에서 발생

</aside>

### **Input 이벤트 & 키보드 이벤트**

편집 가능한 영역에서 키보드 입력이나 삭제, 서식 지정 등을 통해 DOM 요소가 업데이트 될 때 발생하는 이벤트

키보드를 누르는 시점과 떼는 시점에 따라 이벤트가 발생함

<aside>
⌨️ 
**beforeInput** - 입력 후 DOM 요소에 업데이트 되기전 발생

**Input** - 입력 후 DOM 요소에 업데이트된 뒤 바로 발생

**keydown** - 키보드를 누를 때 발생

**keyup** - 누른 키를 뗄 때 발생

</aside>

---

# 이벤트 리스너 추가하기

### **HTML 요소에 속성으로 할당하는 방법**

```html
<button onclick = "alert("안녕안녕")" > 버튼이에뇽 </button>
<button id="button-id" onclick="clickEventHandler(event)"> 클릭하쇼! </button>

<script>
	function clickEventHandler(e) {
		console.log("클릭했습니다"))
	}
</script>
```

### **DOM 프로퍼티 할당하는 방법**

```html
<button id="button-id"> 얼러트 띄우기 </button>
<script>
	document.getElementById("button-id").onclick = (event) => {
		alert("안녕안녕")
	}
</script>
```

### **addEventListener 💘**

이벤트 타입에 여러 개의 리스너를 등록 할 수 있음

이벤트 리스너에 발생한 이벤트 정보가 담긴 Event 객체가 매개 변수로 포함됨

```jsx
function sayHello() {
 alert("hello")
}

document.addEventListener("click", sayHello)
document.removeEventListener("click", sayHello)
```

할당한 이벤트를 해제 하려면 `removeEventListener` 매서드를 사용함

---

# 버블링과 캡쳐링

계층적 구조를 가진 DOM에 이벤트가 발생할 경우 연쇄적으로 이벤트 전파됨

이벤트가 전파되는 방향에 따라 버블링과 캡쳐링으로 구분됨

### 버블링 (Bubbling)

DOM 요소에 이벤트가 발생할 경우 부모 요소로 올라가며 차례대로 이벤트가 전파되는 것

### 캡쳐링 (Capturing)

DOM 요소에 이벤트가 발생할 경우 가장 상위의 부모 요소부터 자식 요소로 내려가며 이벤트가 전파되는 것