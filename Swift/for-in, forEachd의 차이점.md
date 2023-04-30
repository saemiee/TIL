## for-in , forEach 제대로 알고 쓰기

for-in과 forEach의 차이점에 대해 정확히 알고가기 !

### for-in

컬렉션에 저장된 요소 수만큼 반복되며, 저장된 요소가 루프 상수에 하나씩 들어간다.

- Array

```swift
let nums: [Int] = [1, 2, 3, 4]

for num in nums {
  print(num) // 1 2 3 4
}
```

- Dictionary

```swift
let dict: [String: Int] = ["A" : 1, "B" : 2 , "C", 3]

for (key, value) in dict {
  print("\(key) : \(value)")
}

for element in dict {
    print("\(element.key) : \(element.value))")
}

// 키 또는 value만 반복하고 싶다면 ?
for key in dict.keys {
  print(key)
}

for value in dict.values.sorted(){
  print(value)
}
```

정렬 함수인 sorted 함수는 key, value 둘 다 사용할 수 있다.

- Set

```swift
let nums: Set<Int> = [1, 2, 3, 4]

for num in nums {
  print(num) // 3 4 1 2
}
```

### forEach

반복 실행하려는 코드를 파라미터로 받고, 저장된 요소는 클로저 상수로 전달된다.

- Array

````swift
let nums: [Int] = [1, 2, 3, 4]

nums.forEach {
  print($0) // 1 2 3 4
}

* Dictionary
```swift
let dict: [String : Int] = ["A" : 1, "B" : 2 , "C", 3]

dict.forEach {
    print("(\($0.key) : \($0.value))")
}

dict.forEach { (key, value) in
    print("(\(key) : \(value))")
}

dict.keys.forEach {
    print($0)
}

dict.values.sorted().forEach {
    print($0)
}
````

- Set

```swift
let nums: Set<Int> = [1, 2, 3, 4]

nums.forEach {
  print($0) // 2 3 1 4
}
```

### for-in과 forEach의 차이점

- continue와 break
  for-in문은 직접 구현하는 반복문이다. 하지만 forEach는 내가 반복하고 싶은 구문을 forEach라는 함수의 파라미터로 클로저로 작성해서 넘겨주는 것이다. 그렇기 때문에 반복문 안에서만 사용할 수 있는 continue, break는 for-in 에서는 사용이 가능하지만, forEach에서는 불가능하다.
  -> forEach는 반복문이 아니라 클로저를 파라미터로 넘겨주는 메서드이다.
- return문의 영향

```swift
// for-in
func printForIn() {
  let nums = [1, 2, 3]

  for num in nums {
    print(num)
    return // 1
  }
} // 반복문을 돌다가 return을 만나면 함수 자체가 종료된다.

// forEach
func printForEach() {
  let nums = [1, 2, 3]

  nums.forEach {
    print($0)
    return // 1 2 3
  }
}
```

forEach는 반복문이 아닌 클로저 즉, 반복하고자 하는 내용을 익명 함수를 전달하기 때문에 return을 만난다는 것은 내가 전달한 클로저를 종료하는 것을 뜻한다. forEach는 내가 전달한 클로저를 요소 갯수 만큼이나 실행한다. 따라서 1번째 반복 땐 1을 프린트하고 클로저를 return 해버려서 바로 다음 2번째 반복 클로저가 실행된다.
-> 반복 횟수에 영향을 주지않음
