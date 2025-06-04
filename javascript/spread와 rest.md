# spread 연산자

- 배열이나 객체에서 반복되는 값들을 전달할 때 사용
- 함수를 호출할 때 인수로 긴 배열이나 객체를 받아올 때 사용

```javascript
// 배열 예제
const num1 = [1, 2, 3];
const num2 = [5, 6, 7];

// 중간에 다른 값을 넣거나 spread연산자 여러번 사용 가능
console.log(...num1, 4, ...num2, ...num1); // 1 2 3 4 5 6 7 1 2 3

// 객체 예제
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = { ...obj1, ...obj2 }; // { a: 1, b: 2 }
```

# rest 매개변수

- 함수의 매개변수로 값을 가져올 때 사용
- 배열이나 객체의 구조분해 할당에서 특정 값들을 배열이나 객체로 묶을 수 있음

```javascript
// 함수 예제
// rest를 사용해 매개변수로 num배열 받음
function add(...rest) {
  console.log(rest);
}
num = [1, 2, 3];
// spread연산자로 함수의 인수로 num배열 전달
add(...num); // [ 1, 2, 3 ]

// 객체 예제
const toy = {
  type: 'bear',
  price: 15000,
  color: 'blue',
};
let { type, ...rest } = toy;
console.log(type, rest); // bear { price: 15000, color: 'blue' }

// 배열 예제
const arr = [1, 2, 3, 4];
let [num1, num2, ...rest] = arr;
console.log(num1, num2, rest); // 1 2 [ 3, 4 ]
```
