# <Fragments> 태그

컴포넌트 단위로 element를 return 할때 

하나의 <html> 태그로 전체를 감싸지 않으면 오류가 남

`<Fragment>` 태그로 감싸면 <html>태그나 의미없는 태그를 추가하지 않아도 됨🤩

DOM에 별도의 노드를 추가하지 않고 사용할 수 있음

```jsx
import React from "react";

const Test = () => {
	return (
		<Fragment>
			<p>테스트입니다!</p>
		</Fragment>
	)
}
export default Test
```

`<Fragment>` 태그는 `<> </>` 이런식으로 축약해서 사용할수 있음