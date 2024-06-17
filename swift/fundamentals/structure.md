---
description: less memory leaks and thread safety
---

# structure

객체를 생성하는 설계도(블루프린트) 입니다. 프로퍼티, 메서드로 구성되어 커스텀 데이터 타입을 만드는 방법입니다. Swift의 기본타입은 구조체로 pre-built 되어져 있습니다.



Swift의 구조체는 다른 프로그래밍 언어(c, Objective-c)와 다른 특징을 가집니다.

1. **Immutability, self는 let으로 선언되어 상태 변경할 수 없습니다.**
2. **상속을 포함하지 않아 가볍고 심플합니다.**
3. **데이터를 스택에 저장하여 빠릅니다.**
4. **value type으로 깊은 복사를 하기 때문에 원본에 영향을 미치지 않아 안전합니다.**



복잡한 데이터를 구성하는데 사용되며 클래스와 다르게 초기값을 할당하기 위해 생성자를 생성할 필요가 없습니다. 공식문서에서는 객체를 만들 필요성이 있을 때, 먼저 구조체 형식으로 만드는 것을 권장하고 있습니다. 상태를 변경하기 위해 mutating 키워드를 사용할 수 있습니다. 내부에 수정이 발생되면 새로운 인스턴스를 생성합니다. 불변성의 특징 답게 let으로 인스턴스 생성시 어떠한 변경도 허용되지 않습니다.





### Static

구조체의 프로퍼티 또는 메서드에 접근하려 인스턴스를 생성한 후에 사용할 수 있었습니다. 하지만, static 키워드와 함께 프로퍼티를 선언한다면 인스턴스의 생성 없이 바로 접근할 수 있습니다.



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

