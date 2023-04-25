## shift와 pop

### shift

첫번째 원소를 배열에서 추출한다. 추출하는 과정에서 배열의 해당 원소는 사라진다.

```
const numbers = [10, 20, 30, 40];
const value = numbers.shift();
console.log(value);
console.log(numbers);
```

### pop

pop은 push와 반대로 배열의 맨 마지막 항목을 추출한다.

```
const numbers = [10, 20, 30, 40];
const value = numbers.pop();
console.log(value);
console.log(numbers);
```
