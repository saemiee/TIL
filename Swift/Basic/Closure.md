## 클로저

> 클로저란 중괄호로 감싸진 실행 가능한 코드 블럭이다. 클로저를 사용하면 코드를 보다 간결하게 만들 수 있다.

- 참조 타입이다.
- 함수는 클로저의 한 형태로 이름이 있는 클로저이다.
- 일급 객체의 역할을 할 수 있다.
- 일급 객체는 전달인자로 보낼 수 있고, 변수/상수 등으로 전달할 수 있으면 함수의 반환 값이 될 수 있다.

### 클로저 표현식

```swift
{ (인자들) -> 반환타입 in
  로직구현
}
```

클로저는 in으로 구분지어 closure head와 closure body로 나뉜다.

- Parameter와 Return Type이 둘 다 없는 클로저
  클로저는 익명 함수로 생각할 수 있다. 따라서 Swift 1급 객체이기 때문에 다음과 같이 상수에 클로저를 대입하는 것이 가능하다.
  특히 인자와 반환 타입이 없는 경우 다음가 같이 사용이 가능하다.

```swift
let closure = { () -> () in
  print("클로저 공부중")
}
```

클로저에서는 반환 타입이 있어도 생략 가능하고 없어도 생략이 가능하다. 함수에서는 불가능한 인자도 생략이 가능 !

- Parameter와 Return Type이 있는 클로저

```swift
let closure = { (name: String) -> String in
  retrun "Hello \(name)"
}
```

함수와 똑같이 Parameter의 "name"은 단독으로 쓰였으니, Argument Label이자, Parameter Name이라고 생각 할 수 있지만 클로저에서는 Argument Label을 사용하지 않는다. 따라서 name은 Argument Label은 아니고 오직 Parameter Name이다.

```swift
closure("Sodeul")
closure(name: "Sodeul")  //error!
```

### 1급 객체로서 클로저

- 클로저를 상수나 변수에 대입 할 수 있다.
- 함수의 파라미터 타입으로 클로저를 전달 할 수 있다.
- 함수의 반환 타입으로 클로저를 사용할 수 있다.

### 클로저 실행하기

- 클로적 대입된 상수나 변수로 실행하기

```swift
let closure = { () -> String in
  return "Hello saemi"
}

closure()
```

- 클로저를 직접 실행하기
  클로저를 변수나 상수에 대입하지 않고 실행시키고 싶다면(완벽한 일회성) 클로저를 소괄호로 감싸고 마지막에 호출문 구문 () 를 추가해준다.

```swift
({ () -> in
  print("Hello saemi"
)})()
```
