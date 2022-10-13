# collection types

스위프트에서는 값들을 저장하기 위해 3가지 기본 컬렉션 타입을 가집니다. 컬렉션 타입을 var에 할당하면 크기와 내용을 변경할 수 있지만, let에 할당하면 불가능합니다.

* Array : 순서가 있는 값의 모음
* Set : 순서가 없고 고유한 값의 모음
* Dictionary : 순서가 없고 키와 연결된 값의 모음



### Array

```swift
// array[index]
var dogs: Array<String> = []
var cats: [String] = []
let people = Array<String>() 
let pets = [String]()

for item in shoppingList {
    print(item)
}

for (index, value) in shoppingList.enumerated() {
    print("Item \\(index + 1): \\(value)")
}
```





### Set

```swift
var letters = Set<Character>()

for genre in favoriteGenres {
    print("\\(genre)")
}

// Set은 순서가 없지만 순서가 있는 배열 형태로 변환 가능
for genre in favoriteGenres.sorted() {
    print("\\(genre)")
}



let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]



let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```





### Dictionary

```swift
// dictionary[key]
var namesOfIntegers: [Int: String] = [:]

for (airportCode, airportName) in airports {
    print("\\(airportCode): \\(airportName)")
}

for airportCode in airports.keys {
    print("Airport code: \\(airportCode)")
}

for airportName in airports.values {
    print("Airport name: \\(airportName)")
}
```

