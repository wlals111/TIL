# 함수 컴퍼넌트

- 함수를 사용해 만든 컴퍼넌트
- html요소를 반환하게 함
- 컴퍼넌트 함수의 첫 글자는 대문자로 시작해야 함

```jsx
function Header() {
  return (
    <div>
      <h1>header</h1>
    </div>
  );
}
```

# jsx

자바스크립트와 html을 합친 문법

### jsx 주의 사항

1. 중괄호 내부에는 자바스크립트 표현식만 넣을 수 있음(삼항 연산자, 변수)

if문, for문 불가능

```jsx
const App = () => {
  const number = 10;
  return <div>{number % 2 === 0 ? '짝수' : '홀수'}</div>;
};
```

2. 숫자, 문자열, 배열만 렌더링됨.

true, false, null, undefined 는 렌더링 안됨

객체는 렌더링 안됨. 점 표기법으로 객체의 값은 렌더링 가능

```jsx
const App = () => {
  const user = {
    name: '홍길동',
    isLogin: true,
  };

  return (
    <div>
      {user.name}
      {10}
      {true}
      {null}
      {undefined}
    </div>
  );
};
```

3. 모든 태그는 `/` 로 닫혀 있어야 함
4. 리턴문의 최상위 태그는 하나만 있어야 함
