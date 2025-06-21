# custom hook(커스텀 훅)

- 여러 컴포넌트에서 반복되는 로직을 재사용하기 위해 만든 것
- 커스텀 훅의 함수 이름은 `use` 로 시작해야 함
- src폴더 아래에 hooks라는 폴더를 만들어서 커스텀 훅 보관
- return하는 값이 2개 이하고 간단한 로직이면 배열로 return해도 됨 -> return 한 순서대로 구조분해 함
- return하는 값이 3개 이상이고 로직이 복잡하면 객체로 return 하는 게 좋음 -> `key` 값을 기준으로 구조분해 함

```jsx
// 커스텀 훅
import { useState } from 'react';

const useInput = () => {
  const [input, setInput] = useState('');

  const onChange = (e) => {
    setInput(e.target.value);
  };

  // state와 이벤트 핸들러를 배열로 리턴함
  return [input, onChange];
};

export default useInput;
```

```jsx
const HookEaxm = () => {
  // 이름을 바꿔 여러번 사용해도 상관없음, 순서만 지키면 됨
  const [input, onChangeInput] = useInput();
  const [birth, onChangeBirth] = useInnput();

  return (
    <div>
      <input type="text" value={input} onChange={onChangeInput} />
      <br />
      <input type="text" value={birth} onChange={onChangeBirth} />
    </div>
  );
};
```
