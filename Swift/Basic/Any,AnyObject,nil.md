## Any, AnyObject, nil

Swift에는 타입이 정해지지 않은 것들을 다루는 특별한 타입이 존재한다.

### Any

- 모든 타입을 지칭하는 키워드
- Any는 모든 타입을 수용할 수 있다.
- 타입은 Any로 지정되기 때문에 다른 타입의 값에 Any 타입의 값을 대입하는 것은 불가능하다.

```swift
var someAny: Any = 100
someAny = "Swift 공부하기"
someAny = 12.343

// 컴파일 오류 발생
// var someDoule: Double = someAny
```

### AnyObject

- 모든 타입을 지칭하는 프로토콜
- 클래스의 인스턴스만 수용하기 때문에 클래스의 인스턴스가 아니면 할당이 불가능하다.

```swift
class SomeClass {}
var someAnyObject: AnyObject = SomeClass()

//someAnyObject = 123.12 // 컴파일 오류 발생
```

### nil

- 없음을 의미하는 키워드
- 다른 언어의 NULL,null 등과 유사한 표현
- Any, AnyObject의 타입에도 nil 값을 할당할 수 없다.

```swift
someAny = 0
//someAny = nil // 컴파일 오류 발생
//someAnyObject = nil // 컴파일 오류 발생
```
