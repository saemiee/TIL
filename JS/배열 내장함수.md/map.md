## map

배열 안의 각 원소를 변환 할 때 사용되며, 이 과정에서 새로운 배열을 만들어내는 함수이다.

```
// map 함수를 사용해 모든 원소에 제곱한 새로운 배열 만들기
cosnt array = [1, 2, 3, 4, 5, 6, 7, 8];

const square = n => n * n;
const squared = array.map(square);
console.log(squared);
```

- map 함수의 파리미터는 변화를 주는 변화함수를 전달한다.
- 변수 함수를 꼭 이름을 붙여서 선언 할 필요 없이 다음 코드와 작성해도 된다.

```
const squared = array.map(n => n * n);
console.log(squared);
```
