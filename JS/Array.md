## 배열

배열은 여러 개의 항목들이 담겨있는 리스트와 같다.

```
const array = [0, 1, 2, 3]
```

### 배열에 새 항목 추가하기

배열이 지니고 있는 내장함수 `push`를 사용한다.

```
const objects = [{name: 고양이}, {name: 토끼}]

objects.push({name: 강아지})
```

### 배열의 크기 알아내기

배열의 크기를 알아낼 때는 내장함수 `length`를 사용한다.

```
const objects = [{name: "고양이"}, {name: "강아지"}];

console.log(objects.length); // 2
```
