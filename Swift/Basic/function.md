## Swift 함수의 기본

> 함수는 `func` 키워드를 사용해서 정의한다. `->` 를 사용해 함수의 반환 타입을 지정한다.

### 함수 기본

- 함수 선언

```swift
func sum(a: Int, b: Int) -> Int {
  return a + b
}

func printName(name: String) -> Void { // 반환 값이 없는 함수
  print(name)
}
```

- 함수 호출

```swift
sum(a: 4, b: 3)
printName(name: "saemi")
```

### 매개변수 기본값

기본값을 갖는 매개변수는 매개변수 목록 중 가장 뒤쪽에 위치하는 것이 좋다.
매개변수 기본값을 가진 매개변수는 생략이 가능하다.

```swift
func greeting(friend: String, me: String = "saemi") {
  print("Hello \(friend)! I'm \(me)")
}
```

### 전달인자 레이블

전달인자 레이블은 함수를 호출할 때 매개변수의 역할을 좀 더 정확히 하거나 함수 사용자의 입장에서 표현하고자 할 때 사용한다.

```swift
func greeting(to friend: String, from me: String) {
  print("Hello \(friend)! I'm \(me)")
}

greeting(to: "potato", from: "saemi") // 함수를 호출할 때는 전달인자 레이블을 사용해야 한다.
```

### 가변 매개변수

전달 받을 값의 개수를 알기 어려울 때 사용한다. 가변 매개변수는 함수당 하나씩만 가질 수 있다.

```swift
func sayHello(me: String, friedns: String...) -> String {
  return "Hello \(friends)! I'm \(me)"
}

print(sayHello(me: "saemi", friends: "cat", "love", "potato"))
// Hello ["cat", "love", "potato"]! I'm saemi

print(sayHello(me: "saemi"))
// Hello []! I'm saemi
```

### 데이터 타입으로서의 함수

- 스위프트는 함수형 프로그래밍 패러다임을 포함하는 다중 패러다임 언어이다.
- 스위프트의 함수는 일급객체이므로 변수, 상수 등에 저장이 가능하다.
- 매개변수를 통해 전달이 가능하다.

### 함수의 타입표현

- 반환타입을 생략하는 것은 불가능하다.
- 타입이 다른 함수는 할당이 불가능하다.

```swift
var somefFunction: (String, String) -> Void = greeting(to:from:)
someFunction("cat", "saemi")
```
