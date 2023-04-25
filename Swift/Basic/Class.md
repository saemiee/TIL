## Class

> 클래스는 객체 지향 프로그래밍(OOP)에서 특정 객체를 생성하기 위해 변수와 메소드를 정의하는 일종의 틀을 말한다. 객체를 정의 학 위한 상태(멤버변수)와 메서드(함수)로 구성된다.

### 클래스의 특징

- 참조타입이다.
- iOS 프레임워크의 대부분이 클래스로 구성되어있다.
- 단일 상속만 가능하다. 다중 상속은 불가능

### Class 구조

- 클래스는 키워드 `class`를 통해 생성된다.

```swift
class ClassName
{
}
```

- 클래스의 프로퍼티란 객체가 가지고 있는 속성이다.
- 즉 다음과 같은 변수들은 프로퍼티다.

```swift
class ClassName
{
	var name: String = "스위프트 프로그래밍"
	var grade: Int = 100
}
```

### 객체 만들기

- 객체를 만든다는 것은 곧, 클래스의 인스턴스를 생성하는 것이다.
- 다음과 같이 만들 수 있다.

```swift
var example: ClassName = ClassName()
```

- 여기서 `ClassName`은 사실상 `ClassName.init`과 같다.

### Class의 초기화 방법

- 클래스는 기본적으로 다음과 같이 초기화가 이뤄진다.

```swift
nit()
{
}
```

- 엄밀히 따지면, ClassName.init()이라고 초기화해줘야 하는데.
- ClassName()과 같이 생략해서 초기화 할 수도 있는 것이다.
- 이 초기화를 다음과 같이 사용자화 할 수도 있다.

```swift
class ClassName
{
	var name: String = "스위프트 프로그래밍"
	var grade: Int = 100

	init(name: String, grade: Int)
	{
		self.name = name
		self.grade = grade
	}
}
```
