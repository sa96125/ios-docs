# extensions

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

