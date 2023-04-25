## 객체를 위한 반복문 for...in

### 객체의 정보를 배열로 받아올 수 있는 함수

```
const cat = {
  name: "cat",
  sound: "야옹",
  age: 2
}

console.log(Object.entries(cat));
console.log(Object.keys(cat));
console.log(Object.values(cat));
```

- `Object.entries` : `[키, 값], [키, 값]]` 형태로 변환
- `Object.keys` : `[키, 키, 키]` 형태로 변환
- `Object.values` : `[값, 값, 값]` 형태로 변환

객체가 지니고 있는 값에 대하여 반복하고 싶다면 위 함수를 사용하거나 `for...in` 구문을 사용한다.

```
const cat = {
  name: '고양이',
  sound: '야옹',
  age: 2
}

for(let key in cat) {
  console.log(`${key} : ${cat[key]}`);
}
```

### break와 continue

반복문 안에서 break와 continue를 통하여 반복을 벗어나거나 그 다음 루프를 돌게끔 할 수 있다.

```
for(let i = 0; i < 10; i++) {
  if(i === 2) continue; // 다음 루프 실행
  console.log(i);
  if(i === 5) break; // 반복문 끝내기
}
```
