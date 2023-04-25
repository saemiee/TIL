## Tuple

> 튜플은 어떠한 값들의 묶음이다. 배열과 비슷하다고 볼 수 있는데 배열과는 다르게 길이가 고정되어 있다. 값에 접근할 때도 [] 대신 .을 사용한다.

```swift
car coffeeInfo = (coffee: "아메리카노", price: 5000)
coffeeInfo.0 // 아메리카노
coffeInfo.1 // 5000
```

실제로 간단한 자료형을 만들 때는 구조체 대신 튜플을 사용해서 만들기도 한다.

```swift
let(_, latteSize, latterPrice) = ("라떼", "Venti", 5600)
latteSize // Venti
lattePrice // 5600
```

### 튜플의 타입 어노테이션

```swift
var coffeeInfo: (String, Int)
var namedCoffeeInfo: (coffee: String, price: Int)
```

### 여러 변수에 값 저장

```swift
let (coffee, price) = ("아메리카노", 5000)
coffee // 아메리카노
price // 5000
```

### 튜플을 반환하는 함수

```swift
func coffeeInfo(for name: String) -> (name: String, price: Int)? {
  let coffeeInfoList: [(name: String, price: Int)] = [
    ("아메리카노", 5000),
    ("라떼", 5600),
  ]
  for coffeeInfo in coffeeInforList {
    if coffeeInfo.name == name {
      return coffeeInfo
    }
  }
  return nil
}

coffeeInfo(for: "아메리카노")?.price // 5000
coffeeInfo(for: "에스프레소")?.price // nil

let (_, lattePrice) = coffeeInfo(fro: "라떼")!
lattePrice // 56000
```
