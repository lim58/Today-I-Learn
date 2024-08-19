# Router 사용

```jsx
import React from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import About from "./pages/About";
import Home from "./pages/Home";

export default function Router() {
    return (
        <BrowserRouter>
            <Routes>
				      <Route path="/" element={<Home />} />
				      <Route path="/about" element={<About />} />
            </Routes>
        </BrowserRouter>
    )
}
```

Route 컴포넌트로 특정 경로에 원하는 컴포넌트 보여줌

BroswerRouter

- history API를 통해 history 객체를 생성함
- history API는 stack 구조이기에 사용자가 방문한 url 기록을 쌓는 형태로 저장됨

Routes

- location 변경시 하위에 있는 모든 Route를 조회하여 현재 location이랑 맞는 Route를 찾아줌

Route

- 브라우저 location 상태에 따라 다른 element를 렌더링함
    - 렌더링할 element는 <Element /> 형식으로 전달됨
    - path 값이 url과 일치하는지 확인하여 해당 url에 매칭된 element를 렌더링함