## SnapKit

> SnapKit은 UI Layout을 구성할 때 AutoLayout을 더 간결한 코드로 편리하게 작성할 수 있도록 도와주는 라이브러리이다.

### 왜 SnapKit을 사용할까 ?

SnapKit 라이브러리를 사용하지 않고 AutoLayout을 구성할 때 NSLayoutConstraint를 직접 지정해주며 하나하나 제약을 적용해 주어야한다.
이런 방법을 사용하면 화면 구성 요소들이 많아져 필요한 코드가 늘어나며 코드의 가독성이 떨어진다.
SnapKit은 이를 해결하기 위해 간결한 코드로 NSLayoutConstraint를 쉽게 제어할 수 있도록 해준다 !

### SnapKit Code 해석하기

순차적으로 해석하기

```swift
make.top.equalTo(saemi.snp.bottom).offset(18)
```

- 상단을 saemi의 하단과 동일하게 만들기
- offset은 18

### Anchor

- 모든 앵커와 제약 조건 자체를 함께 연결하는 것이 가능

```swift
child.snp.makeConstraints{make in
  make.lead.top.trailing.bottom.equalToSuperview()
}
```

- edge를 이용해 더욱 편하게 사용

```swift
child.snp.makeConstraints { make in
  make.edgees.equalToSuperview()
}
```

- view에 inset 값을 주고 싶은 경우 inset() 사용

```swift
child.snp.makeconstraints { make in
  make.edges.equalToSuperview().inset(16)
}
```

### Constraint

- muliipliedBy()

```swift
// superview의 너비와 같게 만들고 2 곱하기
make.width.equalToSuperview().mulipliedBy(2)
```

- offset()

```swift
// 상단을 viewProgress의 하단으로 제한하고, 20만큼 offset
make.top.equalTo(viewProgress.snp.bottom).offset(20)
```

- offset() vs inset()
  - offset() : element와의 간격에 사용
  - inset() : superview와의 간격에 사용

### 암시

- constraint 기준이 되는 View의 width, point를 지정하지 않아도 암시적으로 동일하도록 설정
- constraint 기준이 되는 View의 값을 최대한 짭게 작성할 수 있도록 도와준다.

```swift
// 아래 세 코드는 모두 같은 코드임 !
view.snap.makeConstraints { make in
  make.width.equalTo(otherView.snp.width)
  make.centerX.equalTo(otherView.snp.centerX)
}

view.snp.makeConstraints { make in
  make.width.equalTo(otherView)
  make.centerX.equalTo(otherView)
}

view.snp.makeConstraints { make in
  make.width.centerX.equalTo(otherView)
}
```

### updateConstraint

- constraint 기준이 될 기존에 지정한 view가 바뀌는게 아닌 constant value만 업데이트 하고 싶은 경우

```swift
extension QuizViewController {
  override func willTransition(
    to newCollection: UITraitCollection,
    with coordinator: UIViewControllerTransitionCoordinator
    ) {
    super.willTransition(to: newCollection, with: coordinator)

    // 현재 방향
    let isPortrait = UIDevice.current.orientation.isPortrait

    // 방향에 따른 label 높이 값 조정
    lblTimer.snp.updateConstraints { make in
      make.height.equalTo(isPortrait ? 45 : 65)
    }

    // 방향에 따른 font 크기 값 조정
    lblTimer.font = UIFont.systemFont(ofSize: isPortrait ? 20 : 32, weight: .light)
  }
}
```

### remakeConstraint

- constant value만 변경되는게 아닌 기준이 될 view도 바뀌는 경우
- 기존에 존재하던 constraints 삭제

```swift
func updateProgress(to progress: Double) {
  viewProgress.snp.remakeConstraints { make in
    make.top.equalTo(view.safeAreaLayoutGuide)
    make.width.equalToSuperview().multipliedBy(progress)
    make.height.equalTo(32)
    make.leading.equalToSuperview()
  }
}
```

### lessThanOrEqualTo, priority

- lessThenOrEqualTo() 추가하여 사용
- priority() 추가하여 사용

```swift
override func updateConstraints() {
    self.growingButton.snp.updateConstraints { (make) -> Void in
        make.center.equalTo(self);
        make.width.height.equalTo(buttonSize).priority(250)
        make.width.height.lessThanOrEqualTo(self)
    }

    super.updateConstraints()
}
```
