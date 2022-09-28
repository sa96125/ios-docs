---
description: 스위프트는 데이터 타입에 굉장히 엄격한 언어이다.
---

# types

### Base Types

* Any : All
* Bool : True or False
* Int : 64bit 정수
* Uint : 64bit 양의 정수
* Float : 32bit 부동 소수점
* Double : 64bit 부동 소수점
* Character : 유니코드
* String : 여러 문자를 담고 있는 문자

{% hint style="info" %}
스위프트 타입은 구조체로 이루어져 있다. 구조체의 특징 중 하나는 value type의 특성을 가진다는 것이다. 이 데이터 타입을 가진 변수를 복사 할때 깊은 복사가 되므로 이점을 꼭 기억하자.
{% endhint %}



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



### Tuple

관계된 값들을 묶을 수 있다. 튜플에 담는 값의 타입을 통일 될 필요가 없어 아무 값을 엮을 수 있지만 복잡한 데이터 구조를 만들 때 적절하지 않다. 특히 함수의 리턴타입으로 사용할 때 유용하다.

```swift
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
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

****

### **Any > AnyObject > NsObject**

* _Any_ : 모든 타입을 포괄하는 데이터 타입
* _AnyObject_ : 클래스로 생성된 형태만 수용하는 데이터 타입
* _NsObject_ : 오직 NS type만 수용



### Enums

서로 관련된 값의 그룹을 위한 타입을 정의하고 코드에서 타입 세이프 방법으로 값을 동작하게 한다. 아래의 코드로 이 의미를 알아보자.

```swift
// 자동차에는 여러 타입이 존재하고 아래의 코드는 2번 자동차의 타입을 할당했다.
// 2라는 숫자는 너무 추상적이다.
var typeOfCar = 2

// 2 대신 구체적인 값을 그룹으로 정의했다.
enum CarType {
	case sedan
	case coupe
	case hatchback
}

// enum에 정의된 값중 하나를 안전하게 사용할 수 있다.
var typeOfCar: CarType = .sedan
```



### Generic

타입에 의존하지 않는 코드를 작성하는 방법이다. 스위프트에서는 엄격한 타입 정의를 기반으로 코드를 실행한다. 실제로 문자열이 들어와야만 실행되는 함수가 존재하고 사칙연산을 수행하는 함수인 경우는 Int 혹은 Float, Double 타입만이 올바르게 동작한다.&#x20;

하지만 예외도 있다. 평소 우리가 배열을 타입을 결정할 때, Array\<type>의 형식으로 배열의 실제 형태를 할당하는데 이때 사용된 것이 제네릭이다.

```swift
// 함수를 정의할 때 사용할 수 있을 뿐만 아니라
// 앞서 배열의 예로 볼 때 구조체, 클래스를 정의할 때도 사용할 수 있다.
struct Stack<T> {
    let items: [T] = []
 
    mutating func push(_ item: T) { ... }
    mutating func pop() -> T { ... }
}

```

