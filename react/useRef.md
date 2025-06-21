# useRef

- reference 객체 생성
- 어떠한 경우에도 리렌더링 되지 않음 -> 렌더링에 영향을 미치고 싶지 않은 변수를 만들 때 사용
- dom요소에 접근 가능 -> dom 요소 조작 가능

### useState와의 차이점

useState는 `state` 가 변경되면 컴포넌트 리렌더링됨

하지만 useRef로 만든 변수는 리렌더링을 유발하지 않음

```jsx
// useRef 기본 구조
const refObj = useRef(초기값);
console.log(refObj); // {current: 초기값}
```

```jsx
// useRef로 input 수정횟수 출력
import { useState, useRef } from 'react';

const Exam = () => {
  const [input, setInput] = useState('');

  const countRef = useRef(0);

  const onChange = (e) => {
    setInput(e.target.value);

    countRef.current++;
    console.log(countRef.current);
  };

  return (
    <div>
      <input value={input} onChange={onChange} type="text" />
    </div>
  );
};

export default Exam;
```
