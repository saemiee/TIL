## Then

> Swift initializers를 위한 라이브러리로 클로저를 이용한 인스턴스 초기화를 좀 더 깔끔하게 사용할 수 있도록 도와주는 라이브러리이다.

### Then 라이브러리를 사용하지 않았을 때

Then 을 사용하지 않았을 때 UILabel 초기화 하기

```swift
 let label: UILabel = {

      let label = UILabel()

      label.textColor = .black

      label.text = "Hello, World!"

      return label

    }()
```

### Then 라이브러리를 사용했을 때

Then 을 사용했을 때 UILabel 초기화 하기

```swift
let label = UILabel().then {

  $0.textColor = .black

  $0.text = "Hello, World!"

}
```

훨씬 깔끔해졌다 !
