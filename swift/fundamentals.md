# Fundamentals

### var, let

값과 이름을 연결하는 키워드로 _`let`_(상)은 값이 할당되면 변경할 수 없지만 _`var`_(변수)를 사용하면 변경 할 수 있다.&#x20;

```swift
// 쉼표를 구분하여 한 줄에 여러 상수 또는 변수 선언 가능
var a = 0, b = 1, c= 2

// Type Annotations
var name: String = "Jake"

// Type Inference으로 타입 생략
// 스위프트 컴파일러가 알아서 타입을 추론
var name = "Jake"

// 변수 상수 이름 유니코드로 모든 문자를 사용
var 🐶 = "dog"

// 변수 및 상수 인쇄
// print(_:separator:terminator:)
// separator, terminator는 디폴트값이 있어 생략
print(🐶)
```



### Immutability

_`let`_과 같은 키워드를 사용하면 값의 수정이 불가능한데 이를 _immutable하다고 표현한다_. 하나의 예를 들면 구조체를 구성하는 프로퍼티 변수를 수정하는 일이 있을 수 있다. 실제 인스턴스에서 이 변수를 수정하는 일이 발생하면 메서드를 사용해야하는데 일반적으로 이 과정에서는 메서드 안에 _`self`_ 키워드로 구조체 변수에 접근하는 로직이 작성된다. **주의할 점은 구조체의 **_**`self`**_**는 인스턴스 생성시 **_**`let`**_**으로 생성되기 때문에 변수를 수정하는 것이 불가능하다.**&#x20;

물론 구조체에 한해서 변경 가능한 방법이 없지는 않다. 이때 구조체에서 _`var`_로 선언된 변수를 수정하기 위해서는 _`mutating`_이라는 키워드를 앞에 붙 메서드를 선언해야한다. 이때는 _`self`_ 키워드를 사용하지 않아도 변수에 접근할 수 있게 된다. 핵심은 상수 선언 키워드 _`let`_을 사용시 해당 메모리 저장된 데이터는 수정이 불가능하다는 것을 기억하자.&#x20;



### **Operators**

대괄호, 제곱, 곱셈 or 나눗셈, 플러스 or 마이너스 우선순로 계산한다. 주의할점은 컴퓨터가 같은 우선순위를 계산할 경우 왼쪽에서 부터 차례대로 연산하게 된다. C 및 Objective-C의 산술 연산자와 달리 Swift 산술 연산자는 기본적으로 값이 오버플로되는 것을 허용하지않는다. 필요에 따라 ampersand(&)로 시작하는 연산 사용해야한다.(&+)

* assignment operator (=)
* equal to operator (==)
* Arithmetic operators (+, -, \*, /, %)
* range operators(…, ..<)

```swift
// string 연결 가능
"hello, " + "world"

// Ternary Conditional Operator
n == 0 ? "none" : "something"

// One-Sided Ranges
// index 2이하 전부
for name in names[...2] {
    print(name)
}

// 1~5까지 랜덤 숫
Int.random(in:1...5)
```



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
var pets = [String]()

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



### switch vs if

범위가 클수록 패턴 매칭이 if구문보다 효율적이고 읽기 쉬운 코드가 된다. swich를 사용할 때, 꼭 범위 외의 사항에 대한 처리가 필요하며 이는 default에서 처리한다. 또한 각각의 범위는 … / ..< 와 같은 범위 연산 키워드를 사용하여 설정할 수 있다.

```swift
 // if로 이렇게 선언하면 따귀 맞는다.
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
```



### Function

Input과 output이 없을 경우, () {}

Input만 있을 경우 (parameter: DataType)

Output만 있을 경우 () returnArrow DataType { return Keyword value } 로 정의할 수 있다.



### Error Handling

프로그램 실행 중에 발생할 수 있는 오류 조건을 함수 내에 작성하면 함수를 호출한 곳에서 정확하게 오류를 응답할 수 있.

```swift
// 오류가능성이 있는 함수는 throws 키워드를 입력
func canThrowAnError() throws {
}

// 에러 가능성이 있는 함수 호출할 경우, do, try, catch 구문 사
do {
    try canThrowAnError()
} catch {
    print(error)
}
```



### Debugging

print는 단지 값을 인쇄하는 역할이지만 assertion을 사용하면 프로그램을 종료시킬 수 있어 디버깅에 적합한 명령어다. 런타임에 발생하는 검사로 필수 조건을 충족하였는지 확인할 때 사용할 수 있.

```swift
// 성공 조건, 실패 문구를 기입
// age < 0 종료
assert(age >= 0, "A person's age can't be less than zero.")

// 이미 실패 조건일 경우, 강제 종료 가능
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```



### Structure

커스텀 데이터 타입을 만들어 사용할 수 있다. 기존 데이터 타입들은 이 구조를 활용되어 만들어졌고 이미 Prebuilt 되어 있어 사용할 수 있는 것이다. 내가 필요한 타입들을 모아 스트럭쳐를 구성할 수 있고 초기화하여 사용할 수 있다. 객체를 생성하는 블루프린트로 불리기도 한다. 이 구성은 프로퍼티 혹은 메서드로 구성 될 수 있다.

structure에 사용할 데이터를 모두 담아둘 수도 있지만, initialize를 통해 생성과 동시에 데이터를 담아 둘 수 있다는 장점이 있다. 하지만 굳이 생성자가 필요없는 경우는 생략하는 것이 정석이다. 블루프린트라는 의미는 프로퍼티, 메서드를 통해 그 형태를 만들어 놓는다는 것이고 생성자를 통해 고유한 특징을 입힘으로서 특정 객체를 나타낼 수 있는 것이다. 예를 들어 다양한 자동차, 국가라는 형태를 잡고 색, 성향, 리소스 즉 데이터를 추가함으로서 고유한 객체를 생성할 수 있게 된다.



### Self keword

자바스크립트의 this와 같다. 즉 실제 생성될 객체를 가르킨다. 블루프린트를 통해 생성된 객체는 각기 다른 특성을 가지고 있다. self를 통해 각각 생성된 객체의 프로퍼티 또는 메서드에 접근할 수 있게 된다. 클래스 내에서 self를 생략해도 스위프트가 알아서 찾아 낼 수 있지만 클로저를 사용할 경우, self를 생각해서는 안된다.



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



### Class

구조체와 유사하지만 클래스의 경우 슈퍼클래스로부터 상속이 가능하다는 점이 다르다. 상속이란 부모가 가진 특징을 그대로 물려받아 사용할 수 있을 뿐만 아니라 추가적인 능력을 추가할 수 있는 것을 의미한다. 미리 작성된 코드를 사용하게 되어 코드를 생성, 반복하는 작업을 줄일 수 있다. 개인적으로 클래스를 한단어로 표현한다면 **파생**이라 말할 수 잇을 것 같다. 물려받은 능력을 그대로 사용하거나 변형되거나 마치 진화하는 모습처럼. 서브클래스로 만든 인스턴스로 부모로 부터 물려받은 변수를 변경하거나 메서드를 호출하는 것이 가능하다. 부모는 자식을 위해 모든 것을 해주는 모습처럼 여길 수 있을 것 같다. 서브 클래스내에서의 메서드를 변경할때 override, super 키워드를 사용할 수 있다. 인스턴스 생성시 프로퍼티에 접근하기 위해 구조체의 경우 init을 선언할 필요업지만 클래스의 경우 init을 사용해야한다.

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



### Lazy

변수명과 함께 사용되는 키워드이다. 호출할 때, 동작하는 코드를 담고 있다. 처음부터 코드를 셋업할 필요가 없다는 의미로 비록 늦게 실행될 수 있지만 실행과 동시에 메모리에 할당되어 이점을 가질 수 있다.

```swift
lazy var persistentContainer: NSPersistentContainer = {    
    let container = NSPersistentContainer(name: "DataModel")
    container.loadPersistentStores(completionHandler: { (storeDescription, error) in
        if let error = error as NSError? {
            fatalError("Unresolved error \\(error), \\(error.userInfo)")
        }
    })
    return container
}()
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



### ViewController life cycle

super 필수적으로 입력한다. 운영체제가 순서대로 호출하는 메서드 모음

* 화면이 사용자에게 보이는 시점 1, 2, 3
* 화면이 사라질려고 할 때 4
* 화면이 완전히 사라지면 5, 조금이라도 ViewController에 일부분이 보이면 동작하지 않는다.

1.  viewDidLoad()

    화면이 생성되었을 때 오직 한번 호출한다. 모든 UI 컴포넌트, 뷰와 관련된 오브젝트를 연동하고 접근할 수 있는 메서드 영역이다. 즉 이 영역에서 모든 UI과 관련된 태그 셋팅을 해야 이후의 라이프 사이클에서 사용할 수 있다.
2.  viewWillApear()

    화면이 사용자에게 보이기 직전에 호출, 즉 스크린에 아무것도 보이지 않는 시간대에 호출, 화면이 구성하고 있는 요소들 중에 특정 부분을 보여 줄지 말지에 대한 결정을 내릴 때
3.  viewDidApear()

    스크린에 View가 보이는 시간 영역으로 타이머를 실행한다던지 사용자가 보는 즉시 해야할 일들을 구현할 수 있다.
4.  viewWillDisapear()

    화면에서 사라지기 직전에 호출
5.  viewDidDisapear()

    화면이 사라지고 난 후 호출, user Can’t see! 화면서에 사라진다는 의미가 삭제, 메모리 할당해제를 의미하는 것이 아니다.



### Application Lifecycle

운영체제는 CPU time, Memory와 같은 한정된 리소스를 할당할지 결정한다. 그렇다면 과연 이에 대한 우선순위는 어떨까? 여러앱을 교차적으로 사용할 때, 내가 입력하고 있는 데이터가 저장되고 있어야한다면 앱이 백그라운드로 들어가는 시점의 라이프사이클에 저장 작업이 수행 될 것이다.

프로젝트를 생성할 때, AppDelegate와 SceneDelegate 함수를 보았을 것이다. 앱 사이클 메서드가 위치하는 곳이 바로 이 파일들이다. 그렇다면 이 둘의 차이점은 뭘까? xcode 11전에는 AppDelegate 파일만 존재했었다. IOS13 이후 iPadOS와 같이 지금은 다양한 윈도우에서 여러 앱이 동작할 수 있게 되었는데, 각각의 윈도우 즉 Scene의 라이프사이클을 관리할 필요성이 생겼고 이를 위해 SceneDelegate가 생기게 되었다. 공통적인 이벤트는 AppDelegate에서 작동하고 윈도우를 위한 개별 콜백은 SceneDelegate에서 호출한다.

여러개의 ViewController는 하나의 Scene에 여러개의 Scene은 하나의 App에 있다. 이 모든 요소는 라이프사이클 메서드를 가지며 override해서 사용할 수 있게 된다.

```swift
// AppDelegate Life cycle methods
// 앱 실행하면 트리거되는 클래스, didFinishLaunchingWithOptions로 인해 런칭을 끝내면 웰컴 스크린을 볼 수 있다. 즉, func application에 포함된 함수가 정상적으로 실행되었다는 것을 의미합니다.
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
	        
	// 현재 함수명 출력, 언제???
	// 가장 먼저 호출,
	print(#function)

  return true
}

// SceneDelegate Life cycle methods
func sceneDidDisconnect(_ scene: UIScene) {
        // Called as the scene is being released by the system.
        // This occurs shortly after the scene enters the background, or when its session is discarded.
        // Release any resources associated with this scene that can be re-created the next time the scene connects.
        // The scene may re-connect later, as its session was not neccessarily discarded (see `application:didDiscardSceneSessions` instead).
    }

func sceneDidBecomeActive(_ scene: UIScene) {
    // Called when the scene has moved from an inactive state to an active state.
    // Use this method to restart any tasks that were paused (or not yet started) when the scene was inactive.
}

func sceneWillResignActive(_ scene: UIScene) {
    // Called when the scene will move from an active state to an inactive state.
    // This may occur due to temporary interruptions (ex. an incoming phone call).
}

func sceneWillEnterForeground(_ scene: UIScene) {
    // Called as the scene transitions from the background to the foreground.
    // Use this method to undo the changes made on entering the background.
}

func sceneDidEnterBackground(_ scene: UIScene) {
    // Called as the scene transitions from the foreground to the background.
    // Use this method to save data, release shared resources, and store enough scene-specific state information
    // to restore the scene back to its current state.
}
```

