# async와 await

프로미스 객체를 더 쉽고 편리하게 사용할 수 있게함.

어떠한 함수에 `async` 키워드를 작성하면 그 함수는 자동으로 프로미스 객체를 반환함.

`await` 은 `async` 로 작성된 함수 안에서 사용함. `await` 키워드로 작성된 코드가 실행되면 작업이 다 끝날 때까지 프로그램을 잠시 중단하고, 해당 작업이 끝나면 다음 코드를 순차적으로 실행함.

`try` , `catch` 와 함께 쓰임. 먼저 `try` 문의 코드가 실행되고, 만약 오류가 발생하면 `catch` 문이 실행되어 오류가 출력된다.

```javascript
// start, middle, end를 각각 2초 후에 출력하는 코드
const delaylog = (msg, time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(msg);
      resolve();
    }, time);
  });
};

// async를 사용해서 result함수가 프로미스 객체를 반환하게 함
const result = async () => {
  // try문이 먼저 실행됨, 오류 발생시 catch문 실행
  try {
    await delaylog('start', 2000);
    await delaylog('middle', 2000);
    await delaylog('end', 2000);
  } catch (error) {
    console.log(error);
  }
};
result();
```

## promise.all([ ])

배열 안에 있는 모든 프로미스들을 동시에 실행시키고, `await` 이나 `then` 에 의해 모든 프로미스들의 작업이 끝날 때까지 기다렸다가 결과를 한번에 배열 형태로 받음

만약 하나라도 실패하면 `catch` 로 넘어가서 오류 출력

```javascript
// 모든 비동기 작업을 한번에 실행시켜서 한번에 출력하는 코드
function job(name, delay) {
  return new Promise((resolve) => {
    setTimeout(() => resolve(`${name} 완료`), delay);
  });
}

const result = async () => {
  try {
    const res = await Promise.all([job('a', 2000), job('b', 2000)]);
    console.log(res);
  } catch (error) {
    console.log(error);
  }
};
result();
// 2초 후에 [ 'a 완료', 'b 완료' ] 출력
```
