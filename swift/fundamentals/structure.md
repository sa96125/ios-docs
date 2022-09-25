# structure

### Structure

커스텀 데이터 타입을 만들어 사용할 수 있다. Swift Primary Data Type들은 이 구조를 활용되어 만들어졌고 이미 Prebuilt 되어 있어 사용할 수 있는 것이다. 내가 필요한 타입들을 모아 스트럭쳐를 구성할 수 있고 초기화하여 사용할 수 있다. 객체를 생성하는 블루프린트로 불리기도 한다. 이 구성은 프로퍼티 혹은 메서드로 구성 될 수 있다.

structure에 사용할 데이터를 모두 담아둘 수도 있지만, initialize를 통해 생성과 동시에 데이터를 담아 둘 수 있다는 장점이 있다. 하지만 굳이 생성자가 필요없는 경우는 생략하는 것이 정석이다. 블루프린트라는 의미는 프로퍼티, 메서드를 통해 그 형태를 만들어 놓는다는 것이고 생성자를 통해 고유한 특징을 입힘으로서 특정 객체를 나타낼 수 있는 것이다. 예를 들어 다양한 자동차, 국가라는 형태를 잡고 색, 성향, 리소스 즉 데이터를 추가함으로서 페라리, 대한민국 처럼 고유한 객체를 생성할 수 있게 된다.



### Self keword

자바스크립트의 this와 같다. 즉 실제 생성될 객체를 가르킨다. 블루프린트를 통해 생성된 객체는 각기 다른 특성을 가지고 있다. self를 통해 각각 생성된 객체의 프로퍼티 또는 메서드에 접근할 수 있게 된다. 클래스 내에서 self를 생략해도 스위프트가 알아서 찾아 낼 수 있지만 클로저를 사용할 경우, self를 생각해서는 안된다.



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

