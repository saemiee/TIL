## 변수와 상수

> 변수는 값을 수정할 수 있고 상수는 값을 수정할 수 없다. Swift에서는 언제 어디서 값이 바뀔지 모르는 변수보다 상수를 권장한다.

- var : 변수
- let : 상수

```swift
var number = 1
let name = "saemi"
```

Swift는 정적 타이핑 언어이다. 정적 타이핑 언어란 변수나 상수를 정의 할 때 그 자료형(타입)이 어떤 것인지를 정확히 명시해야 하는 언어이다.

## 타입 어노테이션 Type Annotaion

```swift
var number: Int = 18
let name: String = 'saemi'
var height: Float = 160.0
```

이렇게 변수 또는 상수 이름 뒤에 콜론을 붙이고 자료형을 써준다.
`: String`과 `: Int` 등을 가지고 **타입 어노테이션(TypeAnnotaion)** 이라고 한다.

Swift는 타입을 엄격하게 다루기 때문에 다른 자료형끼리는 기본적인 연산조차 불가능하다. 다른 자료형끼리 연산은 다음과 같이 사용해야 한다.
`Float(number) + height`
`String(number) + "살" + name + "!"`
`"\(number)살 \(name)!"`

## 타입 추론 Type Interence

첫번째 예제를 살펴보면 자료형을 명시하지 않았다.
Swift 컴퍼일러는 큰따옴표로 감싸진 텍스트는 String 타입인 것을 알고, 숫자는 Int 타입인걸 인식 할 수 있다.

타입을 직접 명시하지 않고도 값을 가지고 정적 타이핑을 할 수 있게 해주는 것을 **타입 추론(Type Interence)**이라고 한다.
