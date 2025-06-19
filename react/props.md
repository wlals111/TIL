# props

- 부모 컴퍼넌트가 자식 컴퍼넌트에 전달하는 값
- 자식 컴퍼넌트에 객체 형태로 전달됨
- 자식 컴퍼넌트는 props를 구조분해 할당으로 받을 수 있음
- props로 컴퍼넌트나 html태그 전달 가능 -> 자식 컴퍼넌트는 `children` 이란 이름으로 받아옴

```jsx
// 부모 컴퍼넌트
function App () {
  const buttonProps = {
    text: '메일',
    color: 'red',
  }

  return (
    <Button {...buttonProps}/>
    <Button text={'카페'}>
    <div>자식 요소</div>
    </Button>
  )
}

// 자식 컴퍼넌트
// color = 'black'와 같이 color props에 기본값 설정 가능
const Button = (children, text, color = 'black')=>{
// 이벤트 핸들러 -> 버튼 클릭할 때마다 콘솔에 text 출력
const onClickButton = ()=>{
  console.log(text)
}

return (
  <button onClick={onClickButton}>
    {text} - {color.toUpperCase()}
    {children}
  </button>
)
}
```
