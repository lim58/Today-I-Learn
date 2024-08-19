# Recoil

리액트 상태 관리 라이브러리

Flux 패턴

![Untitled](Recoil%20fff1375c927880dca6f9de22949748d9/Untitled.png)

선언적 UI / 컴포넌트 중심 설계 / Hooks를 사용하는 방식이 기반

```jsx
import React from 'react';
import { atom, useRecoilState } from 'recoil';

const textState = atom({
  key: 'textState', // 고유한 키
  default: '', // 기본값
});

function TextInput() {
  const [text, setText] = useRecoilState(textState); // 사실상 useState와 동일

  const onChange = (event) => {
    setText(event.target.value);
  };

  return <input type="text" value={text} onChange={onChange} />;
```

- 기본적인 상태를 원자 atom 이라는 원자 단위로 취급
    
    
    atom 컴포넌트가 구독할 수 있는 React state
    
    default 값은 정적인 값, 함수가 될 수 있음
    

`useRecoilState`  atom에 저장된 상태를 읽고 쓰는데 사용

Selector는 Atom에서 파생 상태를 생성하기 위한 방법 제공

```jsx
import { selector } from 'recoil';

const charCountState = selector({
  key: 'charCountState',
  get: ({ get }) => {
    const text = get(textState);
    return text.length;
  },
});

function CharacterCount() {
  const count = useRecoilValue(charCountState);

  return <>Character Count: {count}</>;
}
```

charCountState는 textState의 변경에 의존하는 파생 상태 selector

순수 함수로 정의 되며 textState 값이 변경 될 때만 재 계산 됨

Atom의 상태가 변경되면 이 변경에 의존하는 모든 Selector에 전파됨

`useRecoilValue`  atom or selector 값을 읽는데 사용

Recoil 구독? 애플리케이션 상태 atom 이나 파생된 데이터 Selector의 변경을 감지하고 변경에 반응

구독 매커니즘은 React의 컴포넌트 렌더링 최적화와 상호작용함

```jsx
function TextInput() {
  // textState atom을 구독하고 상태 변경 시 재렌더링
  const [text, setText] = useRecoilState(textState);
}
```

상태가 변경될 때마다 UI가 최신상태를 반영하도록 보장함

`useSetRecoilState` Recoil 상태를 업데이트

`useResetRecoilState` atom 상태를 초기값으로 재설정하는데 사용

`useRecoilValueLoadable` 비동기 selector 상태를 관리하는데 사용 (데이터 로딩, 에러, 완료 상태 처리)

```jsx
import { selector, useRecoilValueLoadable } from 'recoil';

// 비동기 Selector 정의
const asyncDataState = selector({
  key: 'asyncDataState',
  get: async () => {
    const response = await fetch('https://api.example.com/data');
    return response.json();
  },
});

function AsyncDataComponent() {
  const loadable = useRecoilValueLoadable(asyncDataState);

  switch (loadable.state) {
    case 'hasValue':
      return <div>{loadable.contents}</div>;
    case 'loading':
      return <div>Loading...</div>;
    case 'hasError':
      return <div>Error: {loadable.contents.message}</div>;
  }
}
```