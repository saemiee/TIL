# Method

> 메서드란 클래스, 구조체, 열거형에 포함되어 있는 함수를 메서드라고 한다. 메서드는 다른 말로 클래스 함수라고도 할 수 있다.

---

## 인스턴스 메서드

인스턴스 메서드는 특정 Class, Struc 또는 Eunm 의 인스턴스에 속하는 함수이다. 인스턴스 메소드 안에서는 다른 인스턴스 프로퍼티와 인스턴스 메소드에 접근하고 호출할 수 있다.

- 인스턴스 메서드는 다른 모든 인스턴스 메서드 및 해당 타입의 특성에 암시적으로 접근한다.
- 인스턴스 메서드는 자신이 속한 타입의 특정 인스턴스에서만 호출될 수 있다.

```swift
class Counter {
  var count = 0

  func increment() {
    count += 1
  }

  func increment(by amount: Int) {
    count += amount
  }

  func reset() {
    count = 0
  }
}
```

Counter 라는 클래스를 정의했고, Count 클래스는 3가지 인스턴스 메서드를 정의하고 있다.

프로퍼티와 마찬가지로 . 을 통해 인스턴스 메서드를 호출할 수 있다.

```swift
let counter = Counter()

counter.increment() // count = 1
counter.increment(by: 5) // count = 6
counter.reset() // count = 0
```

### Self

self 라는 프로퍼티는 인스턴스 그 자체인 프로퍼티이다.
즉, 인스턴스 메소드 내에서 자기 자신이 인스턴스를 참조할 수 있는 프로퍼티이다.

```swift
class Person() {
  var saemi: String
  init(_ name: String) {
    saemi = name
    print(self.saemi)
  }
}

let a = Person("옥수수") // 옥수수
let b = Person("떡") // 떡
```

a, b 는 Person 타입의 인스턴스들이다.
인스턴스 생성 시 init이 호출되고 그 안에서 self.saemi가 호출된다.
바로 자기 자신의 saemi 프로퍼티를 호출하는 것을 볼 수 있다.

- self 프로퍼티는 보통의 경우 생략하여도 현재 인스턴스의 프로퍼티명과 메소드명을 자동으로 참조하게 된다.
- 인스턴스의 프로퍼티명과 매개변수명이 같은 경우 매개변수의 이름을 우선으로 인식한다.
- 프로퍼티명과 매개변수명이 같은 경우 self를 사용하여 명확하게 알려줘야 한다.

### 값 타입에서의 인스턴스 메서드

구조체, 열겨형은 값 타입이며 값 타입은 전달 받거나 할당을 할 때 복사가 된다.
그런 이유 때문이지 값 타입의 인스턴스 메서드에서는 인스턴스 프로퍼티를 수정하지 못한다.
인스턴스 메서드 내에서 인스턴스 프로퍼티를 접근 할 때 값 타입의 인스턴스 자체를 복사하여 접근한다.
-> 복사본의 프로퍼티를 수정해도 원본과 이미 같지 않기 때문에 수정할 수 없다.

```swift
struct SomeStruct {
  var someProperty: Int = 5
  func someMethod() {
    someProperty = 3 // Cannot assign to property: 'self' is immutable 에러
  }
}
```

메소드 내에서 사용되고 있는 someProperty는 인스턴스 프로퍼티가 아닌 인스턴스 프로퍼티인 someProperty 값을 복사한 복사본이다. 그럼 방법이 없는걸까 ?? 바로 mutating 키워드를 사용하면 된다.

### mutating

mutating 키워드를 사용하면 해당 메소드는 암시적인 self(인스턴스 그 자체)에 수정된 프로퍼티가 적용된 새로운 인스턴스를 만들어 두고 메소드가 종료되면 새로 만들어진 인스턴스로 기존 인스턴스를 대체하게 된다.

```swift
struct SomeStruct {
  var someProperty: Int = 5
  mutating func someMethod() {
    someProperty = 3
  }
}

var mStruct = SomeStruct()
print(mStruct.someProperty) // 5
mStruct.someMethod()
print.(mStruct.someProperty) // 3
```

### Mutating 메소드에 selft 할당

위의 코드에서 컴파일러가 자동으로 처리해준 것을 개발자가 직접 할 수 있다 !

```swift
struct SomeStruct {
  var someProperty: Int = 5
  mutating func someMethod() {
    self = SomeStruct(someProperty: 3)
  }
}

ar mStruct = SomeStruct()
print(mStruct.someProperty) // 5
mStruct.someMethod()
print.(mStruct.someProperty) // 3
```

---

## 타입 메서드

인스턴스 메서드와는 다르게 타입 자체에서 호출되는 메서드이다. 즉, 인스턴스를 생성하지 않고도 타입 자체에서 메서드를 호출할 수 있는 메서드이다. 타입 메서드는 static이나 class의 키워드가 붙는다는 특징이 있다.

### class 키워드

class 키워드를 사용해 타입 메서드를 생성해보자.

```swift
class Print {
  class func printMessage() {
    print("Hello")
  }
}

Print.printMessage()
```

- Print 라는 클래스를 만득고 안에 class 키워드를 이용해 타입 메서드 printMessage() 를 생성했다.
- printMessage() 메서드는 타입 메서드이므로 따로 인스턴스를 생성해줄 필요없이 타입 자체에서 호출이 가능하다
- 클래스에서는 상속이 가능하지만 구조체나 열거형에서는 상속이 불가능해 class 메서드를 선언할 수 없다. 오직 static !

### static 키워드

타입 메서드를 생성할 때는 class 키워드 말고도 static 키워드를 사용해 선언할 수 있다. 이 둘의 가장 큰 차이점은 오버라이드(override)가 가능하냐 불가능하냐의 차이점이다.

- static : 서브클래스에서 오버라이드 불가능
- class : 서브클래스에서 오버라이드 가능

```swift
class Print {
  static func printmessage()n{
    print("Hello")
  }
}

class Print2:Print {

  override class func printMessage() { // error
    print("Hello I'm saemi")
  }
}

Print2.printMesssage()
```

static 타입 메서드를 선언한 메서드는 오버라이딩이 불가능하기 때문에 에러가 발생한다.

---

## 함수와 메서드의 차이

함수를 사용하면 기능의 이름을 지정하고 반복적으로 실행할 수 있으며 Swift의 메서든 거의 동일한 작업을 수행한다.

- 메서드 : struct, enum 및 class 와 같은 유형에 속한다.
- 함수 : 함수는 struct, enum, class 와 같은 유형에 속하지 않는다.

둘 다 가변 매개 변수를 포함해 원하는 수의 매개 변수를 허용할 수 있으며 둘 다 값을 반환할 수 있다.

## 정리

- 인스턴스 메서드는 인스턴스에 속한 메서드이다.
- 값 타입의 메서드에서 프로퍼티를 수정하기 위해선 mutating 키워드를 사용해야 한다.
- 타팁 메서드는 타입 자체에 속한 메서드이다.
- self는 인스턴스 메서드에서는 인스턴스를 참조, 타입 메서드에서는 타입 자체를 의미한다.
