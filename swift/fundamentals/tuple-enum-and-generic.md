# tuple, enum and generic

### Tuple

두 관계된 값을 묶을 수 있습니다. 튜플에 담는 값의 타입은 통일 될 필요가 없습니다. 튜플은 복잡한 데이터 구조를 만들 때 적절하지 않습니다. 단순한 데이터 구조가 필요할 때, 특히 함수의 리턴타입으로 사용할 때 유용하게 사용될 수 있습니다.



```swift
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
```





### Enums

열거형은 타입계의 패스파인더로 서로 **관련된 값의 그룹을 위한 타입을 정의**하고 코드에서 타입 세이프 방법으로 값을 동작하게 합니다.



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

Swift에서 강력한 기능중에 하나로 타입에 의존하지 않는 코드를 작성하는 방법이다. 스위프트에서는 엄격한 타입 검사하에 프로그램을 실행합니다. 이로인해 같은 기능일지라도 타입별로 기능을 구현했습니다. 하지만 제네릭을 사용하면 **타입 리미터를 해제**함으로서 더 적은 코드로 확장성있는 코드를 작성할 수 있습니다.



```swift
// 함수를 정의할 때 사용할 수 있을 뿐만 아니라
// 앞서 배열의 예로 볼 때 구조체, 클래스를 정의할 때도 사용할 수 있다.
struct Stack<T> {
    let items: [T] = []
 
    mutating func push(_ item: T) { ... }
    mutating func pop() -> T { ... }
}

```







### Type Alias

미리 정의된 타입을 위한 약어를 정의하는 키워드입니다. 이전에 Decodable타입은 Encodable타입과 동시에 사용할 수 없는데 이때 Codable을 사용하면 둘다 허용된 타입을 사용할 수 있습니다.

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

