자바스크립트에서는 불리언형이 아니지만 True로 판단되는 값과 False로 판단되는 값들이 있다.
이를 Truthy & Falsy 라고 한다.

- Truthy : True 같은 값
- Falsy : False 같은 값

# Falsy

false로 판단되는 값들 :

- `undefined`
- `null`
- `0`
- `` (공백)
- `NaN`

논리부정연산자"!"는 불리언 값을 역전시켜 반환하니 이를 활용해서 살펴보자.

```js
console.log(!undefined); // true
console.log(!null); // true
console.log(!NaN); // true
console.log(!""); // true
console.log(!0); // true
```

모두 `true`가 나오는 것을 보면 원래 `false`로 판단되는 값들이다.

# Truthy

true로 판단되는 값들 :

- 0을 제외한 숫자형
- 문자열

등등 Falsy 한 다섯가지 값들을 제외한 모든 값들이 Truthy한 값이다.

```js
console.log(!3); // false
console.log(![]); // false
console.log(!"HELLO"); // false
console.log(!{}); // false
```

모두 `false`가 나오는 것을 보면 원래 `true`로 판단되는 값들이다.

# Truthy와 Falsy 활용하기

Truthy와 Falsy를 활용할 수 있다.

아래와 같이 person을 전달받고 person의 이름을 반환하는 함수 getName이 있다고 가정하자.
person이 undefined 상태기 때문에 에러가 발생한다.

```js
function getName(person) {
  return person.name;
}
let person;
const name = getName(person);
console.log(name); // TypeError: Cannot read properties of undefined (reading 'name')
```

그래서 if 문을 추가해 person이 undefined일 경우 정의되지 않았다고 출력하면 person이 undefined일 때는 에러가 출력되지 않지만 null이 들어간다고 하면 다시 에러가 발생하기 때문에 조건문을 추가해줘야한다.

```js
function getName(person) {
  if (person === undefined) {
    return "정의되지 않았어요!";
  }
  return person.name;
}
let person = null;
const name = getName(person);
console.log(name); // TypeError: Cannot read properties of null (reading 'name')
```

이 때 falsy를 활용해 간단하게 작성할 수 있다.
`!person` 을 해주면`!person`이 `true`일 때,
즉 `person`은 `false`일 때 if문 안의 구문을 실행한다.

`person`이 `flase`가 될 때는 `undefined` 거나 `null` 이거나 공백이거나 등등 falsy 한 값들이 올 때이다.

```js
function getName(person) {
  if (!person) {
    return "정의되지 않았어요!";
  }
  return person.name;
}
let person = null;
const name = getName(person);
console.log(name); // 정의되지 않았어요!
```
