# [4/4] margin border padding

생성일: 2023년 4월 4일 오후 8:04

### Margin Border Padding

---

![a.jpg](%5B4%204%5D%20margin%20border%20padding%200c87979bd624444085ef085ad826f6f0/a.jpg)

**Margin  padding  : 여백을 지정하는 단축속성**

🔗 px  em  vw  : 단위로 지정

🔗 %  : 부모 요소의 가로 너비에 대한 비율로 지정

---

---

**Margin**

: border 바깥 여백 영역 설정

<aside>
🔗 margin-top  /  margin-right   /  margin-bottom   /  margin-left

</aside>

```css
table{
margin-top : 5px;
margin-right : 5px;
margin-bottom : 5px;
margin-left : 5px;
}
//margin : 5px; (4면을 다같이 지정할 수 있음)
//margin : 5px 7px 3px 0px; (위, 오른쪽, 아래, 왼쪽 순)

table{
margin : auto 0;  (위아래 값 자동지정, 좌우 0px) //가운데로 정렬할 수 있음
}
```

+) 배경색의 영향을 받지 않음, 음수 값이 허용됨

**Padding**

: content, border 사이의 여백 설정 (요소의 네 방향 안쪽 영역)

<aside>
🔗 padding-top  /  padding-right   /  padding-bottom   /  padding-left

</aside>

```css
<style>
   div{
    padding-top : 5px;
    padding-right : 10px;
    padding-bottom : 7px;
    padding-left : 5px;
}
</style>

p {padding : 5px;}  
p {padding : 2px 5px 3px 5px;}

```

+) 웹의 크기 변화를 인식함 

**border**

: 요소의 테두리를 설정

<aside>
🔗 border-width  /  border-style  /  border-color

</aside>