## Optional

> 옵셔널은 "선택적인"이라고 직역할 수 있다. 옵셔널 변수에는 값이 들어갈 수도 있고, 아닐 수도(nil)있음을 의미한다.

### Optional 사용법

```swift
var name1: String = nil  // error
var name2: String? = nil
var name3: String? = 'saemi'
```

Swift는 기본적으로 변수 선언시 nil 값이 들어가는 것을 허용하지 않는다.
런타임 에러를 뿜는 것이 아니라 아예 컴파일 에러를 내버린다.

### ? 와 !의 차이

- ?

```swift
var someValue: Int? = 30
var Value = someValue // Optional 타입
```

- !
  강제 언래핑 하는 방식이다. 아래의 예제를 보면 ? 를 사용했을 때 오류가 발생한다.

```swift
var someValue: Int? = 30
var Value: Int = someValue
```

하지만 아래와 같이 강제 언래핑을 해주면 오류가 사라지게 된다.

```swift
var someValue: Int? = 30
var Value: Int = someValue!
```

만약 옵셔널 값 안이 nill 이라면 런타임 에러가 발생하게 된다.
그러니 ! 사용은 조심해서 사용하기 !

### Optional 변수의 값 가져오기

- 옵셔널 바인딩 (Optional Binding)
  옵셔널 바인딩은 주로 if let(또는 if var) 구문과 함께 쓰인다.
  nil인지, 값이 있는지 경우에 따라 결과를 달리 할 때 사용한다.

```swift
func print(_name: String){
  print(_name)
}

var myName: String? = nill
if let name = myName {
  printName(_name: name)
}
```

myNmae이라는 상자에 노크해보고 값이 있으면 name에 넣어주고 조건문을 실행한다.
하지만 위의 예제의 myNmae 속에는 nill 있기 때문에 조건문은 실행되지 않는다.
값이 있을 때만 값이 바인딩 되기 때문이다.

- 옵셔널 체이닝 (Optional Chaining)
  옵셔널 체이닝은 하위 property에 optional 값이 있는지 연속적으로 확인하면서 중간에 하나라도 nill이 발견되면 nill이 반환되는 형식이다.

```swift
class Person {
  var residence: Residence?
}

class Residence {
  var numberOfRooms = 1
}

let zedd = Person()

if let roomCount = zedd.residence?.numberOfRooms {
  print("zedd's residence has \(roomCount) room(s).")
} else {
  print("Unable to retrieve the number of romms.")
}

// Unable to retrieve the number of rooms.
```

정리하면 하위 프로퍼티에 Optional 값이 있는지 연속적으로 확인하면서 중간에 하나라도 nill이 발견된다면 nill이 반환하는 것이 옵셔널 체이닝 방식이다.

### !는 언제 사용하면 좋을까 ?

변수에 값이 있다는 것을 확신할 수 있는 경우에는 옵셔널 바인딩과 옵셔널 체이닝을 굳이 이용하지 않아도 된다.
이런 종류의 옵셔널을 implicityl unwrapped optionals이라고 정의한다.
무조건적으로 언랩핑된 옵셔널, 암시적으로 업랩핑된 옵셔널이라고 할 수 있다.

정리하면 옵셔널 바인딩, 체이닝으로 매번 값을 추출하기 귀찮거나 로직상으로 nill이 할당되지 않을 것 같다는 확신이 들 때 사용하기 !
 