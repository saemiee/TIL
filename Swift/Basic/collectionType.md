## 컬렉션 타입
Swift에서는 값을 저장하기 위한 세 가지 컬렉션 타입을 제공한다.
* Array - 넣은 순서대로 저장되는 컬렉션
* Dictionary - key-value 관계를 갖는 순서없는 컬렉션 Set - 값이 중복되지 않은 순서없는 컬렉션
* Set - 값이 중복되지 않은 순서없는 컬렉션

### Array
* 배열 생성
```swift
var saemi: Array<Int> = Array(Int)() // 빈 배열 생성
var potato: [String] = []
```

* 값 추가
```swift
saemi.append(1) // [1]
saemi.append(18) // [1, 18]
```

* 원소 확인
```swift
saemi.contains(100) // fale
saemi.contains(18) // true

saemi.count // 원소 갯수
```

* 원소 삭제
```swift
saemi.remove(at: 0) // [18]
saemi.removeLast() // [1]
saemi.removeAll() // []
```

### Dictionary 
* 딕셔너리 생성
```swift
var cat: Dictionary<String, Any> = [String: Any]()
var some: [String: String] = [:]
```

* 값 할당
```swift
cat["someKey"] = "value"
cat["고양이"] = "츄르"
```

* 값 삭제
```swift
cat.removeValue(forKey: "고양이") // 키에 해당하는 값 삭제
cat["고양이"] = nil
```

### Set
* set 생성
```swift
var newSet: Set<Int> = Set<Int>()
var Sett: Set<int> = [3,5,35,6]
```

* 요소 추가
```swift
newSet.insert(1)
newSet.insert(18)
newSet.insert(7)
newSet.insert(7)
newSet.insert(7) // newSet{1,18,7}
```

* 요소 확인
```swift
newSet.contains(18) // true
newSet.contains(6) // false

newSet.count
```

* 요소 삭제
```swift
newSet.remove(1)
newsEt.removeFirst()

* Set 연산
```swift
let setA: Set<Int> = [1, 2, 3, 4, 5] // {1,2,3,4,5}
let setB: Set<Int> = [3, 4, 5, 6, 7] // {3,4,5,6,7}

let union: Set<Int> = setA.union(setB) // 합집합 구하기 {1,2,5,3,7,6,4}
let sortedUnion: [Int] = union.stored() // 집합 정렬하기 [1,2,3,4,5,6,7]
let intersection: Set<Int> = setA.intersection(setB) // 교집합 구하기 {3,4,5}
let subtracting: Set<Int> = setA.subtracting(setB) // 차집합 구하기 {2,1}
```

