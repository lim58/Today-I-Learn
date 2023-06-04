# [4/4] vh vw %

생성일: 2023년 4월 6일 오후 7:02

**vh  /  vw** (viewport height / viewport width)

> 현재 **실행중인 스크린 크기에 맞춰 상대적 크기** 반환
> 

> 1vh=1%                                                                                                                                                                                            1vw=1%
> 

_ 100분의 1단위

ex) 높이값이 900px일때 1vh = 9px, 너비값이 750px일때 1vw=7.5x 

**%** : **부모 요소를 기준으로 상대적 크기** 변환

```css
div { width : 200px; }
div p { width : 50%; }  //p요소는 200px 절반인 100px를 가짐
```