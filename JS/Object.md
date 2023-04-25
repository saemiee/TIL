## 객체

객체는 변수나 상수를 사용하게 될 때 하나의 이름에 여러 종류의 값을 넣을 수 있게 해준다.

```
const cat = {
  name: "소금이",
  age: 2
};

console.log(cat.name); // 소금이
console.log(cat.age); // 2
```

객체를 선언 할 때 `{ }`문자 안에 원하는 값을 넣어준다.
만약 키 부분에 공백이 있어야 하는 상황이라면 따옴표로 감싸서 문자열로 넣어준다.

### 함수에서 객체를 파라미터로 받기

```
const cat = {
  name: "소금이",
  age: 2,
  color: "하얀색"
}

function print(animal) {
  const text = `${cat.name}은 제가 키우는 ${cat.age}살 ${cat.color} 고양이입니다. `;
  console.log(text);
}

print(cat);
```

### 객체 비구조화 할당

객체 비구조화 할당은 객체 구조 분해라고도 하며 사용하면 코드를 짧고 보기 좋게 작성 할 수 있다.

```
const cat = {
  name: "소금이",
  age: 2,
  color: "하얀색"
}

function print(animal) {
  const { name, age, color } = animal;
  const text = `${name}은 제가 키우는 ${age}살 ${color} 고양이입니다. `;
  console.log(text);
}

print(cat);
```

객체에서 값들을 추출해 새로운 상수로 선언해 준다.
더 나아가 파라미터 단계에서 객체 비구조화 할당을 할 수 있다.

```
function print({ name, age, color }) {
  const text = `${name}은 제가 키우는 ${age}살 ${color} 고양이입니다. `;
  console.log(text);
}
```

### 객체 안에 함수 넣기

```
const cat = {
  name: "소금이",
  sound: "야옹",
  say: function say() {
    console.log(this.sound);
  }
}

cat.say; // 야옹
```

- 함수가 객체 안에 들어가면 `this`는 자신이 속해있는 객체를 가르킨다.
- 함수는 이름이 없어도 된다.
- 객체 안의 화살표 함수를 넣으면 제대로 작동하지 않는다.
- function으로 작성한 함수는 this가 제대로 자기 자신이 속한 객체를 가르키다.
- 그러나, 화살표 함수는 객체 안에 들어갔을 때 this가 제대로 자기 자신이 속한 객체를 가르키지 않는다.
