# API란?

클라이언트(웹브라우저)와 서버 간의 요청과 응답이 잘 이루어질 수 있도록 도와주는 체계

## 클라이언트와 서버의 통신과정

클라이언트(웹브라우저)가 서버에 원하는 데이터를 요청하면, 서버는 데이터베이스에서 요청받은 데이터를 찾아서 클라이언트에게 전달해줌

클라이언트는 API를 이용해서 서버에 원하는 데이터를 요청하고 전달받음

## fetch()

- fetch() 메서드를 통해 api호출
- 비동기 함수

## JSON

- 자바스크립트 객체 표기법
- 사람이 읽기 쉽고, 컴퓨터가 해석하기 쉬운 텍스트 형식의 데이터 구조
- `key`와 `value` 쌍으로 이루어짐
- [{...}, {...}, {...}] 구조
- 서버와 클라이언트 간에 데이터를 주고 받을 때 사용
- API 응답은 보통 JSON형식의 문자열로 옴

```javascript
const getData = async () => {
  try {
    // fetch는 비동기 함수이기 때문에 await으로 api호출이 다 끝날 때까지 기다림
    let response = await fetch('https://jsonplaceholder.typicode.com/users');

    // response는 api호출에 성공했을 때 반환되는 response 객체
    // 이 response 객체 안에는 json형식의 데이터가 포함되어 있음
    console.log(response);

    // .json()메서드를 사용해서 response객체에 담긴 json형식의 데이터를 자바스크립트 객체로 변환
    // 이 작업도 비동기이기 때문에 await을 사용해서 데이터 변환이 다 끝날 때까지 기다림
    const data = await response.json();

    console.log(data);
  } catch (error) {
    console.log(error);
  }
};
```
