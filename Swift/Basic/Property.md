## Property

> 프로퍼티는 구조체, 클래스, 열거형 내부에 구현해 타입과 연관된 값들을 표현할 때 사용한다.

- 저장 프로퍼티
- 연산 프로퍼티
- 인스턴스 프로퍼티
- 타입 프로퍼티

### 정의

```swift
struct Student {
  // 인스턴스 저장 프로퍼티
  var name: String = ""
  var 'class': String ="Swift"
  var koreanAge: Int = 0

  // 인스턴스 연산 프로퍼티
  var westernAge: Int {
    get {
      return koreanAge - 1
    }
    set(inputValue) {
      koreanAge = inputValue + 1
    }
  }

  // 타입 저장 프로퍼티
  static var typeDescription: String = "학생"

  // 읽기 전용 인스턴스 연산 프로퍼티
  var selfIntroduction: String {
    get {
      return "저는 \(self.class)반 \(name)입니다"
    }
  }
}
```

### 예제

```swift
struct Money {
  var currencyRate: Double = 1100
  var dollar: Double = 0
  var won: Double {
    get {
      return dollar * currencyRate
    }
    set {
      dollar = newValue / currencyRate
    }
  }
}

var moneyInMyPocket = Money()

moneyInMyPocket.won = 11000
print(moneyInMyPocket.won) // 11000

moneyInMyPocket.dollar = 10
print(moneyInMyPocket.won) // 11000
```
