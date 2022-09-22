---
description: >-
  Complexity를 관리하는 방법. 정말 많은 패턴(아키텍쳐 블루프린트)가 존재한다. 이중에는 요구사항을 기반으로하는 패턴과 스타일을
  중점으로 하는 패턴으로 나뉜다. 공통된 문제에 대한 검증된 솔루션을 의미한다.
---

# Design Patterns

### MVC

model-view-controller 디자인 패턴은 쉽게 말해 데이터와 이를 처리하는 로직을 담는 영역, 인터랙션을 담당하는 유저 인터페이스 영역 그리고 이를 중재하는 영역으로 나눈 것을 말한다. 모델과 뷰는 직접 관여하지 않고 컨트롤러에 의해서 상호작용을 할 수 있게 된다. 만약 화면 속에서 다양한 내용을 표현하고 싶을 때, 모델 부분만 다르게 처리하여 코드를 재사용할 수 있는 이점이 생긴다. 뿐만아니라 분리하여 컴포넌트를 관리가능하니까 나뿐만 아니라 다른사람들이 보기에도 프로그램이 훨씬 읽고 이해하기 쉬워진다.

1. send event
2. makes request
3. send back data
4. modifies UI

실제 코드를 작성한 뒤 MVC패턴으로 코드를 리팩토링할 수 있어야한다. 먼저 Model을 구조체로 생성한 후, 기존 코드 로직을 객체의 메서드로 호출한다. 여기서 고려해야할 사항은 구조체 내에서 사용하는 변수를 굳이 생성자로 값을 받아 할당할 필요성이 있는가 하는 것, 또 초기화값이 굳이 할당되어야하는 것일까? 초기화 값이 필요 없다면 nil이 포함되는데, 옵셔널 변수는 값이 할당되지 않은채 값이 호출 될 수 있다. 즉 런타임 에러를 초래하지 않도록 고려되어야 한다.



### Delegate

대신 처리하는 패턴으로 프로토콜과 함께 사용되는 패턴이다. 이는 스위프트에서 많이 활용하는 방식으로 POP(protocal oriented programming)패러다임 언어로 불리는 이유이기도 하다.

```swift
protocol AdvancedLifeSupport {
	func performCPR()
}

class EmergencyCallHandler {
	var delegate: AdvancedLifeSupport
	
	func assessSituation() {
		print("can you tell me what happend?")
	}

	func medicalEmergency() {
		delegate?.performCRP()
	}
}

struct Paramedic: AdvancedLifeSupport {
	init(handler: EmergencyCallHandler) {
		handler.delegate = self
	}

	func perfomrCPR() {
		print("The paramedic does chest compressions, 30 per second")
	}
}

class Doctor: AdvancedLifeSupport {
	init(handler: EmergencyCallHandler) {
		handler.delegate = self
	}

	func performCPR() {
		print("The doctor does chest compressions, 30 per second")	
	}

	func useStethescope() {
		print("Listening for heart sounds")	
	}
}

class Surgeon: Doctor {
	override func performCPR() {
		super.performCPR()
		print("Sings staying alive by the BeeGees")
	}

	func useElectricDrill() {
		print("Whirr...")
	}
}

let emilio = EmergencyCallHandler()
let pete = Paramedic(handler: emilio)

emilio.assessSituation()
emilio.medicalEmergency()
```



### Observer

*   ObservableObject Protocal

    이 프로토콜을 가지면 자신의 프로퍼티 혹은 메서드를 다른 곳에서 사용이 가능하다.
*   @Published

    이 property wrapper을 가진 변수는 다른 곳에서 구독할 수 있다는 것을 의미한다.
*   @ObservedObject

    ObservableObject 인스턴스를 생성하여 사용할 수 있다.



### Singleton

모든 곳에서 사용하는 단 하나의 오브젝를 생성하는 클래스

```swift
class Car {
	var colour = "Red"

	// 계속 똑같은 객체를 카피.
	static let singletonCar = Car()
}

let myCar = Car.singletonCar
myCar.colour = "Blue"

let yourCar = Car.singletonCar
print(yourCar.color) // "Blue"
```

