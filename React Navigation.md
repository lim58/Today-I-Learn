# React Navigation

**React Native에서 다른 페이지를 이동할 수 있게 해주는 라이브러리**

네비게이션 종류 `stack(스택)` `tab(탭)` `drawer(드로어)`

### Navigation 구조

| 👾 NavigationContainer 
: 최상위 컴포넌트 | 🪆Navigator 
: 화면 관리자 | 📺 Screen 
: 화면 |
| --- | --- | --- |
| - 네비게이션 계층 구조와 상태를 관리하는 컨테이너  | - 여러 개의 Screen 컴포넌트를 
자식 컴포넌트로 가짐 | - name, component 속성을 지정
- 항상 navigation, route가 props로 전달됨 |

---

## stack navigation

스택 네비게이션에 필요한 라이브러리 설치

<aside>
📌 npm install @react-navigation/stack

</aside>

**현재 화면 위에 다른 화면을 쌓으면서 화면을 이동함**

화면 위에 새로운 화면을 쌓으면서 (push) 이동함

이전 화면을 계속 유지함

가장 위의 화면을 들어내면 (pop) 이전 화면으로 들어갈 수 있음 

![download.png](React%20Navigation%20301f8adcba484c6e9d2746d9d6898055/download.png)

**ex) 카카오톡** 

카카오톡 앱을 실행 → 채팅 창 리스트 나옴 → 메신저 창으로 들어가기

![68747470733a2f2f74312e6b616b616f63646e2e6e65742f6b616b616f636f72702f536572766963652f4b616b616f54616c6b2f70632f736c6964652f74616c6b70635f706376657273696f6e5f30312e6a7067.jpg](React%20Navigation%20301f8adcba484c6e9d2746d9d6898055/68747470733a2f2f74312e6b616b616f63646e2e6e65742f6b616b616f636f72702f536572766963652f4b616b616f54616c6b2f70632f736c6964652f74616c6b70635f706376657273696f6e5f30312e6a7067.jpg)

**1) 화면 구성**

`createStackNavigator` 함수로 스택 네비게이션 생성

```jsx
import React from 'react';
import { createStackNavigator } from '@react-navigation/stack';
import Home from '../screens/Home';
import List from '../screens/List';
import Item from '../screens/Item';

const Stack = createStackNavigator();

const StackNavigation = () => {
  return (
    <Stack.Navigator>
        <Stack.Screen name="Home" component={Home} />
        <Stack.Screen name="List" component={List} />
        <Stack.Screen name="Item" component={Item} />
    </Stack.Navigator>
);
};

export default StackNavigation;
```

Screen 컴포넌트와 Navigator 컴포넌트가 있음

Screen 컴포넌트의 name은 반드시 다른 값을 가져야 함

**2) 화면 이동** 

Screen 컴포넌트의 component로 지정된 컴포넌트는 화면으로 이용

- navigation이 props로 전달

```jsx
const Home = ({ navigation }) => (
  return (
      <Container>
          <StyledText>Home</StyledText>
          <Button
              title="go to the list screen"
              onPress={() => navigation.navigate('List')}
        />
      </Container>
	)} 
```

컴포넌트에서 navigation props를 받아 `navigation.navigate(스택이름)` 으로 이동함