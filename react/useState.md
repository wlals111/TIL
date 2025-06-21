# state

- 현재의 상태를 의미
- 변화할 수 있는 동적인 값(컴퍼넌트가 렌더링될 때마다 바뀔 수 있음)
- state가 변경되면 그 state를 가지고 있는 컴퍼넌트가 리렌더링됨 -> ui가 바뀔 수 있음
- 하나의 컴퍼넌트에 여러 개의 state가질 수 있음
- `useState` 훅 사용

### useState 구조

```jsx
const [state, setState] = useState(초기값);
```

`state` : 현재 상태
`setState` : `state`를 변경시키는 함수(상태 변화 함수)

`setState` 를 사용해야만 `state` 의 값을 변경시킬 수 있음

# 리액트 컴퍼넌트의 리렌더링이 발생하는 경우

1. 자신이 가지고 있는 `state` 가 변경됐을 때

그 `state` 를 가진 컴퍼넌트만 리렌더링됨. 부모나 형제 컴퍼넌트에는 영향 X

2. 부모로부터 받은 `props` 가 변경됐을 때

3. 부모 컴퍼넌트가 리렌더링되면 자식 컴퍼넌트도 리렌더링됨

```jsx
// 버튼을 누르면 0부터 1씩 늘어나는 앱

// 자식 컴퍼넌트
import { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button
        onClick={() => {
          setCount(count + 1);
        }}
      >
        +
      </button>
    </div>
  );
};

// 부모 컴퍼넌트
function App() {
  return;
  <>
    <Counter />
  </>;
}
```
