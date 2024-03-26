# DOM

## 문서 객체 모델 Document Object Model, DOM

DOM은 일종의 인터페이스로 해당 요소를 나타내는 노드,

노드의 속성을 나타내는 프로퍼티와 이를 조작할 수 있는 여러 메서드를 담아 구조화한 객체로 표현함

**DOM을 통해 해당 요소에 접근해 구조나 내용, 스타일을 변경할 수 있음**

DOM API는 Document를 통해 사용할 수 있음

Document는 DOM 트리의 진입점이자 브라우저가 불러온 웹 페이지를 의미하는 Document 인터페이스를 의미

## DOM 트리

**DOM 문서를 노드의 계층적인 트리 구조로 나타냄**

노드 트리의 최상위 노드를 root라 하며 일반적으로 HTML 문서에서 <html>이 root 노드가 됨

트리의 시작점은 Document 

각각 노드의 타입에 따라 `요소 노드` `텍스트 노드` `어트리뷰트 노드` 등으로 분류되어 계층 구조를 가짐

![Untitled](DOM%20741542605eba4708aa48aec365b9d88c/Untitled.png)

## Node

**노드 인터페이스는 전체 문서의 요소들에 대한 객체 형태의 기본 데이터 타입**

DOM 트리의 구성 요소를 나타내며

- `nodeType nodeName nodeValue 자식 노드와 형제 노드에 대한 관계` 등 여러 정보를 갖음
    
    
    - nodeType - 12개의 노드 타입을 정수로 나타냄
    - nodeName - 노드의 이름
    - nodeValue - 노드의 값
    
    ![Untitled](DOM%20741542605eba4708aa48aec365b9d88c/Untitled%201.png)
    
    - parentNode - 부모 노드를 반환함
    - childNodes - 요소의 자식 노드를 반환
    - firstChild - 자식 노드 중 첫번 째 자식 반환
    - lastChild - 자식 노드 중 마지막 자식 반환
    - nextSilbling - 부모의 childNodes 목록 중 자신 다음에 있는 노드 반환
    - previousSibling - 부모의 childNodes 목록 중 자신 이전에 있는 노드르 반환
    

 

![Untitled](DOM%20741542605eba4708aa48aec365b9d88c/Untitled%202.png)

**EventTarget은 이벤트가 발생했을 때 대상이 되는 타깃을 의미함**

> HTML 요소를 다룰 때 Element 와 HTMLElement 클래스를 사용함
> 

**Element는 DOM 요소 생성의 가장 기본이 되는 클래스**, 요소를 조작하고 탐색하는데 사용함

요소 탐색 (querySelector, getElementsByName …) 

이벤트 리스너 관리 (addEventListener, removeEventListener …) 여러 매서드를 제공함

**HTMLElement는 Element를 상속받아 HTML 요소를 구현한 기본 클래스**

HTMLElement를 상속받아 

HTMLDivElement, HTMLInputElement, HTMLLabelElement 등 다양한 HTML 요소를 구현하게 됨

