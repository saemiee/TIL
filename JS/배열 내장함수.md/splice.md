## splice

splice는 배열에서 특정 항목을 제거할 때 사용한다.

```
const numbers = [1, 2, 3, 4];
const index = numbers.indexOf(3);
numbers.splice(index, 1);
// [1, 2, 4]
```

첫번째 파라미터는 어떤 인덱스부터 지울지, 두번째 파라미터는 그 인덱스부터 몇개를 지울지를 의미한다.
