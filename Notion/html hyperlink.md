# html hyperlink

생성일: 2023년 4월 10일 오후 10:00

### **하이퍼링크**

  **문서 내의 다른 문서나 웹 페이지로 이동할 수 있는 링크**

> <a> 태그를 이용하여 표현함
> 

> 파일, 이미지, 이메일 주소 같은 다른 리소스들을 연결함
> 

---

**하이퍼링크로 표현 가능한 속성**

### **href**

**URL 주소 (파일의 경로 값) 지정함**

<aside>
🔗 **<a href = “url” > link text </a>**

                                     ****

**url** → 하이퍼링크로 연결할 파일 경로 지정

**link text** → 링크를 클릭할 때 보이는 텍스트를 지정

</aside>

```html
<a href ="http://www.naver.com"> NAVER </a>

<a href = "http://www.google.com">
 <img src = "google">
</a>
```

---

- **파일경로**
    
    해당 html 파일이 위치한 **디렉토리와 파일명으로 구성**
    
    <aside>
    🔗 **/ 디렉토리 / 파일명.html**
    
    </aside>
    
    **절대경로** 
    
    **: 전체 경로를 명시하여 경로를 지정하는 방식**
    
    http:// 웹 프로토콜로 시작함
    
    디렉터리와 관계없이 특정 파일의 절대적 위치를 가리킴
    
    **상대경로** 
    
    **: 현재 파일이 위치한 디렉토리를 기준으로 파일 경로 지정**
    
    경로를 작성하는 파일 기준으로 연결하는 파일의 위치를 작성하는 것
    
    <aside>
    🔗 [http://www.mysite.com/index.html](http://www.mysite.com/index.html)   → 절대경로
    
    ./index.html  ../dist/index.js   → 상대경로
    
    </aside>
    
    ---
    
- **href 어트리뷰트  _ 하이퍼링크를 생성하는데 사용되는 속성**
    
    **절대 URL**  
    
    **: 프로토콜, 도메인 이름을 포함한 전체 경로 표시**
    
    접근하는 최초 시작점으로부터 경유한 경로를 모두 기록하여 자원 위치 나타냄
    
    웹 사이트 URL
    
    **상대 URL**  
    
    **: 현재 문서 위치를 기준으로 상대적인 경로 표시** 
    
    프로토콜, 도메인 이름을 생략함
    
    ```html
    <a href="http://www.example.com">Example</a> 
    <a href="subdirectory/example.html">Example</a>
    ```
    
    **fragment identifier (=anchor / bookmark)** 
    
    : **문서 내의 특정요소를 나타냄**
    
    ```html
    <a href = "#title"> 
     <p> 제목으로 </p>
    </a>
    
    '''
    <h2> <a name = "title"> </a> 제목 <h2>
    ```
    
    href 속성 값 앞에 **#**을 붙이면 해당 id를 가진 요소로 이동함
    
    **메일주소 및 특수 프로토콜**                                                                                                                                                                                                      
    
    ```html
    <a href = "mailto : dylim7715@gmail.com"> 이메일 </a>  
    <a href = "tel : 123-456-7890"> 전화번호 </a>
    ```
    

---

### target

**: 링크로 연결된 문서가 열릴 곳을 지정함**

```html
<a href="[http://www.google.com](http://www.google.com/)" target="_blank">
Visit [google](http://google.com/) </a>
```

| target 속성값 | 설명 |
| --- | --- |
| _blank | 새로운 웹 브라우저 창에 오픈 |
| _self | 현재 프레임에서 오픈 (기본설정) |
| _parent | 부모 프레임에서 오픈 |
| _top | 현재 창의 가장 상위 프레임에서 오픈 |
| 프레임명  | 링크로 연결된 문서를 지정된 프레임에서 오픈 |

---

- **rel**  :  **링크된 리소스와 현재 문서 간의 관계를 정의함**
    
    
- **download**  :  **지정된 파일을 직접 다운로드**
    
    ```html
    <a href = "cat.jpg" download>
      <img src = "cat.jpg"> 
    </a>
    ```