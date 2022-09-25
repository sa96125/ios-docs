# var and let

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



### get, set, didSet, willSet

프로퍼티를 다채롭게 활용하는 방법이다.

```swift
// 입력된 값을 검증(validation)할 때 사용할 수 있다.
var myProperty: Int {
   get {
      return _myProperty
   }
   set(newVal) {
      _myProperty = newVal
   }
}

// 값이 입력된 직전/후에 수행할 로직
var myProperty: Int {
   willSet {
      loadItems()
   }
   didSet {
      loadItems()
   }
}
```

