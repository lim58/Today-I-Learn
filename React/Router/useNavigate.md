# useNavigate

다른 페이지로 이동하는 hook

특정 이벤트가 발생하였을 때 페이지를 이동할 수 있음

```jsx
import { useNavigate } from "react-router-dom";

const navigate = useNavigate();

const onClick = () => {
	navigate('/')
}
```