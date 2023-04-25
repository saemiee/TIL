## 구조체

> Swift의 구조체는 타입을 정의한다.

### 프로퍼티와 메서드

- 프로퍼티 - 구조체 안의 인스턴스 변수
- 메서드 - 구조체 안의 함수

```swift
struct Sample {
  var mutableProperty: Int = 100 // 가변 프로퍼티
  let immutableProperty: Int = 100 // 불변 프로퍼티

  static var typeProperty: Int = 100 // 타입 프로퍼티

  // 인스턴스 메서드
  func instanceMethod() {
    print("instance method")
  }

  // 타입 메서드
  static func typeMethod() {
    print("type emthod")
  }
}
```

### 구조체 사용

```swift
// 가변 인스턴스
var mutable: Sample = Sample()
mrtable.mutableProperty = 200

// 불변 인스턴스
let immutable: Sample = Sample() // 값 변경 불가

// 타입 프로퍼티 및 메서드
Sample.typeProperty = 300
Sample.typeMethod() // type method
// mutable.typeProperty = 200 인스턴스에서 타입 프로퍼티를 사용하는 것은 불가능하다.
```

### 구조체 예제

```swift
struct Student {
  var name: String = "unkonwn"
  var 'class': String = "Swift"

  static func selfIntroduve() {
    print("학생타입입니다")
  }
  func selfIntroduce() {
    print("저는 \(self.class)반 \(name)입니다")
  }
}

Student.selfIntroduce() // 학생타입입니다

var saemi: Student = Strudent()
saemi.name = "새미"
saemi.class = "iOS"
saemi.selfIntroduce() // 저는 iOS반 새미입니다

let cat: Student = Student()
// 불변 인스턴스이므로 프로퍼티 값 변경 불가
// 컴파일 오류 발생
cat.selfIntroduce() // 저는 Swift반 unkonwn입니다
```
