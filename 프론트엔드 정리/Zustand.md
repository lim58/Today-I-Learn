# Zustand

태그:  공부필요

### 🔀 **상태 관리 라이브러리**

**상태 변경 시 불필요한 리렌더링을 방지하며 provider hell 문제를 해결할 수 있음**

Flux 구조를 사용하는 확장 가능한 상태 관리 라이브러리

***Flux 구조**

- 어느 방향으로 데이터가 전달될지 모르는 복잡성을 해소하기위해
- Flux 패턴을 통해 데이터가 단방향으로 변경될 수 있도록 만든 구조

![img1.daumcdn.png](Zustand%209916563a4b30408a9b65bbcff2e63df0/img1.daumcdn.png)

![img1.daumcdn.png](Zustand%209916563a4b30408a9b65bbcff2e63df0/img1.daumcdn%201.png)

### 🤷‍♀️ Zustand 특징

![download.jpg](Zustand%209916563a4b30408a9b65bbcff2e63df0/download.jpg)

- provider 사용하지 않음
- store 사용을 위한 작성되는 코드 길이가 비교적 짧음
- 자주 바뀌는 상태를 직접 제어 가능 (Transient Update)
- immer, devtools 지원

***immer** 내부적으로 불변성을 처리함

***DevTools** 브라우저의 개발자 도구와 연동하여 간편한 디버깅을 지원

### 🛠️ 동작 원리

**1) `create` 함수로 스토어를 생성**

- 초기 상태와 업데이트하는 함수를 받아 상태를 관리함
- 상태가 변경될 때마다 구독자 (subscriber)에게 알리고 컴포넌트를 리렌더링 함

```jsx
const useProductStore = create(set => ({
  productsData: [],
  setProductsData: data => set({ productsData: data }),
  // ... (다른 상태 및 업데이트 함수들)
}));
```

![images.jpg](Zustand%209916563a4b30408a9b65bbcff2e63df0/images.jpg)

**2) `subscribe` 매서드를 통해 상태 변화 감지**

```jsx
const store = useProductStore();

//상태 변화를 감지하는 콜백 함수 등록
const unsubscribe = store.subscribe(state => {
  console.log("상태가 변경됨: ", state);
});

store.setProductsData(newData); //상태 변경
unsubscribe(); //구독 해제
```

**3) 상태 업데이트 및 읽기**

- `set`  상태를 변경 (상태 업데이트)
- `get` 현재 스토어 상태를 읽음 (상태 조회 및 조건부 업데이트 수행)

```jsx
const useStore = create((set, get) => ({
  count: 0,
  doubleCount: () => get().count * 2,
}));
```