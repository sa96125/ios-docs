# collection types

스위프트에서는 값들을 저장하기 위해 3가지 기본 컬렉션 타입을 가집니다. 컬렉션 타입을 var에 할당하면 크기와 내용을 변경할 수 있지만, let에 할당하면 불가능합니다.

* Array : **순서가 있는** 값의 모음
* Set : 순서가 없고 **고유한 값**의 모음
* Dictionary : 순서가 없고 **키와 연결**된 값의 모음



### Array

```swift
// 빈 배열 선언
var dogs: Array<String> = []
var cats: [String] = []
let people = Array<String>() 
let pets = [String]()


// 배열에 포함된 값을 순
for item in items {
    print(item)
}


// 배열에 포함된 인덱스와 값을 순회 
for (index, value) in shoppingList.enumerated() {
    print("Item \\(index + 1): \\(value)")
}


// 고차 함수
items.map{ print($0) }


// 배열 메서드
Array.isEmpty
Array.count
Array.append(value)
Array.insert(value, at:)
Array.remove(at:)
Array.removeLast()
```





### Set

Set에는 Hashtable type의 값만을 저장할 수 있습니다. Swift의 기본 타입이 이에 해당합니다.

```swift
// Set 선언
var letters = Set<Character>()


// Set 순서가 없고 효율적인 방식으로 알아서 순회
for genre in favoriteGenres {
    print("\\(genre)")
}


// 순서가 있는 배열 형태로 변환
for genre in favoriteGenres.sorted() {
    print("\\(genre)")
}


// Set 메서드, 합집합/ 교집합/ 여집합/ 정
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted() // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted() // []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted() // [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted() // [1, 2, 9]


// Set 메서드, 합집합/ 교집합/ 여집합 확인
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals) // true
farmAnimals.isSuperset(of: houseAnimals) // true
farmAnimals.isDisjoint(with: cityAnimals) // true


// Set 메서드
Set.isEmpty
Set.count
Set.insert(value, at:)
Set.remove(at:)
```





### Dictionary

```swift
// 딕셔너리 선
var lastNames: [Int: String] = [:]


// 값 할당
lastNames["jake"] = "Park"


// 딕셔너리에 포함된 키,값을 순회
for (airportCode, airportName) in airports {
    print("\\(airportCode): \\(airportName)")
}


// 딕셔너리에 포함된 키 순회
for airportCode in airports.keys {
    print("Airport code: \\(airportCode)")
}


// 딕셔너리에 포함된 값 순회
for airportName in airports.values {
    print("Airport name: \\(airportName)")
}


// 딕셔너리 메서드
Dictionary.isEmpty
```

