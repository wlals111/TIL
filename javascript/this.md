# this

자신이 속한 객체를 가리키는 키워드

함수를 어떻게 호출했는지에 따라 this가 바인딩하는 값(가리키는 값)이 달라짐

```javascript
// 전역공간에서 this를 호출하면 전역객체인 window객체가 출력됨
console.log(this);
```

## 일반함수 호출에서 this

```javascript
function func() {
  console.log(this);
}

// this가 있는 함수를 전역객체가 호출했기 때문에 this에는 window객체가 바인딩됨
func();
```

## 메서드 호출에서 this

```javascript
const cafe = {
  brand: '투썸',
  menu: '아메리카노',

  newCafe:{
  brand: '메가',
  menu: '아이스티',
  }
  print: function () {
    console.log(this);
  },
};

// print 메서드를 newCafe객체가 호출했기 때문에 this는 newCafe객체 그 자체를 가리킴
cafe.newCafe.print(); // {brand: '메가', menu: '아이스티', print: ƒ}
```

## 생성자 함수 호출에서 this

생성자 함수는 새로운 객체를 생성함. `new` 키워드로 호출

```javascript
function cafe(menu) {
  console.log(this); // cafe {}
  this.menu = menu;
}

// new cafe함수가 실행되면서 새로운 객체 { }가 생성되고, this에는 새로운 객체가 바인딩됨
// 새로운 객체의 menu프로퍼티에 '아메리카노'를 할당하여 {menu: '아메리카노'} 가 만들어지고, 이 객체를 리턴함
let myCafe = new cafe('아메리카노');
console.log(mycafe); // cafe {menu: '아메리카노'}
```

## 콜백 함수 호출에서 this

```javascript
const cafe = {
  brand: '투썸',
  menu: '',
  setMenu: function (menu) {
    this.menu = menu;
  },
};

// 콜백함수 호출은 일반함수 호출과 같음 -> 전역객체가 함수롤 호출한 것과 같음 -> this는 전역객체를 바인딩함
function getMenu(menu, callback) {
  callback(menu);
}

getMenu('아메리카노', cafe.setMenu);
console.log(cafe); // {brand: '투썸', menu: '', setMenu: ƒ}
```
