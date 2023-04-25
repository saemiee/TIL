## enum

> enum은 서로 관계있는 값들을 모아서 표현한것이다. 열거형은 깔끔한 코드를 작성하는데 도움을 준다. 간단하게 말하자면 상수 역할 값들을 보기 쉽게 나열해 놓은 것이다.

```swift
enum WeekDay {
  case mon
  case tue
  case wed
  case thu
  case fri
}

var today: WeekDay = .mon

enum MediaType {
  case audio
  case video
}

var mediaType: MediaType = .audio
```

### Why ?

enum은 사용하면 뭐가 좋을까?

- 코드가 보기 쉽고 간결해진다.
- 코드를 작성할 때 실수를 줄일 수 있다.
- 코드를 작성하기 편리하다.
