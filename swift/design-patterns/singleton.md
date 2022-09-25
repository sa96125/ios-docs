# Singleton

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
