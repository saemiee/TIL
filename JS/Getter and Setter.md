## Getter와 Setter 함수

객체의 프로퍼티는 두 종류로 나뉜다.

- 데이터 프로퍼티
- 접근자 프로퍼티(getter, setter)

### Getter

getter 메서드는 프로퍼티를 읽을 때 실행한다.

```
const numbers = {
  a: 1,
  b: 2,
  get sum () {
    console.log('sum 함수 실행');
    return this.a + this.b;
  }
};

console.log(numbers.sum); // 3
```

getter 메서드는 특정 값을 조회 할 때 설정한 함수로 연산된 값을 반환한다.

### Setter

setter 메서드는 프로퍼티로 값을 할당 할 때 실행된다.

```
const user = {
  name: 'saemi',
  surname: 'kim'

  get fullName() {
    return `${this.surname} ${this.name};
  }

  set fullName(value) {
    [this.surname, this.name] = value.split("");
  }
};

user.fullName = "고 양이"

alert(user.fullName) // 고 양이
```

setter 메서드는 앞부분에 set을 붙인다.
setter를 설정하고 나면 값을 설정했을 때 파라미터로 받아온다.
