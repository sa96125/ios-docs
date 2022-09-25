# Delegate

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
