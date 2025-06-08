# DOM

- 문서 객체 모델
- 웹브라우저가 HTML문서를 자바스크립트가 접근하고 조작할 수 있도록 객체 형태로 변환시킨 모델

# DOM트리

- HTML요소들을 트리 구조로 나타낸 것(부모-자식 구조)
- 각각의 HTML요소를 노드라고 함
- 자바스크립트는 DOM트리를 탐색해서 원하는 노드에 접근하고, 그것을 조작함

# DOM API

DOM(HTML 문서)을 자바스크립트로 조작할 수 있게 해주는 명령어 모음

```html
<div class="animal-info">
  <div id="name" class="info-item">강아지</div>
  <div id="color" class="info-item">갈색</div>
  <div id="age" class="info-item">2살</div>
</div>
```

위의 html문서를 dom api를 통해서 접근해보도록 하겠음

1. getElementById : 특정 id를 가진 요소 반환

```javascript
// id를 color로 갖는 div태그 자체를 반환
const $color = document.getElementById('color');

console.log($color);
```

1. querySelector : 특정 css선택자를 가지는 요소 반환

```javascript
// animal-info 클래스를 가지는 요소 반환
const $animalInfo = document.querySelector('div.animal-info');

// age 클래스를 가지는 요소 반환
const ageElement = document.querySelector('div.age');

console.log($animalInfo);
console.log(ageElement);
```

3. querySelectorAll : 특정 css선택자를 가지는 모든 요소 반환

```javascript
// info-item 클래스를 가지는 모든 요소 반환
const $infoItem = document.querySelectorAll('div.info-item');

console.log($infoItem);
```

4. getElementsByClassName : 특정 클래스 명을 가지는 모든 요소 반환

```javascript
// info-item 클래스를 가지는 모든 요소 반환
const $infoItem = document.getElementsByClassName('info-item');

console.log($infoItem);
```

5. getElementByTagName : 특정 태그 명을 가지는 모든 요소 반환

```javascript
// div태그를 가지는 모든 요소 반환
const $div = document.getElementByTagName('div');

console.log($div);
```

6. className : 클래스 명 변경

```javascript
const $name = document.getElementById('name');

// id가 name인 요소의 클래스 명을 dog-name으로 변경
$name.className = 'dog-name';
console.log($name);
```

7. id : 요소의 id값 추가, 수정

```javascript
const $animalInfo = document.querySelector('div.animal-info');

// class가 animal-info인 요소에 id를 추가함
$animalInfo.id = 'animal';
console.log($animalInfo);
```

8. classList.add : 요소에 클래스 추가
9. classList.remove : 요소에서 클래스 제거

```javascript
const $color = document.getElementById('color');

// id가 color인 요소에 이름이 dog-color인 클래스 추가
$color.classList.add('dog-color');
console.log($color);

// id가 color인 요소에 이름이 info-item인 클래스 삭제
$color.classList.remove('info-item');
ocnsole.log($color);
```

10. textContent : 요소의 텍스트 변경

```javascript
const $age = document.getElementById('age');

// id가 age인 요소의 텍스트를 변경
$age.textContent = '5살';
console.log($age);
```

11. style : 요소의 스타일 변경

```javascript
const $color = document.getElementById('color');

// id가 color인 요소의 스타일 변경
$color.style.color = 'pink';
console.log($color);
```

12. createElement : 새로운 요소 생성
13. createTextNode : 순수 텍스트만 생성함
14. parent.appendChild(child) : 부모에 자식요소 추가

```javascript
// div태그를 가지는 요소 생성
const $type = document.createElement('div');

$type.classList.add('info-item');
$type.id = 'type';

// '말티즈'라는 텍스트 생성
const $typeText = document.createTextNode('말티즈');

const $animalInfo = document.querySelector('div.animal-info');

// animal-info 클래스의 자식 요소로 새로운 div요소 추가
$animalInfo.appendChild($type);

// 새로운 div요소에 텍스트 추가
$type.appenChild($typeText);

console.log($type);
```
