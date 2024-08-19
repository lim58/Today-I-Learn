# export default & export name

### **export default**

한 모듈당 export default는 하나만 존재

export default 내보내면 export 한 이름과 상관없이 원하는 이름으로 import 가능

```jsx
const Test = () => {
	return (
		<div>테스트</div>
	)
}
export default Test

// 다른 파일
import Test from "./Test"
```

### **export name**

하나 or 여러개 내보낼 때 모두 사용

named export인 경우 export 한 이름으로만 import 가능

그리고 반드시 중괄호로 가져와야함

```jsx
export function Test() {
	console.log("테스트")
}

// 다른 파일
import { Text } from "./Test"
```