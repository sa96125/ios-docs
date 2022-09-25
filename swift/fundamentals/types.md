# types

### Collection Types

스위프트에서는 값을 저장하기 위해 3가지 기본 컬렉션 타입을 가진다.

* 순서가 있는 값의 모음
* 순서가 없고 고유한 값의 모음
* 순서가 없고 키와 연결된 값의 모음

이러한 특징을 가진 타입을 순서대로 배열, 셋, 딕셔너리라 한다. 이 컬렉션을 var에 할당하면 크기와 내용을 변경할 수 있지만, let에 할당하면 불가능하다.

```swift
// Array
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

```swift
// Set
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

```swift
// Dictionary
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



### Type Alias

미리 정의된 타입을 위한 약어. 이전에 Decodable타입은 Encodable타입과 동시에 사용할 수 없는데 이때 Codable을 사용하면 둘다 허용된 타입을 사용할 수 있다.

```swift
typealias Codable = Decodable & Encodable
```



### Type Casting

검을 가공하는 프로세스를 연상한다.

```swift
class Animal {
	var name: String?
	init(n: String){
		name : n
	}
}

class Humen : Animal {
}

class Fish : Animal {
	func breatheUnderWater() {
		print("pu pu pu")
	}
}

let jake = Humen(n: "Jake park")
let anjela = Humen(n: "Angela Yu")
let nemo = Fish(n: "Nemo")
let animals = [jake, anjela, nemo]

// type checking
if jack is Human {
	return
}

// Upcast
// convert subclass in to superclass
let animalFish = fish as Animal

// Forced Downcast
// convert superclass into subclass
func findNemo(from animals: [Animal]) {
	for animal in animals {
		if animal is Fish {
			print(animal.name)

			// 코드에 적힌 이상 animal 자체는 Animal 타입이므로,
			let fish = animal as! Fish
			fish.breatheUnderWater()
		}
	}
}

// optional cast
func findNemo(from animals: [Animal]) {
	for animal in animals {
		if animal is Fish {
			print(animal.name)

			// 확신 하지 않을 때, 더욱 안전한 방법으로 처리할 수 있다.
			if let fish = animal as? Fish {
				fish?.breatheUnderWater()
			} else {
				print("casting has failed")
			}			
		}
	}
}
```



### Any, AnyObject, NsObject

Any 모든 타입을 포괄하는 데이터 타입

AnyObject 클래스로 생성된 형태만 수용하는 데이터 타입

NsObject 오직 NS type만 수용
