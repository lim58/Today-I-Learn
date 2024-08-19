# Reflow & Repaint

![image.png](Reflow%20&%20Repaint%20f36c1a0de9d74adb851b51ef57d671b5/image.png)

Reflow Repaint는 요소가 시각적으로 변경되면 변화를 계산하여 화면에 그려주는 작업

### Reflow

Layout 단계에서 수정이 발생하여 각 노드의 위치를 렌더 트리에 재 생성

요소들이 레이아웃에 영향을 주는 변화가 생길 시

요소의 너비 높이 위치 등이 변경될 시

EX) DOM 노드 추가 및 제거 / 요소 위치 크기 변경 / 폰트 텍스트 변경…

### Repaint

Reflow 하위 과정 (Reflow가 발생하면 repaint 발생)

요소의 스타일이 변경 되었을 시

EX) color / background-color / visibility…

---

**렌더링 최적화 하는 방법??**

1. cssText 속성을 편집
    
    ```jsx
    function Test() {
    	let element = document.getElementById("container")
    		
    	element.style.cssText = "background:red; width:200px"
    	
    	return false
    }
    ```
    
2. Fragment 사용 [**<Fragments> 태그**](https://www.notion.so/Fragments-2f1fab40753d4615aab4227763427b96?pvs=21) 
3. 계산된 스타일을 변수에 캐싱
    
    offset / scrollTop 같은 계산된 스타일 정보를 요청하면
    큐를 비우고 모든 변경사항을 적용하기 때문
    
    ```jsx
    let top = el.offsetTop;
    let left = el.offsetLeft;
    let elStyle = el.style;
    
    for (let i = 0; i < len; i++) {
      top += 10;
      left += 10; 
      elStyle.top = `${ top }px`; 
      elStyle.left = `${ left }px`;
    }
    ```
    
4. 영향받는 element 제한 (position fixed, absolute 활용)
5. <table> 레이아웃 피하기
6. IE의 CSS표현식을 사용하지 않기
7. 되도록 실행 사이클 안에 처리
8. 노드 복제
    
    변경하려는 요소의 노드를 복제한 후 복제된 노드에서 필요한 작업 실행
    
    ```jsx
    let element = document.getElementById("box1")
    let clone = element.cloneNode(true) // 원본 노드를 복제
    
    for(let i=0; i < 100; i++) {
        clone.style.width = i + "px";
    }
    
    //변경된 복제 노드를 DOM 트리에 반영하기 위해 기존 노드와 치환
    parentNode.replaceChild(clone, element);
    ```
    
    복제 노드는 DOM 트리에 추가된 상태 X 즉 reflow repaint 발생 X
    
    작업이 완료 된 후 변경 사항 적용
    

---

[리플로우, 리페인트와 브라우저 렌더링 알아보기](https://mong-blog.tistory.com/entry/리플로우-리페인트와-브라우저-렌더링-알아보기)

[Reflow, Repaint 와 7가지 렌더링 최적화방법](https://ekimnida.tistory.com/45)