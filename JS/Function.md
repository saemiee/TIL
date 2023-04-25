## 함수

- 함수를 만들 때는 `function` 키워드를 사용한다.
- 값을 받아주는 파라미터(매개변수)
- 함수 내부에서 `return` 키워드를 사용해 함수 결과물 지정
- `return`을 사용하면 함수가 끝난다.

```
function add(a, b) {
  return a + b;
}

const sum = add(3,4);
console.log(sum); // 7
```

### ES6

- ES6 는 ECMAScript6를 의미하며 자바스크립트의 버전을 가르킨다.
- 새로운 자바스크립트 버전이 나올때마다 새로운 문법이 소개된다.
- 브라우저 버전에 따라 지원되는 자바스크립트 버전이 다르다.
- 하지만, 보통 웹 개발을 할 때에는 Babel 이라는 도구를 사용하여 최신 버전의 자바스크립트가 구버전의 브라우저에서도 실행되도록 할 수 있다.

```
function hello(name) {
  console.log(`Hello ${name}!)
}

hello('saemi');
```

### 화살표 함수

함수를 선언하는 방식 중 또 다른 방법은 화살표 함수 문법을 사용하는 것이다.

- `function` 키워드 대신 `=>`문자를 사용하여 함수를 구현한다.
- 화살표의 좌측에는 파라미터를 배치한다.
- 화살표이 우측에는 코드블록을 배치한다.
- 화살표 함수가 가르키는 this와 function 에서 가르키는 this는 서로 다르다.

```
const add = (a, b) => {
  retrun a + b ;
};

console.log(add(1, 2));
```
