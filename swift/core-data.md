# Core Data

### if, Switch

범위가 클수록 패턴 매칭이 if구문보다 효율적이고 읽기 쉬운 코드가 된다. swich를 사용할 때, 꼭 범위 외의 사항에 대한 처리가 필요하며 이는 default에서 처리한다. 또한 각각의 범위는 … / ..< 와 같은 범위 연산 키워드를 사용하여 설정할 수 있다.



### Function

Input과 output이 없을 경우, () {}

Input만 있을 경우 (parameter: DataType)

Output만 있을 경우 () returnArrow DataType { return Keyword value } 로 정의할 수 있다.



### Structure

커스텀 데이터 타입을 만들어 사용할 수 있다. 기존 데이터 타입들은 이 구조를 활용되어 만들어졌고 이미 Prebuilt 되어 있어 사용할 수 있는 것이다. 내가 필요한 타입들을 모아 스트럭쳐를 구성할 수 있고 초기화하여 사용할 수 있다. 객체를 생성하는 블루프린트로 불리기도 한다. 이 구성은 프로퍼티 혹은 메서드로 구성 될 수 있다.

structure에 사용할 데이터를 모두 담아둘 수도 있지만, initialize를 통해 생성과 동시에 데이터를 담아 둘 수 있다는 장점이 있다. 하지만 굳이 생성자가 필요없는 경우는 생략하는 것이 정석이다. 블루프린트라는 의미는 프로퍼티, 메서드를 통해 그 형태를 만들어 놓는다는 것이고 생성자를 통해 고유한 특징을 입힘으로서 특정 객체를 나타낼 수 있는 것이다. 예를 들어 다양한 자동차, 국가라는 형태를 잡고 색, 성향, 리소스 즉 데이터를 추가함으로서 고유한 객체를 생성할 수 있게 된다.



### Self keword

자바스크립트의 this와 같다. 즉 실제 생성될 객체를 가르킨다. 블루프린트를 통해 생성된 객체는 각기 다른 특성을 가지고 있다. self를 통해 각각 생성된 객체의 프로퍼티 또는 메서드에 접근할 수 있게 된다. 클래스 내에서 self를 생략해도 스위프트가 알아서 찾아 낼 수 있지만 클로저를 사용할 경우, self를 생각해서는 안된다.



### Immutability

let과 같은 키워드를 사용하면 값의 수정이 불가능한데 이를 immutable이라고 한다. 앞서 설명한 구조체를 예로들면, 구조체를 구성하는 프로퍼티 변수를 수정하는 일이 있을 수 있다. 실제 인스턴스에서 이 변수를 수정하는 일이 발생하면 메서드를 사용해야하는데 이때 메서드 속에는 self 키워드로 구조체 변수에 접근하는 로직이 작성된다. **주의할 점은 구조체의 self는 인스턴스 생성시 let으로 생성되기 때문에 변수를 수정하는 것이 불가능하다.** 이때 구조체에서 var로 선언된 변수를 수정하기 위해서는 mutating이라는 키워드로 메서드를 선언해야한다. 이때는 self 키워드를 사용하지 않아도 변수에 접근할 수 있다.&#x20;



### Optional

값이 있을 수도 없을 수도 있는 변수의 타입을 의미한다. nil을 할당하면 기존 값을 없애는 것과 같은 행동이고 결국 실행해 다다랐을 때 런타임 오류가 발생한다. 옵셔널로 할당 된 값은 값이 존재할 때의 처리와 nil일 경우의 처리를 해야한다. 즉, nil crushing으로 인한 런타임 오류가 유일한 이슈 사항이니 주의가 필요하.

1.  Force Unwrapping never gonna be NIL&#x20;

    하지만 값이 할당되지 않은 옵셔널을 경우 Nil만 가지고 있어 런타임 오류가 발생한다.
2.  Check for nil value

    ```swift
    if optional != nil {
    	optional!
    } else {
    	print("myOptional was found to be nil")
    }
    ```
3.  Optional Binding

    ```swift
    // !을 사용하지 않고 check nil
    if let safeOptional = myOptional {
    	let text:String = safeOptional
    } else {
    	print("myOptional was found to be nil")
    }
    ```
4.  Nil Coalescing Operator

    ```swift
    // more clear way
    optional ?? defaultValue
    ```
5.  Optional Chaining

    ```swift
    // : Struct? , : Class? 에서도 사용 가능
    // nil이 아니면 프로퍼티 또는 메서드 실행, nil이면 실행하지 않음.
    optoinal?.pro
    ```

####

### External Parameter Name & \_

함수를 호출할 때 사용할 파라미터 이름을 재정의하거나 생략할 수 있는 방법

```swift
// func performRequest(urlString: String)
// performRequest(urlString: urlString)
// more readable
func performRequest(urlString: String)
performRequest(with: urlString)

```

####

### Order of mathematical operations

대괄호, 제곱, 곱셈 or 나눗셈, 플러스 or 마이너스 순서로 계산한다. 주의할점은 컴퓨터가 같은 우선순위를 계산할 경우 왼쪽에서 부터 차례대로 연산하게 된다



### Class

구조체와 유사하지만 클래스의 경우 슈퍼클래스로부터 상속이 가능하다는 점이 다르다. 상속이란 부모가 가진 특징을 그대로 물려받아 사용할 수 있을 뿐만 아니라 추가적인 능력을 추가할 수 있는 것을 의미한다. 미리 작성된 코드를 사용하게 되어 코드를 생성, 반복하는 작업을 줄일 수 있다. 개인적으로 클래스를 한단어로 표현한다면 **파생**이라 말할 수 잇을 것 같다. 물려받은 능력을 그대로 사용하거나 변형되거나 마치 진화하는 모습처럼. 서브클래스로 만든 인스턴스로 부모로 부터 물려받은 변수를 변경하거나 메서드를 호출하는 것이 가능하다. 부모는 자식을 위해 모든 것을 해주는 모습처럼 여길 수 있을 것 같다. 서브 클래스내에서의 메서드를 변경할때 override, super 키워드를 사용할 수 있.

* passed by reference //의도치 않게 변경할 수 있는 위험요소 발생 가능성(다중 스레드 환경에서 주의)
* inheritance
* init is necessary
* mutable

공식문서에서는 객체를 만들 필요성이 있을 때 먼저 구조체 형식으로 만드는 것을 권장한다. 클래스를 let으로 선언할 경우, 구성하고 있는 프로퍼티와 메서드의 접근이 불가능하다.



### Protocol(certificate)

프로토콜의 기능을 알기 전에 먼저 어떤 문제가 있었는지에 대해 알 필요가 있다. 클래스간 상속을 통해 코드의 중복을 피하고 슈퍼클래스의 특성을 서브클래스에서 재사용할 수 있고 뿐만 아니라 그 기능을 재 정의할 수 있다는 것을 배웠다. 하지만 특수한 예로, 부모의 기능을 사용하지 않는 경우라면 어떻게 해야할까? 상속의 특성상 서브클래스는 무조껀 슈퍼클래스의 기능을 사용할 수 있다. 이처럼 불필요한 동작의 기능을 막기 위해 그 기능을 분리 시켜야할 경우 프로토콜을 사용하여 구조체, 혹은 클래스에서 정의하도록 도와준다.

프로토콜을 정의할 때, 메서드의 이름만 작성해야하고 프로토콜을 호출하는 구조체와 클래스에서 무조껀 그 메서드 이름에 해당하는 기능을 작성해야한다. 뿐만아니라 해당 기능을 가진 오브젝트를 파라메터로 사용할 수 있는 변수의 타입으로도 지정할 수 있다. 이를 통해 알수 있는 것은 프로토콜의 기능을 활용하면 쓸대없는 클래스 상속을 피할 수 있고 데이터타입을 확장된 형태로도 나타낼 수 있게 된다. 또한 프로토콜이 사용된 클래스와 구조체에서는 해당하는 기능이 무조껀 들어있다는 것도 명시적으로 알 수 있다. 여러개를 사용할 수 있고, 상속과 함께 그 다음에 붙여서 사용할 수도 있다.

여기서 알 수 있는 부분은 모든 능력을 물려줘야하는 상속이 필요하다면 클래스를 사용하고, 어디에서든 사용할 수 있는 기능을 구현해야할 필요가 있을 때 프로토콜을 사용, 그외에 여러 변수를 담는다던지, 객체를 만들어야할 때는 기본적으로 구조체를 할용할 수 있다. 구조체의 경우 값의 복사 참조의 특성을 가져 안전한 사용이 가능한데 프로토콜덕분에 클래스의 상속 개념을 사용하여 모듈화할 수 있습니다.



### Closures

이름이 없는 함수, Anonymous Function이라 부른다. func 키워드와 함수이름을 지우고 첫 번째 중괄호를 이동 후 In 키워드를 추가하여 작성한다. 컴파일러가 타입을 추론할 수 있어 인풋과 아웃풋의 타입을 생략할 수 있다. Return 키워드, 파라미터 또한 생략가능하다.

```swift
func calculator(n1: Int, n2: Int, operation:(Int, Int) -> Int) -> Int {
	return operation(n1, n2)
}

func add(n1: Int, n2: Int) -> Int {
	return n1 + n2
}

or

func calculator(n1: Int, n2: Int, operation:(Int, Int) -> Int) -> Int {
	return operation(n1, n2)
}

// 1. default
calculator(n1: 2, n2: 3, operation: {(no1: Int, no2: Int) -> Int in 
	return no1 * no2 
})

// 2. omit
calculator(n1: 2, n2: 3, operation: {$0 * $1})

// 3. trailing closure : 콜백함수가 마지막 파라메터일 경우 분리하여 작성
calculator(n1: 2, n2: 3) {$0 * $1}

// 4. 실전
// 배열의 각요소 1씩 더하기, 클로저가 마지막이라 () 생략.
array.map{$0 + 1}

// 배열의 각요소 문자열 변환
array.map{"\\($0)"}
```

보다시피 클로저를 사용하면 코드를 줄여 간단하게 작성할 수 있다는 것이다. 하지만 읽기 좋은 코드가 되기 힘들다. 읽기좋은 코드와 간결한 코드를 적절한 밸런스로 작성하는 능력은 중요하며 온전히 코드를 작성하는 사람에게 달렸다.



### Computed Variable

특정 프로퍼티의 영향으로 추출할 수 있는 값을 만들 수 있다. 로직을 굳이 메서드로 표현할 필요가 없다. 항상 var 키워드로 선언해야한다는 것이 특징

```swift
struct WeatherModel {
    let conditionId: Int
    let cityName: String
    let tamperature: Double
    
    var conditionName: String {
        switch conditionId {
        case 200...232:
            return "cloud.bolt"
        case 300...321:
            return "cloud.drizzle"
        case 500...531:
            return "cloud.rain"
        case 600...622:
            return "cloud.snow"
        case 700...781:
            return "cloud.fog"
        case 800:
            return "sun.max"
        case 800...804:
            return "cloud.bolt"
        default:
            return "cloud"
        }
    }
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



### Loop

일련의 작업을 순서대로 수행한다.

```swift
let fruitBasket = ["Apple", "Orange", "Pear"]
let fruitBasket2: Set = ["Apple", "Orange", "Pear"]
let contacts = ["Adam": 12345678, "James": 9876512]
let titleText = "Flash"
let closeRange = 1...5

// 배열, 문자열 각 구성 요소 순서대로 순회
for latter in titleText {
}

// 효율적인 방식으로 순회(순서 보장 X)
for fruit in fruitBasket2 {
}

// 
for person in contacts {
	print(person.key)
	print(person.value)
}

// use range operator
for number in 1...5 {
}

// 5번 순회
for _ in closeRange {
}

// isTrue가 false가 될때까지 무한 반복
// 사용시 주의가 필요하고 종료할 수 있는 원포인트를 꼭 지정해야한다.
// 얼마나 걸릴지 모르는 작업을 처리할 때 사용한다.
while isTrue {
}
```



### Set

컬렉션 타입중 하나로 배열과 다르게 순서를 보장하지 않는다.



### Extensions

기존 메인 코드를 수정하지 않고 추가적인 기능 넣어 확장할 수 있는 기능. structure, class 그리고 protocol에 사용할 수 있다. 애플의 UI 클래스는 오픈소스가 아니라 코드를 수정하는 것이 불가능하지만 이 extension 기능을 사용하면 필요한 기능을 덮어 사용할 수 있다.

```swift
// 자리수에 맞는 소수점까지 표현하는 메서드 추가
extension Double {
	func round(to places: Int) -> Double {
		let precisionNumber = pow(10, Double(places)	
		var n = self
		n = n * preciesionNumber
		n.round()
		n = n / preciesionNumber
		return n
	}
}

// 버튼을 원형으로 만드는 메서드 추가
extension UIButton {
	func makeCircular() {
		self.clipsToBounds = true
		self.layer.cornerRadius = self.frame.size.width / 2
	}
}

// 프로토콜의 메서드의 디폴트 구현
// 프로토콜을 호출한 구조체 또는 클래스에서 메서드를 정의할 필요가 없다.
extension CanFly {
	func fly() {
			print("I believe I can fly")
	}
}
```



### MARK

파일안에 작성된 코드들을 섹션별로 나눌 수 있다. 또한 커스텀 코드 스니펫을 만들어 활용하기도 한다.

```swift
// Devide section 
//MARK: - UITextFeildDelegate

// create code snnipet
1. //MARK: - 
2. 오른쪽 클릭
3. create code snnipet
```



### Static

기존에 구조체안에서 프로퍼티를 만들면 인스턴스를 생성한 후에 사용할 수 있게 된다. 하지만, static 키워드를 사용하게 되면 인스턴스를 생성하지 않고 구조체 고유의 특성, 즉 타입 프로퍼티에 바로 접근할 수 있게 된다.

```swift
struct Mystructure {
	let instanceProperty = "ABC"
	static let typeProperty = "123"

	func instanceMethod() {}
	static func typeMethod() {}
}

// need instance
let myStructure = MyStructure()
print(myStructure.instanceProperty)
print(myStructure.instanceMethod)

// no need that
print(myStructure.typeProperty)
print(myStructure.typeMethod)
```



